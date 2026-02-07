# Basic Commands Lab

## Week 1-2: Fundamentals

### Day 1: File System Navigation

**Objectives:**
- Master directory navigation
- Understand file system hierarchy
- Use path (absolute and relative)

**Commands to Practice:**
```bash
pwd                 # Print working directory
ls                  # List directory contents
ls -la              # List all files with details
cd /path/to/dir     # Change directory
cd ..               # Move up one directory
cd ~                # Go to home directory
cd -                # Go to previous directory
```

**Exercises:**

1. **Navigate the System**
   ```bash
   # Start from home directory
   cd ~
   # Go to root
   cd /
   # List all directories
   ls -la
   # Navigate to /etc
   cd /etc
   # Go back to home
   cd ~
   ```

2. **Explore Directory Structure**
   - Navigate to `/var/log` and list all log files
   - Find your current location
   - Go to `/tmp` and create a test directory
   - Return to home using absolute path

3. **Practice Paths**
   - Use absolute paths to navigate to `/usr/local/bin`
   - Use relative paths to move between sibling directories
   - Use `cd -` to toggle between two directories

### Day 2: File Operations

**Commands to Practice:**
```bash
touch file.txt           # Create empty file
cat file.txt             # Display file content
less file.txt            # View file with pagination
head -n 10 file.txt      # Show first 10 lines
tail -n 10 file.txt      # Show last 10 lines
cp source dest           # Copy file
mv source dest           # Move/rename file
rm file.txt              # Remove file
mkdir dirname            # Create directory
rmdir dirname            # Remove empty directory
rm -rf dirname           # Remove directory recursively
```

**Exercises:**

1. **Create and Manipulate Files**
   ```bash
   # Create a practice directory
   mkdir ~/linux-practice
   cd ~/linux-practice
   
   # Create files
   touch file1.txt file2.txt file3.txt
   
   # Add content
   echo "Hello Linux" > file1.txt
   echo "Daily Practice" >> file1.txt
   
   # View content
   cat file1.txt
   ```

2. **Copy and Move Operations**
   - Copy `file1.txt` to `file1_backup.txt`
   - Move `file2.txt` to a new name `renamed.txt`
   - Create a subdirectory and move files into it
   - Copy entire directory with `cp -r`

3. **File Cleanup**
   - Remove individual files
   - Remove directories
   - Practice safe deletion (always double-check before `rm -rf`)

### Day 3: File Viewing and Searching

**Commands to Practice:**
```bash
cat file.txt                    # Concatenate and display
more file.txt                   # Page through file
less file.txt                   # Better pager
head file.txt                   # Show beginning
tail file.txt                   # Show end
tail -f file.txt                # Follow file updates
grep "pattern" file.txt         # Search in file
find /path -name "*.txt"        # Find files
locate filename                 # Quick file search
which command                   # Find command location
```

**Exercises:**

1. **View System Files**
   ```bash
   # View system info
   cat /etc/os-release
   
   # Check system logs (if accessible)
   sudo tail -f /var/log/syslog
   
   # Find configuration files
   find /etc -name "*.conf" -type f 2>/dev/null | head -20
   ```

2. **Search Practice**
   - Create a file with multiple lines
   - Use grep to search for specific words
   - Use grep with options: `-i` (ignore case), `-v` (invert), `-n` (line numbers)
   - Find all `.sh` files in your home directory

3. **Real-world Scenario**
   - Find all files modified in the last 24 hours
   - Search for files larger than 1MB
   - Locate all Python files in a directory tree

### Day 4-5: Challenge Labs

**Challenge 1: File System Explorer**
Create a script that:
- Lists all directories in `/usr`
- Counts the number of files in each
- Saves the output to a file

**Challenge 2: Backup System**
Create a simple backup:
- Create a directory with sample files
- Copy all `.txt` files to a backup directory
- Add timestamp to backup folder name

**Challenge 3: File Organizer**
- Create files with different extensions
- Organize them into folders by extension
- Generate a report of file counts

## Tips for Success

1. **Practice Daily**: Even 30 minutes makes a difference
2. **Use Man Pages**: `man ls` to learn more about commands
3. **Take Notes**: Document commands you find useful
4. **Make Mistakes**: The best way to learn is by trying
5. **Use Tab Completion**: Save time and reduce errors

## Next Steps

Once comfortable with these basics, move on to:
- Text Processing Lab
- Shell Scripting Lab
- System Administration Lab
