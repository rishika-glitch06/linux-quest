# 🧪 Lab 01 — Explore the Linux File System

> Learn how to navigate and explore the Linux File System Hierarchy using basic Linux commands.

---

## 🎯 Lab Objectives

By completing this lab, you will learn how to:

- Navigate the Linux file system
- Understand the Root Directory `/`
- Use `pwd`
- Use `ls`
- Use `cd`
- Explore important directories
- Understand absolute paths
- Understand relative paths

---

# 🧰 Commands Used

```bash
pwd
ls
ls -l
ls -a
cd
cd /
cd ..
cd ~
```

---

# 🧩 Task 01 — Check Your Current Location

Run:

```bash
pwd
```

### Expected Result

You should see the absolute path of your current working directory.

Example:

```text
/home/rishika
```

### 🧠 What did you learn?

`pwd` means:

```text
Print Working Directory
```

It tells you where you currently are in the Linux file system.

---

# 🧩 Task 02 — Explore the Root Directory

Navigate to the Root Directory:

```bash
cd /
```

Now check your location:

```bash
pwd
```

Expected:

```text
/
```

---

# 🧩 Task 03 — List Root Directory Contents

Run:

```bash
ls
```

For detailed information:

```bash
ls -l
```

To include hidden files:

```bash
ls -la
```

Observe directories such as:

```text
bin
boot
dev
etc
home
lib
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var
```

---

# 🧩 Task 04 — Explore `/home`

Run:

```bash
cd /home
```

Check your location:

```bash
pwd
```

List the contents:

```bash
ls
```

You should see directories belonging to normal users.

Example:

```text
rishika
```

---

# 🧩 Task 05 — Explore Your Home Directory

Navigate to your home directory:

```bash
cd ~
```

Check your location:

```bash
pwd
```

List your files:

```bash
ls
```

List detailed information:

```bash
ls -la
```

---

# 🧩 Task 06 — Move to the Parent Directory

Run:

```bash
cd ..
```

Check your location:

```bash
pwd
```

The `..` represents the parent directory.

---

# 🧩 Task 07 — Return to Home

Run:

```bash
cd ~
```

or simply:

```bash
cd
```

Verify:

```bash
pwd
```

---

# 🧩 Task 08 — Explore `/etc`

Run:

```bash
ls /etc
```

You can also navigate there:

```bash
cd /etc
```

Check:

```bash
pwd
```

You should see:

```text
/etc
```

Explore some files:

```bash
ls /etc
```

---

# 🧩 Task 09 — Explore `/var`

Run:

```bash
ls /var
```

Now explore logs:

```bash
ls /var/log
```

Observe the different log files and directories.

---

# 🧩 Task 10 — Explore `/tmp`

Run:

```bash
ls /tmp
```

This directory contains temporary files created by applications and users.

---

# 🧩 Task 11 — Practice Absolute Paths

Run:

```bash
cd /var/log
```

Check:

```bash
pwd
```

Expected:

```text
/var/log
```

An absolute path starts from the Root Directory `/`.

Example:

```text
/var/log
```

---

# 🧩 Task 12 — Practice Relative Paths

Navigate to:

```bash
cd /var
```

Now run:

```bash
cd log
```

Check:

```bash
pwd
```

Expected:

```text
/var/log
```

Here, `log` is a relative path from `/var`.

---

# 🧠 Challenge

Without looking at the commands above, try to complete these tasks:

### Challenge 01

Go to the Root Directory.

```bash
______
```

### Challenge 02

Check your current location.

```bash
______
```

### Challenge 03

List all files including hidden files.

```bash
______
```

### Challenge 04

Go to your home directory.

```bash
______
```

### Challenge 05

Move one directory up.

```bash
______
```

---

# 📝 Lab Questions

Answer these questions after completing the lab.

### Q1. What does `pwd` do?

**Your Answer:**

---

### Q2. What does `/` represent?

**Your Answer:**

---

### Q3. What is the difference between `cd /` and `cd ~`?

**Your Answer:**

---

### Q4. What does `..` represent?

**Your Answer:**

---

### Q5. What is the difference between an absolute path and a relative path?

**Your Answer:**

---

# ✅ Lab Completion Checklist

- [ ] Used `pwd`
- [ ] Explored `/`
- [ ] Used `ls`
- [ ] Used `ls -la`
- [ ] Explored `/home`
- [ ] Explored `/etc`
- [ ] Explored `/var`
- [ ] Explored `/var/log`
- [ ] Explored `/tmp`
- [ ] Practiced absolute paths
- [ ] Practiced relative paths
- [ ] Completed the challenge
- [ ] Answered lab questions

---

# 🏆 Quest Complete

You have successfully completed:

> 🐧 **Level 02 — Lab 01: Explore the Linux File System**

You can now navigate the Linux file system and understand the basic hierarchy.

---

## 🔗 Navigation

📖 [Level 02 — Linux File System](../../levels/level-02-file-system/README.md)

🖼️ [Linux File System Hierarchy Diagram](../../assets/diagrams/linux-file-system-hierarchy.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🏠 [Back to Linux Quest](../../README.md)