# Networking Lab

## Week 8: Linux Networking Essentials

### Day 1: Network Basics

**Objectives:**
- Understand network interfaces
- Configure network settings
- Test connectivity

**Commands:**
```bash
# Network information
ip addr show                 # Show IP addresses
ip link show                 # Show interfaces
ifconfig                     # Legacy interface info
hostname                     # Show hostname
hostname -I                  # Show IP addresses

# Routing
ip route show                # Show routing table
route -n                     # Legacy routing table
traceroute host              # Trace route to host
tracepath host               # Alternative trace

# DNS
nslookup domain              # DNS lookup
dig domain                   # Detailed DNS info
host domain                  # Simple DNS lookup
cat /etc/resolv.conf         # DNS servers
```

**Exercises:**

1. **Network Discovery**
   ```bash
   # Check your IP
   ip addr show
   
   # Find default gateway
   ip route show | grep default
   
   # Check DNS servers
   cat /etc/resolv.conf
   
   # Hostname info
   hostname
   hostname -f
   ```

2. **Connectivity Tests**
   ```bash
   # Ping test
   ping -c 4 google.com
   
   # Trace route
   traceroute google.com
   
   # DNS lookup
   nslookup google.com
   dig google.com
   ```

3. **Network Troubleshooting**
   - Test local connectivity
   - Test gateway connectivity
   - Test external connectivity
   - Verify DNS resolution

### Day 2: Network Tools

**Commands:**
```bash
# Port scanning
netstat -tuln                # Listening ports
ss -tuln                     # Socket statistics
lsof -i                      # Open network files
nmap localhost               # Port scan (if installed)

# Network statistics
netstat -s                   # Network statistics
ss -s                        # Socket summary
iftop                        # Bandwidth monitor
nethogs                      # Per-process bandwidth

# Download/Upload
wget url                     # Download file
curl url                     # Transfer data
curl -I url                  # Get headers
scp file user@host:path      # Secure copy
```

**Exercises:**

1. **Port Monitoring**
   ```bash
   # List listening ports
   sudo ss -tuln
   
   # Find process using port
   sudo lsof -i :80
   sudo lsof -i :22
   
   # Check established connections
   ss -t state established
   ```

2. **File Transfer**
   ```bash
   # Download with wget
   wget https://example.com/file.txt
   
   # Download with curl
   curl -O https://example.com/file.txt
   
   # Test API endpoint
   curl -X GET https://api.github.com
   ```

3. **Network Analysis**
   - Identify active connections
   - Monitor bandwidth usage
   - Check for unusual traffic
   - List services and ports

### Day 3: SSH and Remote Access

**Commands:**
```bash
# SSH basics
ssh user@host                        # Connect to host
ssh -p port user@host                # Custom port
ssh-keygen                           # Generate key pair
ssh-copy-id user@host                # Copy public key

# SSH file transfer
scp file user@host:/path             # Copy to remote
scp user@host:/path/file .           # Copy from remote
scp -r directory user@host:/path     # Copy directory

# SFTP
sftp user@host                       # Interactive SFTP
```

**Exercises:**

1. **SSH Key Setup**
   ```bash
   # Generate SSH key
   ssh-keygen -t rsa -b 4096 -C "your@email.com"
   
   # View public key
   cat ~/.ssh/id_rsa.pub
   
   # Copy to remote (if you have remote host)
   # ssh-copy-id user@remotehost
   ```

2. **SSH Configuration**
   ```bash
   # Create SSH config
   cat > ~/.ssh/config << 'EOF'
   Host myserver
       HostName server.example.com
       User myuser
       Port 22
       IdentityFile ~/.ssh/id_rsa
   EOF
   
   # Set permissions
   chmod 600 ~/.ssh/config
   ```

3. **Remote Commands**
   ```bash
   # Execute remote command
   ssh user@host 'ls -la'
   
   # Run script remotely
   ssh user@host 'bash -s' < local_script.sh
   
   # Tunnel creation
   ssh -L 8080:localhost:80 user@host
   ```

### Day 4: Firewall Basics

**Commands (UFW - Ubuntu):**
```bash
# UFW basics
sudo ufw status                  # Check status
sudo ufw enable                  # Enable firewall
sudo ufw disable                 # Disable firewall

# Rules
sudo ufw allow 22                # Allow SSH
sudo ufw allow 80/tcp            # Allow HTTP
sudo ufw deny 23                 # Deny Telnet
sudo ufw delete allow 80         # Delete rule

# Advanced
sudo ufw allow from 192.168.1.0/24   # Allow subnet
sudo ufw limit ssh                    # Rate limit
```

**Commands (firewalld - CentOS/RHEL):**
```bash
# Firewalld basics
sudo firewall-cmd --state
sudo firewall-cmd --list-all
sudo firewall-cmd --get-active-zones

# Rules
sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --add-port=8080/tcp --permanent
sudo firewall-cmd --reload
```

**Exercises:**

1. **Basic Firewall Setup**
   ```bash
   # Enable firewall
   sudo ufw enable
   
   # Allow essential services
   sudo ufw allow ssh
   sudo ufw allow http
   sudo ufw allow https
   
   # Check status
   sudo ufw status verbose
   ```

2. **Port Management**
   - Open required ports
   - Block unnecessary ports
   - Test firewall rules
   - Document configuration

### Day 5: Network Troubleshooting

**Common Issues and Solutions:**

1. **No Internet Connection**
   ```bash
   # Check interface
   ip link show
   
   # Check IP address
   ip addr show
   
   # Check gateway
   ip route show
   
   # Test connectivity
   ping -c 4 8.8.8.8
   ```

2. **DNS Issues**
   ```bash
   # Check DNS servers
   cat /etc/resolv.conf
   
   # Test DNS
   nslookup google.com
   dig google.com
   
   # Use alternative DNS
   nslookup google.com 8.8.8.8
   ```

3. **Slow Connection**
   ```bash
   # Check bandwidth
   sudo iftop
   
   # Check connections
   ss -s
   
   # Monitor packets
   sudo tcpdump -i eth0 -n
   ```

### Challenge Labs

**Challenge 1: Network Diagnostic Tool**
Create a script that:
- Tests connectivity to multiple hosts
- Checks DNS resolution
- Verifies open ports
- Generates connectivity report
- Suggests fixes for common issues

**Challenge 2: SSH Management**
Create a tool to:
- Manage multiple SSH connections
- Store connection profiles
- Quick connect to saved hosts
- Log connection history

**Challenge 3: Network Monitor**
Create a monitoring system:
- Track bandwidth usage
- Monitor active connections
- Alert on unusual activity
- Generate hourly reports
- Log all network events

## Network Security Tips

1. **Use SSH Keys**: Disable password authentication
2. **Keep Firewall Active**: Only open necessary ports
3. **Regular Updates**: Update network tools
4. **Monitor Logs**: Check for suspicious activity
5. **Strong Passwords**: For all network services
6. **Disable Unused Services**: Reduce attack surface
7. **Use VPN**: For remote access
8. **Encrypt Traffic**: Use HTTPS, SFTP, etc.

## Useful Network Commands Summary

```bash
# Quick reference
ip addr                     # IP addresses
ip route                    # Routing table
ss -tuln                    # Listening ports
ping host                   # Test connectivity
traceroute host             # Trace route
nslookup domain             # DNS lookup
netstat -i                  # Interface statistics
tcpdump                     # Packet capture
iptables -L                 # Firewall rules
```

## Next Steps

Advanced topics:
- Network packet analysis (Wireshark, tcpdump)
- VPN configuration
- Network automation
- Load balancing
- Container networking
- Advanced security and hardening
