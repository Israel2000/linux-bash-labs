# Text Processing Lab

## Week 3-4: Intermediate Text Processing

### Day 1: Grep - Pattern Matching

**Objectives:**
- Master grep for text searching
- Use regular expressions
- Combine grep with other commands

**Commands to Practice:**
```bash
grep "pattern" file.txt              # Basic search
grep -i "pattern" file.txt           # Case-insensitive
grep -v "pattern" file.txt           # Invert match
grep -r "pattern" directory/         # Recursive search
grep -n "pattern" file.txt           # Show line numbers
grep -c "pattern" file.txt           # Count matches
grep -l "pattern" *.txt              # List matching files
grep -E "regex" file.txt             # Extended regex
```

**Exercises:**

1. **Basic Grep Practice**
   ```bash
   # Create sample file
   cat > sample.log << 'EOF'
   ERROR: Connection failed
   INFO: Server starting
   WARNING: Low memory
   ERROR: Database timeout
   INFO: Request processed
   ERROR: File not found
   EOF
   
   # Find all errors
   grep "ERROR" sample.log
   
   # Count errors
   grep -c "ERROR" sample.log
   
   # Case-insensitive search
   grep -i "error" sample.log
   ```

2. **Regular Expression Practice**
   - Match lines starting with ERROR: `grep "^ERROR" file`
   - Match lines ending with numbers: `grep "[0-9]$" file`
   - Match email addresses: `grep -E "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}" file`
   - Match IP addresses: `grep -E "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" file`

3. **Real-world Scenarios**
   - Find all ERROR entries in log files
   - Search for specific user activity
   - Extract all URLs from a file
   - Find configuration entries

### Day 2: Sed - Stream Editor

**Commands to Practice:**
```bash
sed 's/old/new/' file.txt              # Replace first occurrence
sed 's/old/new/g' file.txt             # Replace all occurrences
sed 's/old/new/gi' file.txt            # Case-insensitive replace
sed -i 's/old/new/g' file.txt          # In-place editing
sed -n '1,10p' file.txt                # Print lines 1-10
sed '5d' file.txt                      # Delete line 5
sed '/pattern/d' file.txt              # Delete matching lines
```

**Exercises:**

1. **Text Replacement**
   ```bash
   # Create sample file
   echo "Hello World" > test.txt
   
   # Replace World with Linux
   sed 's/World/Linux/' test.txt
   
   # Replace all occurrences
   echo "test test test" | sed 's/test/example/g'
   ```

2. **Line Operations**
   - Print specific line ranges
   - Delete empty lines: `sed '/^$/d'`
   - Remove comments: `sed '/^#/d'`
   - Add line numbers: `sed = file.txt | sed 'N;s/\n/\t/'`

3. **Advanced Sed**
   - Multiple operations: `sed -e 's/old/new/' -e 's/foo/bar/'`
   - Using sed with variables
   - Complex pattern matching

### Day 3: Awk - Text Processing Language

**Commands to Practice:**
```bash
awk '{print $1}' file.txt              # Print first column
awk '{print $NF}' file.txt             # Print last column
awk '/pattern/ {print}' file.txt       # Print matching lines
awk '{sum+=$1} END {print sum}'        # Sum first column
awk -F: '{print $1}' /etc/passwd       # Custom delimiter
awk 'NR==10' file.txt                  # Print line 10
awk 'length > 80' file.txt             # Lines longer than 80
```

**Exercises:**

1. **Column Processing**
   ```bash
   # Create sample data
   cat > data.txt << 'EOF'
   John 25 100
   Alice 30 150
   Bob 22 120
   Eve 28 180
   EOF
   
   # Print names (column 1)
   awk '{print $1}' data.txt
   
   # Print names and scores
   awk '{print $1, $3}' data.txt
   
   # Calculate average
   awk '{sum+=$3; count++} END {print sum/count}' data.txt
   ```

2. **Conditional Processing**
   - Print lines where column 2 > 25
   - Sum values with condition
   - Format output with printf

3. **Real-world Examples**
   - Parse log files by column
   - Calculate statistics from data
   - Format report outputs
   - Process CSV files

### Day 4: Combining Tools

**Pipe and Combine Commands:**
```bash
# Count unique IPs in log
cat access.log | awk '{print $1}' | sort | uniq -c | sort -rn

# Find top 10 largest files
find . -type f -exec ls -lh {} \; | awk '{print $5, $9}' | sort -rh | head -10

# Process and filter
grep "ERROR" log.txt | awk '{print $1, $2}' | sort | uniq -c
```

**Exercises:**

1. **Log Analysis Pipeline**
   - Extract error messages from log
   - Count occurrences
   - Sort by frequency
   - Display top 10

2. **Data Processing**
   - Read CSV file
   - Filter specific rows
   - Calculate averages
   - Generate report

3. **System Information**
   - Process output of `ps`, `df`, `netstat`
   - Extract relevant information
   - Format for readability

### Day 5: Challenge Labs

**Challenge 1: Log Analyzer**
Create a script that:
- Reads a log file
- Counts different log levels (INFO, WARNING, ERROR)
- Extracts timestamps
- Generates summary report

**Challenge 2: Data Transformer**
- Read a CSV file
- Transform data format
- Calculate statistics
- Export to new format

**Challenge 3: Text Report Generator**
- Process multiple text files
- Extract key information
- Combine into single report
- Format professionally

## Tips for Text Processing

1. **Start Simple**: Test patterns on small files first
2. **Use Quotes**: Single quotes for literal strings, double quotes for variables
3. **Test Regex**: Use online regex testers
4. **Read Man Pages**: `man grep`, `man sed`, `man awk`
5. **Practice Regularly**: Text processing is a fundamental skill

## Next Steps

Move on to:
- Shell Scripting Lab (combine text processing with automation)
- System Administration Lab (apply to real system files)
