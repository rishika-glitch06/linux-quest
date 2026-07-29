# 🐧 Linux Quest — Level 02
# Hands-on Lab 07: Linux File System

> Practice navigating the Linux file system, working with directories and files, checking disk usage, inspecting storage devices, and understanding mount points.

---

# 🎯 Lab Objectives

By completing this lab, you will practice:

- Navigating the Linux file system
- Understanding absolute and relative paths
- Working with `/`, `/home`, `/etc`, `/var`, `/tmp`
- Creating files and directories
- Copying and moving files
- Finding files
- Checking disk usage
- Inspecting block devices
- Understanding mount points
- Creating symbolic links
- Working with file system information

---

# 🧰 Requirements

You need:

- A Linux system
- Ubuntu / Debian / Kali / Fedora / WSL / Virtual Machine
- Terminal access

> ⚠️ Most tasks can be performed without `sudo`. Use `sudo` only when explicitly required.

---

# 🟢 Task 01 — Identify Your Current Location

Run:

```bash
pwd
```

### Questions

1. What is your current working directory?
2. Does the path start with `/`?
3. Is it an absolute path?

### Expected Learning

Understand the concept of the current working directory.

---

# 🟢 Task 02 — Explore the Root Directory

Run:

```bash
ls /
```

Then:

```bash
ls -la /
```

### Questions

1. Which directories do you see?
2. Can you find:
   - `/etc`
   - `/home`
   - `/tmp`
   - `/var`
   - `/usr`
   - `/dev`

### Expected Learning

Understand the top-level Linux file system hierarchy.

---

# 🟢 Task 03 — Navigate Using `cd`

Run:

```bash
cd /
```

Then:

```bash
pwd
```

Now navigate to:

```bash
cd /tmp
```

Check:

```bash
pwd
```

Return to your home directory:

```bash
cd ~
```

### Challenge

Move to the parent directory:

```bash
cd ..
```

### Questions

1. What does `/` represent?
2. What does `~` represent?
3. What does `..` represent?

---

# 🟢 Task 04 — Create a Practice Directory

Go to your home directory:

```bash
cd ~
```

Create:

```bash
mkdir linux-filesystem-lab
```

Enter it:

```bash
cd linux-filesystem-lab
```

Verify:

```bash
pwd
```

---

# 🟢 Task 05 — Create a Directory Structure

Inside `linux-filesystem-lab`, run:

```bash
mkdir -p projects/python
mkdir -p projects/linux
mkdir -p documents
mkdir -p backups
```

View the structure:

```bash
find .
```

If the `tree` command is available:

```bash
tree
```

### Expected Structure

```text
linux-filesystem-lab/
├── backups/
├── documents/
└── projects/
    ├── linux/
    └── python/
```

---

# 🟢 Task 06 — Create Files

Run:

```bash
touch documents/notes.txt
touch projects/python/app.py
touch projects/linux/commands.md
```

Check:

```bash
find .
```

---

# 🟢 Task 07 — Write Data Into a File

Run:

```bash
echo "Linux File System Lab" > documents/notes.txt
```

View the file:

```bash
cat documents/notes.txt
```

Add another line:

```bash
echo "Learning Linux is fun!" >> documents/notes.txt
```

View again:

```bash
cat documents/notes.txt
```

### Question

What is the difference between:

```bash
>
```

and:

```bash
>>
```

---

# 🟡 Task 08 — Copy Files

Copy the notes file:

```bash
cp documents/notes.txt backups/notes-backup.txt
```

Verify:

```bash
ls -l backups/
```

### Challenge

Copy the entire `projects` directory into `backups`:

```bash
cp -r projects backups/
```

Check:

```bash
find backups/
```

---

# 🟡 Task 09 — Move and Rename Files

Rename:

```bash
mv documents/notes.txt documents/linux-notes.txt
```

Check:

```bash
ls documents/
```

Move the file to `backups`:

```bash
mv documents/linux-notes.txt backups/
```

Check:

```bash
ls documents/
ls backups/
```

---

# 🟡 Task 10 — Create Hidden Files

Create a hidden file:

```bash
touch .hidden-file
```

Run:

```bash
ls
```

Now run:

```bash
ls -a
```

### Questions

