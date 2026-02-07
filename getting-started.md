# Getting Started with Linux Labs

Welcome to your Linux and Bash learning journey! This guide will help you set up and start your daily practice.

## Prerequisites

### Basic Requirements
- A computer with Linux, macOS, or Windows
- Internet connection (for initial setup)
- Text editor (nano, vim, or VS Code)
- 30-60 minutes daily for practice

### No Linux? No Problem!

**Option 1: Windows Users - WSL (Recommended)**
```bash
# Install WSL from PowerShell (Admin)
wsl --install

# Install Ubuntu
wsl --install -d Ubuntu

# Launch Ubuntu
wsl
```

**Option 2: Any OS - Virtual Machine**
- Download VirtualBox: https://www.virtualbox.org/
- Download Ubuntu: https://ubuntu.com/download
- Create VM with 2GB RAM, 20GB disk
- Install Ubuntu in VM

**Option 3: Cloud - Free Tier**
- AWS EC2 Free Tier
- Google Cloud Free Tier
- Azure Free Tier
- DigitalOcean ($100 credit)

**Option 4: Docker Container**
```bash
# If you have Docker installed
docker run -it ubuntu:latest bash
```

**Option 5: Online Terminals**
- replit.com (free Linux terminal)
- katacoda.com (interactive scenarios)
- webminal.org (practice terminal)

## First Steps

### 1. Clone This Repository

```bash
# Using git
git clone https://github.com/Israel2000/linux-bash-labs.git
cd linux-bash-labs

# Or download ZIP and extract
```

### 2. Verify Your Environment

```bash
# Check you're in a bash shell
echo $SHELL

# Check basic commands work
pwd
ls -la
whoami
date
```

### 3. Create Your Practice Space

```bash
# Create practice directory in your home
mkdir -p ~/linux-practice
cd ~/linux-practice

# Create subdirectories for each week
mkdir -p week-{1..8}

# Create your first practice tracker
cp ~/path/to/repo/practice-tracker-template.md ~/linux-practice/week-1-tracker.md
```

## Understanding the Structure

### Repository Layout
```
linux-bash-labs/
├── README.md                      # Main overview
├── 8-week-plan.md                 # Complete 8-week curriculum
├── quick-reference.md             # Command cheat sheet
├── practice-tracker-template.md   # Daily tracking template
├── getting-started.md             # This file
└── labs/
    ├── basics/                    # Week 1-2 labs
    ├── text-processing/           # Week 3-4 labs
    ├── scripting/                 # Week 5-6 labs
    ├── sysadmin/                  # Week 7 labs
    └── networking/                # Week 8 labs
```

### How to Use This Repo

1. **Start with the 8-Week Plan**
   - Read `8-week-plan.md`
   - Understand the progression
   - Set your start date

2. **Daily Practice Routine**
   - Read today's lab in `/labs/` directory
   - Practice commands in your terminal
   - Complete exercises
   - Document in your tracker

3. **Track Your Progress**
   - Use `practice-tracker-template.md`
   - Fill it out weekly
   - Review and reflect

4. **Reference as Needed**
   - Keep `quick-reference.md` open
   - Use it to look up commands
   - Add your own notes

## Your First Practice Session

### Session 1: Getting Comfortable (30 minutes)

**Step 1: Basic Navigation (10 minutes)**
```bash
# Where am I?
pwd

# What's in this directory?
ls

# List with details
ls -la

# Go to home directory
cd ~
pwd

# Go to root
cd /
pwd
ls

# Back to home
cd ~
```

**Step 2: Create Your First File (10 minutes)**
```bash
# Create a practice directory
mkdir ~/linux-practice/day-1
cd ~/linux-practice/day-1

# Create a file
touch my-first-file.txt

# Add some content
echo "Hello, Linux!" > my-first-file.txt
echo "Today is my first day of practice" >> my-first-file.txt

# View the file
cat my-first-file.txt

# View with line numbers
cat -n my-first-file.txt
```

**Step 3: Practice File Operations (10 minutes)**
```bash
# Copy the file
cp my-first-file.txt backup.txt

# List files
ls -l

# Rename a file
mv backup.txt my-backup.txt

# Create another file
echo "This is file 2" > file2.txt

# List all files
ls -l

# Remove a file
rm file2.txt

# Verify it's gone
ls -l
```

**Congratulations!** You've completed your first practice session!

## Daily Practice Workflow

### Morning (Optional - 10 minutes)
1. Open terminal
2. Navigate to practice directory: `cd ~/linux-practice`
3. Review yesterday's notes
4. Read today's lab material

