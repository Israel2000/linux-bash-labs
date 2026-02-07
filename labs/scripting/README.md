# Shell Scripting Lab

## Week 5-6: Shell Scripting Mastery

### Day 1: Bash Basics

**Objectives:**
- Understand shell scripting fundamentals
- Work with variables and data types
- Create executable scripts

**Script Structure:**
```bash
#!/bin/bash
# Script description
# Author: Your Name
# Date: YYYY-MM-DD

# Variables
NAME="value"

# Main code
echo "Hello, $NAME"

# Exit with status
exit 0
```

**Exercises:**

1. **First Script**
   ```bash
   # Create script file
   cat > hello.sh << 'EOF'
   #!/bin/bash
   echo "Hello, Linux Lab!"
   echo "Today is: $(date)"
   echo "Current user: $(whoami)"
   EOF
   
   # Make executable
   chmod +x hello.sh
   
   # Run script
   ./hello.sh
   ```

2. **Variables Practice**
   ```bash
   #!/bin/bash
   
   # String variables
   NAME="Student"
   GREETING="Welcome"
   
   # Numeric variables
   COUNT=10
   PRICE=99.99
   
   # Command substitution
   CURRENT_DIR=$(pwd)
   DATE=$(date +%Y-%m-%d)
   
   # Using variables
   echo "$GREETING, $NAME!"
   echo "Current directory: $CURRENT_DIR"
   echo "Today: $DATE"
   ```

3. **User Input**
   ```bash
   #!/bin/bash
   
   echo "Enter your name:"
   read NAME
   
   echo "Hello, $NAME!"
   
   # Read with prompt
   read -p "Enter your age: " AGE
   echo "You are $AGE years old"
   ```

### Day 2: Conditionals

**Commands:**
```bash
# If statement
if [ condition ]; then
    # commands
elif [ condition ]; then
    # commands
else
    # commands
fi

# Test conditions
[ -f file ]        # File exists
[ -d dir ]         # Directory exists
[ -z "$var" ]      # Variable is empty
[ "$a" = "$b" ]    # Strings equal
[ $a -eq $b ]      # Numbers equal
[ $a -lt $b ]      # Less than
[ $a -gt $b ]      # Greater than
```

**Exercises:**

1. **File Checker**
   ```bash
   #!/bin/bash
   
   FILE="$1"
   
   if [ -z "$FILE" ]; then
       echo "Usage: $0 filename"
       exit 1
   fi
   
   if [ -f "$FILE" ]; then
       echo "$FILE exists"
       echo "Size: $(du -h "$FILE" | cut -f1)"
   else
       echo "$FILE does not exist"
   fi
   ```

2. **Number Comparison**
   ```bash
   #!/bin/bash
   
   read -p "Enter first number: " NUM1
   read -p "Enter second number: " NUM2
   
   if [ $NUM1 -gt $NUM2 ]; then
       echo "$NUM1 is greater than $NUM2"
   elif [ $NUM1 -lt $NUM2 ]; then
       echo "$NUM1 is less than $NUM2"
   else
       echo "$NUM1 equals $NUM2"
   fi
   ```

3. **Menu System**
   ```bash
   #!/bin/bash
   
   echo "Select an option:"
   echo "1. Show date"
   echo "2. Show current directory"
   echo "3. List files"
   
   read -p "Enter choice: " CHOICE
   
   case $CHOICE in
       1) date ;;
       2) pwd ;;
       3) ls -la ;;
       *) echo "Invalid choice" ;;
   esac
   ```

### Day 3: Loops

**Loop Types:**
```bash
# For loop
for item in list; do
    echo "$item"
done

# While loop
while [ condition ]; do
    # commands
done

# Until loop
until [ condition ]; do
    # commands
done

# C-style for loop
for ((i=0; i<10; i++)); do
    echo $i
done
```

**Exercises:**

1. **File Iterator**
   ```bash
   #!/bin/bash
   
   # Loop through files
   for file in *.txt; do
       echo "Processing: $file"
       wc -l "$file"
   done
   
   # Loop through numbers
   for i in {1..5}; do
       echo "Count: $i"
   done
   ```

2. **While Loop Counter**
   ```bash
   #!/bin/bash
   
   COUNT=1
   
   while [ $COUNT -le 10 ]; do
       echo "Iteration: $COUNT"
       COUNT=$((COUNT + 1))
       sleep 1
   done
   ```

3. **Read File Line by Line**
   ```bash
   #!/bin/bash
   
   while IFS= read -r line; do
       echo "Line: $line"
   done < input.txt
   ```

### Day 4: Functions

**Function Syntax:**
```bash
# Define function
function_name() {
    # code
    local var="value"
    return 0
}

# Call function
function_name arg1 arg2

# With return value
result=$(function_name)
```

