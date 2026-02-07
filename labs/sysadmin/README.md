# System Administration Lab

## Week 7: System Administration Essentials

### Day 1: User and Group Management

**Objectives:**
- Manage users and groups
- Understand permissions
- Configure user access

**Commands:**
```bash
# User management
useradd username              # Create user
userdel username              # Delete user
usermod -aG group user        # Add user to group
passwd username               # Set password
id username                   # Show user info

# Group management
groupadd groupname            # Create group
groupdel groupname            # Delete group
groups username               # Show user groups

# Information
whoami                        # Current user
who                          # Logged in users
w                            # Detailed user info
last                         # Login history
```

**Exercises:**

1. **Create Test Users**
   ```bash
   # Create user
   sudo useradd -m -s /bin/bash testuser
   sudo passwd testuser
   
   # View user info
   id testuser
   cat /etc/passwd | grep testuser
   
   # Create group
   sudo groupadd developers
   sudo usermod -aG developers testuser
   ```

2. **Permission Management**
   ```bash
   # Create test directory
   mkdir ~/shared
   
   # Change ownership
   sudo chown testuser:developers ~/shared
   
   # Set permissions
   chmod 775 ~/shared
   
   # Verify
   ls -ld ~/shared
   ```

3. **Sudo Configuration**
   - Add user to sudo group
   - Configure sudoers file
   - Test sudo access

### Day 2: Process Management

**Commands:**
```bash
# Process viewing
ps aux                    # All processes
ps -ef                    # Full format
top                       # Interactive view
htop                      # Better top (if installed)
pgrep name               # Find process by name
pidof program            # Get PID of program

# Process control
kill PID                 # Terminate process
kill -9 PID              # Force kill
killall name             # Kill by name
pkill pattern            # Kill by pattern

# Background jobs
command &                # Run in background
jobs                     # List jobs
fg %1                    # Bring to foreground
bg %1                    # Resume in background
nohup command &          # Run immune to hangup
```

**Exercises:**

1. **Process Monitoring**
   ```bash
   # Find processes
   ps aux | grep bash
   
   # Monitor resources
   top -b -n 1 | head -20
   
   # Check specific process
   ps -p $$ -o pid,comm,%cpu,%mem
   ```

2. **Process Control**
   ```bash
   # Start background job
   sleep 100 &
   
   # List jobs
   jobs
   
   # Kill job
   kill %1
   ```

3. **Resource Usage**
   - Find top CPU consuming processes
   - Find memory hogs
   - Monitor specific application

### Day 3: Service Management (systemd)

**Commands:**
```bash
# Service control
systemctl start service      # Start service
systemctl stop service       # Stop service
systemctl restart service    # Restart service
systemctl reload service     # Reload config
systemctl enable service     # Enable at boot
systemctl disable service    # Disable at boot

# Service status
systemctl status service     # Service status
systemctl is-active service  # Check if active
systemctl is-enabled service # Check if enabled

# System state
systemctl list-units         # List all units
systemctl list-unit-files    # List unit files
systemctl daemon-reload      # Reload systemd
```

**Exercises:**

1. **Service Management**
   ```bash
   # Check SSH status
   systemctl status ssh
   
   # List all services
   systemctl list-units --type=service
   
   # Check failed services
   systemctl --failed
   ```

2. **Create Simple Service**
   ```bash
   # Create service file
   sudo cat > /etc/systemd/system/myapp.service << 'EOF'
   [Unit]
   Description=My Application
   After=network.target
   
   [Service]
   Type=simple
   User=myuser
   ExecStart=/path/to/script.sh
   Restart=on-failure
   
   [Install]
   WantedBy=multi-user.target
   EOF
   
   # Reload and start
   sudo systemctl daemon-reload
   sudo systemctl start myapp
   sudo systemctl enable myapp
   ```

### Day 4: Disk and File System Management

**Commands:**
```bash
# Disk usage
df -h                    # Disk space
du -sh directory         # Directory size
du -h --max-depth=1      # Size of subdirectories

# Disk operations
fdisk -l                 # List disks
lsblk                    # Block devices
mount                    # Show mounted filesystems
mount /dev/sda1 /mnt     # Mount partition
umount /mnt              # Unmount

# Find large files
find / -type f -size +100M -exec ls -lh {} \; 2>/dev/null
```

**Exercises:**

1. **Disk Analysis**
   ```bash
   # Check disk usage
   df -h
   
   # Find large directories
   du -h /var | sort -rh | head -10
   
   # Find large files
   find /home -type f -size +50M -ls 2>/dev/null
   ```

2. **Cleanup Tasks**
   - Remove old log files
   - Clean package caches
   - Remove temporary files
   - Empty trash

### Day 5: Log Management

**Commands:**
```bash
# View logs
journalctl                     # All logs
journalctl -u service          # Service logs
journalctl -f                  # Follow logs
journalctl --since today       # Today's logs
journalctl -p err              # Error level
tail -f /var/log/syslog        # Follow syslog

# Log rotation
logrotate -f /etc/logrotate.conf
```

**Exercises:**

1. **Log Analysis**
   ```bash
   # Check system logs
   sudo journalctl -p err --since today
   
   # Service logs
   sudo journalctl -u ssh -n 50
   
   # Boot logs
   sudo journalctl -b
   ```

2. **Log Parsing**
   - Extract error messages
   - Count different log levels
   - Find authentication failures
   - Generate log report

### Challenge Labs

**Challenge 1: System Monitor Script**
Create a monitoring script that:
- Checks CPU usage
- Monitors memory
- Checks disk space
- Reports service status
- Sends alerts if thresholds exceeded

**Challenge 2: User Management System**
Create a script to:
- Add multiple users from file
- Set up home directories
- Configure groups
- Set default permissions
- Generate report

**Challenge 3: Backup and Restore**
Create backup system:
- Backup important directories
- Compress and archive
- Manage retention policy
- Restore functionality
- Verification checks

## Security Best Practices

1. **Principle of Least Privilege**: Grant minimum necessary permissions
2. **Regular Updates**: Keep system updated
3. **Strong Passwords**: Enforce password policies
4. **Audit Logs**: Regularly review logs
5. **Disable Unused Services**: Reduce attack surface
6. **Firewall Configuration**: Control network access
7. **Backup Regularly**: Protect against data loss

## Next Steps

Move on to:
- Networking Lab
- Security and Hardening
- Automation and Orchestration