1. Why was `.hidden-file` not visible with `ls`?
2. Which command displays hidden files?

---

# 🟡 Task 11 — Inspect File Information

Run:

```bash
ls -lh
```

Then:

```bash
ls -lah
```

Observe:

- Permissions
- Owner
- Group
- File size
- Modification time
- File name

---

# 🟡 Task 12 — Find Files

Find all `.txt` files:

```bash
find . -name "*.txt"
```

Find all Markdown files:

```bash
find . -name "*.md"
```

Find Python files:

```bash
find . -name "*.py"
```

### Challenge

Find all hidden files:

```bash
find . -name ".*"
```

---

# 🟠 Task 13 — Check Disk Usage With `df`

Run:

```bash
df -h
```

Observe:

- File system
- Size
- Used
- Available
- Usage percentage
- Mount point

### Questions

1. Which file system contains your root directory?
2. What is its usage percentage?
3. How much free space is available?

---

# 🟠 Task 14 — Check Directory Usage With `du`

From your home directory, run:

```bash
du -sh linux-filesystem-lab
```

Check individual directories:

```bash
du -sh linux-filesystem-lab/*
```

Sort by size:

```bash
du -sh linux-filesystem-lab/* | sort -h
```

### Question

Which directory is using the most space?

---

# 🟠 Task 15 — Inspect Block Devices

Run:

```bash
lsblk
```

If available:

```bash
lsblk -f
```

Observe:

- Disk names
- Partitions
- File systems
- Mount points

### Questions

1. What is the name of your primary disk?
2. Which partitions are mounted?
3. Which file system is being used?

---

# 🟠 Task 16 — Explore `/etc`

Run:

```bash
ls /etc
```

Check:

```bash
cat /etc/hostname
```

Check:

```bash
cat /etc/hosts
```

### Questions

1. What is your hostname?
2. What type of information is stored in `/etc`?

---

# 🟠 Task 17 — Explore `/var/log`

Run:

```bash
ls /var/log
```

If permitted:

```bash
ls -lh /var/log
```

Explore log files:

```bash
find /var/log -maxdepth 1 -type f
```

### Question

Why is `/var/log` important for system administrators?

---

# 🟠 Task 18 — Explore `/tmp`

Run:

```bash
ls -la /tmp
```

Create a temporary file:

```bash
touch /tmp/linux-quest-test.txt
```

Verify:

```bash
ls -l /tmp/linux-quest-test.txt
```

Remove it:

```bash
rm /tmp/linux-quest-test.txt
```

---

# 🔴 Task 19 — Create a Symbolic Link

Go to your lab directory:

```bash
cd ~/linux-filesystem-lab
```

Create a file:

```bash
echo "This is the original file" > documents/original.txt
```

Create a symbolic link:

```bash
ln -s documents/original.txt original-link.txt
```

Check:

```bash
ls -l
```

Read through the link:

```bash
cat original-link.txt
```

### Expected Concept

```text
original-link.txt
        │
        ▼
documents/original.txt
```

---

# 🔴 Task 20 — Test the Symbolic Link

Delete the original file:

```bash
rm documents/original.txt
```

Now run:

```bash
cat original-link.txt
```

### Question

What happened?

### Expected Learning

A symbolic link points to a path. If the target disappears, the symbolic link becomes broken.

---

# 🔴 Task 21 — Understand Mount Points

Run:

```bash
findmnt
```

Or:

```bash
mount
```

You can also use:

```bash
df -h
```

Observe the mount points.

Typical examples:

```text
/
/home
/boot
/tmp
```

### Question

What is the purpose of a mount point?

---

# 🔴 Task 22 — Explore `/proc`

Run:

```bash
cat /proc/cpuinfo
```

Then:

```bash
cat /proc/meminfo
```

Check your kernel version:

```bash
cat /proc/version
```

### Questions

1. Is `/proc` a normal disk directory?
2. What type of information does it provide?

---

# 🔴 Task 23 — Explore `/sys`

Run:

```bash
ls /sys
```

Explore:

```bash
ls /sys/class
```

### Question

What kind of information does `/sys` expose?

---

# 🔴 Task 24 — Disk Full Investigation

Imagine that your system reports:

```text
No space left on device
```

Start troubleshooting.

First:

```bash
df -h
```

Then identify large directories:

```bash
sudo du -xhd1 / | sort -h
```

Check `/var`:

```bash
sudo du -sh /var/*
```

### Challenge

Explain the troubleshooting flow:

```text
Disk Full
    ↓
df -h
    ↓
Identify Full File System
    ↓
du
    ↓
Find Large Directory
    ↓
Find Large Files
    ↓
Clean Unnecessary Data
```

---

# 🔴 Task 25 — File System Investigation Challenge

Answer the following without searching online.

### Question 1

What is the difference between:

```text
/
```

and:

```text
/root
```

---

### Question 2

What is the difference between:

```text
/home
```

and:

```text
/usr
```

---

### Question 3

What is the difference between:

```bash
df -h
```

and:

```bash
du -sh
```

---

### Question 4

What is the difference between:

```text
/dev
```

and:

```text
/proc
```

---

### Question 5

What is a mount point?

---

### Question 6

What is the purpose of `/etc/fstab`?

---

### Question 7

What is an inode?

---

### Question 8

What is the difference between a symbolic link and a hard link?

---

# 🏆 Final Challenge

Create this structure:

```text
linux-filesystem-final/
├── data/
│   ├── raw/
│   │   └── data.csv
│   └── processed/
│       └── result.csv
├── logs/
│   └── application.log
├── scripts/
│   └── backup.sh
└── README.md
```

### Step 1

Create the directories:

```bash
mkdir -p linux-filesystem-final/data/raw
mkdir -p linux-filesystem-final/data/processed
mkdir -p linux-filesystem-final/logs
mkdir -p linux-filesystem-final/scripts
```

### Step 2

Create files:

```bash
touch linux-filesystem-final/data/raw/data.csv
touch linux-filesystem-final/data/processed/result.csv
touch linux-filesystem-final/logs/application.log
touch linux-filesystem-final/scripts/backup.sh
touch linux-filesystem-final/README.md
```

### Step 3

Verify:

```bash
find linux-filesystem-final
```

### Step 4

Check size:

```bash
du -sh linux-filesystem-final
```

### Step 5

Create a symbolic link:

```bash
ln -s data/raw/data.csv linux-filesystem-final/raw-data-link.csv
```

### Step 6

Verify:

```bash
ls -l linux-filesystem-final
```

---

# 📸 Evidence Checklist

For your Linux Quest learning record, capture screenshots of:

- [ ] `pwd`
- [ ] `ls -la /`
- [ ] Directory structure
- [ ] `df -h`
- [ ] `du -sh`
- [ ] `lsblk`
- [ ] `findmnt`
- [ ] Symbolic link
- [ ] Final challenge structure

---

# 🧠 What You Learned

After completing this lab, you should be able to:

```text
Navigate Linux File System
        ↓
Create & Manage Files
        ↓
Understand Directory Hierarchy
        ↓
Find Files
        ↓
Check Disk Usage
        ↓
Inspect Disks & Partitions
        ↓
Understand Mount Points
        ↓
Create Symbolic Links
        ↓
Troubleshoot Disk Space
```

---

# ✅ Lab Completion Checklist

- [ ] Navigate the file system
- [ ] Understand absolute paths
- [ ] Understand relative paths
- [ ] Create directories
- [ ] Create files
- [ ] Copy files
- [ ] Move files
- [ ] Rename files
- [ ] Delete files
- [ ] Find files
- [ ] Work with hidden files
- [ ] Use `df`
- [ ] Use `du`
- [ ] Use `lsblk`
- [ ] Explore `/etc`
- [ ] Explore `/var/log`
- [ ] Explore `/tmp`
- [ ] Explore `/proc`
- [ ] Explore `/sys`
- [ ] Understand mount points
- [ ] Create symbolic links
- [ ] Troubleshoot disk usage
- [ ] Complete final challenge

---

# 🏁 Lab Status

```text
🧪 Lab 07 — Linux File System

Status: 🟡 In Progress

Navigation          ⬜
File Management     ⬜
Disk Usage          ⬜
Storage             ⬜
Mount Points        ⬜
Symbolic Links      ⬜
Troubleshooting     ⬜
Final Challenge     ⬜
```

> 🐧 **Linux Quest — Level 02**

> *Don't just learn the file system. Explore it.*