**Exercises:**

1. **Basic Functions**
   ```bash
   #!/bin/bash
   
   greet() {
       local name=$1
       echo "Hello, $name!"
   }
   
   calculate_sum() {
       local a=$1
       local b=$2
       echo $((a + b))
   }
   
   # Call functions
   greet "Student"
   result=$(calculate_sum 10 20)
   echo "Sum: $result"
   ```

2. **File Operations Function**
   ```bash
   #!/bin/bash
   
   backup_file() {
       local file=$1
       
       if [ ! -f "$file" ]; then
           echo "Error: File not found"
           return 1
       fi
       
       local backup="${file}.backup.$(date +%Y%m%d)"
       cp "$file" "$backup"
       echo "Backed up to: $backup"
       return 0
   }
   
   backup_file "important.txt"
   ```

3. **Menu with Functions**
   ```bash
   #!/bin/bash
   
   show_date() {
       echo "Current date: $(date)"
   }
   
   show_uptime() {
       echo "System uptime:"
       uptime
   }
   
   show_users() {
       echo "Logged in users:"
       who
   }
   
   while true; do
       echo "Menu:"
       echo "1. Date"
       echo "2. Uptime"
       echo "3. Users"
       echo "4. Exit"
       
       read -p "Choice: " choice
       
       case $choice in
           1) show_date ;;
           2) show_uptime ;;
           3) show_users ;;
           4) exit 0 ;;
           *) echo "Invalid" ;;
       esac
   done
   ```

### Day 5: Advanced Scripting

**Topics:**
- Error handling
- Logging
- Argument parsing
- Exit codes
- Debugging

**Exercises:**

1. **Robust Script Template**
   ```bash
   #!/bin/bash
   
   # Error handling
   set -euo pipefail
   
   # Script info
   SCRIPT_NAME=$(basename "$0")
   LOG_FILE="/tmp/${SCRIPT_NAME}.log"
   
   # Logging function
   log() {
       echo "[$(date +'%Y-%m-%d %H:%M:%S')] $*" | tee -a "$LOG_FILE"
   }
   
   # Error handler
   error_exit() {
       log "ERROR: $1"
       exit 1
   }
   
   # Main
   log "Script started"
   
   # Your code here
   
   log "Script completed"
   ```

2. **Argument Parser**
   ```bash
   #!/bin/bash
   
   usage() {
       echo "Usage: $0 [-f file] [-v] [-h]"
       echo "  -f file   Input file"
       echo "  -v        Verbose mode"
       echo "  -h        Show help"
   }
   
   FILE=""
   VERBOSE=0
   
   while getopts "f:vh" opt; do
       case $opt in
           f) FILE="$OPTARG" ;;
           v) VERBOSE=1 ;;
           h) usage; exit 0 ;;
           *) usage; exit 1 ;;
       esac
   done
   
   [ -z "$FILE" ] && { echo "File required"; exit 1; }
   [ $VERBOSE -eq 1 ] && echo "Processing: $FILE"
   ```

3. **System Check Script**
   ```bash
   #!/bin/bash
   
   check_disk_space() {
       local threshold=80
       local usage=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')
       
       if [ $usage -gt $threshold ]; then
           echo "WARNING: Disk usage is ${usage}%"
           return 1
       else
           echo "OK: Disk usage is ${usage}%"
           return 0
       fi
   }
   
   check_memory() {
       free -h
   }
   
   check_services() {
       local services=("ssh" "cron")
       
       for service in "${services[@]}"; do
           if systemctl is-active --quiet "$service"; then
               echo "OK: $service is running"
           else
               echo "WARN: $service is not running"
           fi
       done
   }
   
   echo "=== System Health Check ==="
   check_disk_space
   check_memory
   check_services
   ```

### Challenge Labs

**Challenge 1: Backup Script**
Create a script that:
- Backs up a directory
- Compresses the backup
- Adds timestamp
- Keeps only last 5 backups
- Logs all operations

**Challenge 2: Log Monitor**
Create a script that:
- Monitors a log file
- Alerts on ERROR keywords
- Counts different log levels
- Generates hourly reports

**Challenge 3: System Report**
Create a script that:
- Collects system information
- Checks service status
- Reports disk usage
- Formats as HTML or text

## Tips for Shell Scripting

1. **Always Use SheBang**: Start with `#!/bin/bash`
2. **Quote Variables**: Use `"$var"` not `$var`
3. **Check Exit Codes**: Use `$?` to check command success
4. **Use Functions**: Break code into reusable functions
5. **Add Comments**: Explain complex logic
6. **Test Thoroughly**: Test with different inputs
7. **Use shellcheck**: Validate your scripts

## Next Steps

Move on to:
- System Administration Lab
- Automation with Cron
- Advanced Bash techniques
