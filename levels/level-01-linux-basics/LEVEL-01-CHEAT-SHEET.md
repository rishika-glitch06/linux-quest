# 📋 Level 01 Cheat Sheet

A quick reference for all the important Linux commands covered in Level 01.

---

# 📂 Navigation Commands

| Command | Purpose |
|----------|---------|
| `pwd` | Print current working directory |
| `ls` | List files and directories |
| `cd directory` | Change directory |
| `cd ..` | Move to the parent directory |
| `cd ~` | Go to the home directory |
| `clear` | Clear the terminal screen |

---

# 📁 File & Directory Commands

| Command | Purpose |
|----------|---------|
| `mkdir folder` | Create a new directory |
| `touch file.txt` | Create an empty file |
| `cp source destination` | Copy files or directories |
| `mv source destination` | Move or rename files |
| `rm file.txt` | Delete a file |
| `rm -r folder` | Delete a directory and its contents |
| `rmdir folder` | Delete an empty directory |

---

# 🔍 Search & Information

| Command | Purpose |
|----------|---------|
| `find . -name "file"` | Search for a file |
| `file filename` | Show the file type |
| `history` | Display previously executed commands |

---

# 💻 System Information

| Command | Purpose |
|----------|---------|
| `whoami` | Display the current user |
| `hostname` | Display the system hostname |
| `date` | Show the current date and time |
| `uname -a` | Display detailed system information |

---

# 📌 Symbols to Remember

| Symbol | Meaning |
|--------|---------|
| `/` | Root directory |
| `~` | Home directory |
| `.` | Current directory |
| `..` | Parent directory |

---

# ⚡ Quick Tips

- Always use `pwd` if you're unsure where you are.
- Use `ls` before making changes to a directory.
- Use `cp` to create backups before editing important files.
- Be careful with `rm` because deleted files cannot be easily recovered.
- Prefer absolute paths in scripts for better reliability.

---

# 🧠 Remember

Linux commands are **case-sensitive**.

For example:

```bash
Documents
```

and

```bash
documents
```

are considered different names.

---

# 🎯 Level 01 Complete Commands

```text
pwd
ls
cd
mkdir
touch
cp
mv
rm
rmdir
find
file
history
echo
clear
hostname
date
whoami
uname
```