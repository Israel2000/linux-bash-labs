# Linux Command Quick Reference

Essential commands for daily Linux practice and operations.

## Navigation & File System

### Directory Navigation
```bash
pwd                    # Print working directory
ls                     # List files
ls -la                 # List all with details
cd /path               # Change directory
cd ~                   # Go to home
cd ..                  # Go up one level
cd -                   # Go to previous directory
tree                   # Show directory tree
```

### File Operations
```bash
touch file             # Create empty file
cat file               # Display file
less file              # View file (paginated)
head -n 10 file        # First 10 lines
tail -n 10 file        # Last 10 lines
tail -f file           # Follow file updates
cp src dest            # Copy file
mv src dest            # Move/rename file
rm file                # Remove file
mkdir dir              # Create directory
rm -rf dir             # Remove directory
```

### File Searching
```bash
find /path -name "*.txt"        # Find by name
find /path -type f -size +1M    # Find large files
find /path -mtime -7            # Modified in last 7 days
locate filename                 # Quick find
which command                   # Find command location
whereis command                 # Locate binary/source/man
```

## Text Processing

### Grep - Search Text
```bash
grep "pattern" file              # Basic search
grep -i "pattern" file           # Case insensitive
grep -v "pattern" file           # Invert match
grep -r "pattern" dir/           # Recursive search
grep -n "pattern" file           # Show line numbers
grep -c "pattern" file           # Count matches
grep -l "pattern" *.txt          # Files with matches
grep -E "regex" file             # Extended regex
```

### Sed - Stream Editor
```bash
sed 's/old/new/' file            # Replace first occurrence
sed 's/old/new/g' file           # Replace all
sed -i 's/old/new/g' file        # In-place edit
sed -n '1,10p' file              # Print lines 1-10
sed '5d' file                    # Delete line 5
sed '/pattern/d' file            # Delete matching lines
```

### Awk - Text Processing
```bash
awk '{print $1}' file            # Print first column
awk '{print $NF}' file           # Print last column
awk '/pattern/' file             # Print matching lines
awk '{sum+=$1} END {print sum}'  # Sum column
awk -F: '{print $1}' file        # Custom delimiter
awk 'NR==10' file                # Print line 10
awk 'length>80' file             # Lines > 80 chars
```

### Other Text Tools
```bash
cut -d: -f1 file         # Cut by delimiter
sort file                # Sort lines
sort -r file             # Reverse sort
sort -n file             # Numeric sort
uniq file                # Remove duplicates
uniq -c file             # Count occurrences
wc -l file               # Count lines
wc -w file               # Count words
tr 'a-z' 'A-Z'           # Translate characters
```

## Permissions & Ownership

### File Permissions
```bash
chmod 755 file           # rwxr-xr-x
chmod u+x file           # Add execute for user
chmod g-w file           # Remove write for group
chmod o+r file           # Add read for others
chmod -R 644 dir/        # Recursive permission
```

### Ownership
```bash
chown user file          # Change owner
chown user:group file    # Change owner and group
chgrp group file         # Change group
chown -R user:group dir/ # Recursive ownership
```

### Permission Values
```
r = 4 (read)
w = 2 (write)
x = 1 (execute)

755 = rwxr-xr-x (owner: rwx, group: r-x, others: r-x)
644 = rw-r--r-- (owner: rw-, group: r--, others: r--)
600 = rw------- (owner: rw-, group: ---, others: ---)
```

## Process Management

### Viewing Processes
```bash
ps                       # Current shell processes
ps aux                   # All processes
ps -ef                   # Full format
ps -u username           # User processes
top                      # Interactive process viewer
htop                     # Better top (if installed)
pgrep name               # Find process by name
pidof program            # Get PID
```

### Process Control
```bash
command &                # Run in background
jobs                     # List background jobs
fg %1                    # Bring job 1 to foreground
bg %1                    # Resume job 1 in background
kill PID                 # Terminate process
kill -9 PID              # Force kill
killall name             # Kill by name
pkill pattern            # Kill by pattern
nohup command &          # Run immune to hangup
```

## User Management

### User Operations
```bash
whoami                   # Current user
who                      # Logged in users
w                        # Detailed user info
id username              # User ID info
last                     # Login history
useradd username         # Create user
userdel username         # Delete user
usermod -aG group user   # Add to group
passwd username          # Change password
```

### Group Operations
```bash
groups username          # Show user groups
groupadd groupname       # Create group
groupdel groupname       # Delete group
```

