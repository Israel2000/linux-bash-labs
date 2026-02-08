# linux-bash-labs
plan for linux lab everyday practice


---

## 🎯 Purpose  
A structured, daily Linux practice plan designed to build muscle memory with Bash commands, scripting, navigation, permissions, processes, and networking.

---

# 🗓 Day 1 — Bash Essentials

## 📂 Navigation
```bash
pwd
ls
ls -la
cd /etc
cd ~
cd -

## 📁 Create Directories & Files
```bash
mkdir day1-bash
cd day1-bash

touch file1.txt file2.txt
mkdir scripts logs

## 📦 Copy, Move, Remove
```bash
cp file1.txt logs/
mv file2.txt scripts/
rm backup.txt

## 📄 View & Inspect Files
```bash
cat file1.txt
less /etc/passwd
head -n 5 /etc/passwd
tail -n 5 /etc/passwd

## ✍️ Write & Append Text
```bash
echo "Hello Linux" > file1.txt
echo "Learning Bash" >> file1.txt
cat file1.txt

## 🔐 Permissions & Ownership
```bash
ls -l
chmod 644 file1.txt
chmod 755 hello.sh

## 🔍 Search & Filters
```bash
grep root /etc/passwd
ls -l | grep file

## 🔗 Pipes & Redirection
```bash
cat /etc/passwd | wc -l
ps aux | grep ssh

## ⚙️ Processes & System Info
```bash
ps aux
top
uptime
whoami

## 🌐 Networking Basics
```bash
ip a
ip route
ping -c 4 google.com
ss -tuln

## 🧠 Environment Variables
```bash
echo $HOME
echo $PATH
export MY_VAR="LinuxRocks"
echo $MY_VAR

## 📝 Bash Script Creation
```bash
#!/bin/bash
echo "User: $(whoami)"
echo "Date: $(date)"
echo "Uptime:"
uptime

chmod +x hello.sh
./hello.sh

## 🧾 Save Command History
```bash
🧾 Save Command History


## ✅ End of Day 1