### Main Session (30-60 minutes)
1. **Warm up (5 min)**: Review previous commands
2. **Learn (15 min)**: Read today's lab, try examples
3. **Practice (25 min)**: Complete exercises
4. **Document (10 min)**: Update your tracker

### Evening (Optional - 5 minutes)
1. Quick review of commands learned
2. Note any questions
3. Preview tomorrow's topic

## Tips for Success

### 1. **Practice Daily**
- Consistency is more important than duration
- 20 minutes daily beats 2 hours weekly
- Don't skip more than one day

### 2. **Type Everything**
- Don't copy-paste commands
- Typing helps muscle memory
- Make mistakes and learn

### 3. **Experiment Freely**
- Try variations of commands
- See what happens with different flags
- Breaking things is learning

### 4. **Use Man Pages**
```bash
# Learn about any command
man ls
man grep
man bash

# Quick help
ls --help
grep --help
```

### 5. **Keep a Command Journal**
```bash
# Create a personal cheat sheet
nano ~/linux-practice/my-commands.txt

# Add commands you use often
# Review it weekly
```

### 6. **Safe Practice Environment**
- Always work in your practice directory
- Use test files, not system files
- Be careful with `rm -rf`
- When in doubt, check twice

### 7. **Learn from Errors**
- Errors are normal and valuable
- Read error messages carefully
- Search errors online
- Ask for help in communities

## Common Beginner Mistakes to Avoid

### 1. Case Sensitivity
```bash
# Linux is case-sensitive
cd Desktop   # ✓ Correct
cd desktop   # ✗ Wrong if folder is "Desktop"
```

### 2. Spaces in Commands
```bash
# Space is important
ls-la        # ✗ Wrong
ls -la       # ✓ Correct
```

### 3. Paths
```bash
# Absolute path (starts with /)
cd /home/user/documents

# Relative path (from current location)
cd documents

# Home directory
cd ~/documents
```

### 4. Dangerous Commands
```bash
# Be careful with these
rm -rf /     # ⚠️ NEVER run this!
rm -rf *     # ⚠️ Deletes everything in current directory
chmod -R 777 / # ⚠️ Security nightmare

# Always double-check before:
# - Using rm -rf
# - Changing permissions on system directories
# - Running commands as root/sudo
```

## Getting Help

### Built-in Help
```bash
man command       # Full manual
command --help    # Quick help
info command      # Info pages
whatis command    # Brief description
```

### Online Resources
- **Stack Overflow**: For specific problems
- **Unix & Linux Stack Exchange**: For Unix/Linux questions
- **r/linux4noobs**: Reddit community for beginners
- **Linux Journey**: Interactive tutorials
- **ExplainShell.com**: Explains command syntax

### Practice Platforms
- **OverTheWire Bandit**: Command line game
- **Hackerrank Linux Shell**: Practice exercises
- **LeetCode Shell**: Shell scripting problems

## Setting Goals

### Week 1-2 Goals
- [ ] Comfortable with terminal
- [ ] Can navigate file system
- [ ] Can create, edit, delete files
- [ ] Understand basic permissions

### Week 3-4 Goals
- [ ] Can use grep, sed, awk
- [ ] Understand pipes and redirections
- [ ] Can write simple scripts
- [ ] Comfortable with text processing

### Week 5-6 Goals
- [ ] Can write complete shell scripts
- [ ] Understand functions and loops
- [ ] Can handle errors properly
- [ ] Scripts are production-ready

### Week 7-8 Goals
- [ ] Understand system administration
- [ ] Can manage services and users
- [ ] Know networking basics
- [ ] Can troubleshoot issues

## Motivation Tips

### Remember Why You Started
- Career advancement
- Automation skills
- Better productivity
- Understanding systems
- Personal growth

### Track Wins
- Keep a "wins" journal
- Note every breakthrough
- Celebrate milestones
- Share your progress

### Join Community
- Find study partners
- Join Linux forums
- Share your journey
- Help others when you can

## Ready to Start?

1. ✅ Environment set up
2. ✅ Repository cloned
3. ✅ First session completed
4. ✅ Practice directory created
5. ✅ This guide read

**Next Steps:**
1. Read `8-week-plan.md` to see the full curriculum
2. Start with `labs/basics/README.md`
3. Copy `practice-tracker-template.md` for Week 1
4. Begin your daily practice!

---

**Remember**: Every expert was once a beginner. Stay consistent, be patient, and enjoy the journey!

**Questions?** Create an issue in this repository or reach out to the community.

**Happy Learning! 🚀**