## System Information

### System Details
```bash
uname -a                 # System information
hostname                 # System hostname
uptime                   # System uptime
date                     # Current date/time
cal                      # Calendar
df -h                    # Disk space
du -sh dir/              # Directory size
free -h                  # Memory usage
lsblk                    # Block devices
```

### System Monitoring
```bash
top                      # Process monitor
htop                     # Better process monitor
vmstat                   # Virtual memory stats
iostat                   # I/O statistics
dmesg                    # Kernel messages
journalctl               # System logs
```

## Networking

### Network Info
```bash
ip addr show             # IP addresses
ip link show             # Network interfaces
ip route show            # Routing table
hostname -I              # IP addresses
```

### Connectivity
```bash
ping host                # Test connectivity
traceroute host          # Trace route
nslookup domain          # DNS lookup
dig domain               # Detailed DNS info
curl url                 # Transfer data
wget url                 # Download file
```

### Network Tools
```bash
netstat -tuln            # Listening ports
ss -tuln                 # Socket statistics
lsof -i                  # Open network files
netstat -i               # Interface statistics
```

### SSH
```bash
ssh user@host            # Connect via SSH
ssh-keygen               # Generate SSH keys
ssh-copy-id user@host    # Copy public key
scp file user@host:path  # Secure copy
```

## Package Management

### APT (Debian/Ubuntu)
```bash
apt update               # Update package list
apt upgrade              # Upgrade packages
apt install package      # Install package
apt remove package       # Remove package
apt search package       # Search packages
apt show package         # Show package info
```

### YUM/DNF (RHEL/CentOS)
```bash
yum update               # Update packages
yum install package      # Install package
yum remove package       # Remove package
yum search package       # Search packages
```

## Archive & Compression

### Tar
```bash
tar -czf file.tar.gz dir/     # Create compressed archive
tar -xzf file.tar.gz          # Extract compressed archive
tar -tzf file.tar.gz          # List contents
tar -xzf file.tar.gz file     # Extract specific file
```

### Compression
```bash
gzip file                # Compress file
gunzip file.gz           # Decompress file
bzip2 file               # Better compression
bunzip2 file.bz2         # Decompress bzip2
zip -r file.zip dir/     # Create zip
unzip file.zip           # Extract zip
```

## Redirection & Pipes

### Redirection
```bash
command > file           # Redirect stdout (overwrite)
command >> file          # Redirect stdout (append)
command 2> file          # Redirect stderr
command &> file          # Redirect both stdout/stderr
command < file           # Read from file
```

### Pipes
```bash
cmd1 | cmd2              # Pipe output to input
cmd1 | tee file          # Save and display
cmd1 && cmd2             # Run cmd2 if cmd1 succeeds
cmd1 || cmd2             # Run cmd2 if cmd1 fails
cmd1 ; cmd2              # Run sequentially
```

## Shell Scripting

### Script Basics
```bash
#!/bin/bash              # Shebang line
# Comment              # Comments
variable="value"         # Variable assignment
$variable                # Variable usage
$(command)               # Command substitution
```

### Conditionals
```bash
if [ condition ]; then
    commands
fi

[ -f file ]              # File exists
[ -d dir ]               # Directory exists
[ "$a" = "$b" ]          # String equality
[ $a -eq $b ]            # Numeric equality
[ $a -lt $b ]            # Less than
[ $a -gt $b ]            # Greater than
```

### Loops
```bash
for i in {1..5}; do
    echo $i
done

while [ condition ]; do
    commands
done
```

## Keyboard Shortcuts

### Command Line
```bash
Ctrl+C                   # Kill current process
Ctrl+Z                   # Suspend current process
Ctrl+D                   # Exit shell / EOF
Ctrl+L                   # Clear screen
Ctrl+A                   # Move to line start
Ctrl+E                   # Move to line end
Ctrl+U                   # Delete line before cursor
Ctrl+K                   # Delete line after cursor
Ctrl+W                   # Delete word before cursor
Ctrl+R                   # Search command history
Tab                      # Auto-complete
!!                       # Repeat last command
!$                       # Last argument of last command
```

## Getting Help

```bash
man command              # Manual page
command --help           # Help message
info command             # Info documentation
whatis command           # Brief description
apropos keyword          # Search man pages
tldr command             # Simplified examples
```

---

**Tip**: Practice these commands daily. Start with basics and gradually move to advanced topics. Keep this reference handy during practice sessions!
