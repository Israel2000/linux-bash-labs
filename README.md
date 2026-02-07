# linux-bash-labs
plan for linux lab everyday practice

day1-bash/
├── hello.sh
├── commands.txt
├── file1.txt
├── scripts/
├── logs/
ji9

#Nav
pwd
ls
ls -la
cd
cd ~
cd -
#Create Dir & Files
mkdir day1-bash
cd day1-bash

touch file1.txt file2.txt
mkdir scripts logs

#📦 Copy, Move, Remove
cp file1.txt logs/
mv file2.txt scripts/
rm backup.txt

#📄 View & Edit Files
cat file1.txt
less /etc/passwd
head -n 5 /etc/passwd
tail -n 5 /etc/passwd

#✍️ Write & Append Text
echo "Hello Linux" > file1.txt
echo "Learning Bash" >> file1.txt
cat file1.txt

#🔐 Permissions & Ownership
ls -l
chmod 644 file1.txt
chmod 755 hello.sh

#🔍 Search & Filters
grep root /etc/passwd
ls -l | grep file

#Pipes & Redirection
cat /etc/passwd | wc -l
ps aux | grep ssh

#⚙️ Processes & System Info
ps aux
top
uptime
whoami

#🌐 Networking Basics
ip a
ip route
ping -c 4 google.com
ss -tuln

# 🧠 Environment Variables
echo $HOME
echo $PATH
export MY_VAR="LinuxRocks"
echo $MY_VAR

#📝 Bash Script Creation
nano hello.sh
#!/bin/bash
echo "User: $(whoami)"
echo "Date: $(date)"
echo "Uptime:"
uptime
chmod +x hello.sh
./hello.sh
history | tail -n 30 > commands.txt
-- --End of day1--


