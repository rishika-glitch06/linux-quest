# 🧪 Lab 03 — Linux File Paths & Navigation

> Practice absolute paths, relative paths, and essential Linux navigation commands.

---

## 🎯 Lab Objectives

By completing this lab, you will learn how to:

- Check your current working directory
- Navigate using absolute paths
- Navigate using relative paths
- Use `/`
- Use `~`
- Use `.`
- Use `..`
- Use `cd -`
- List directory contents
- Explore hidden files
- Practice Linux file system navigation

---

# 🧰 Commands Used

```bash
pwd
ls
ls -la
cd
cd /
cd ~
cd ..
cd -
```

---

# 🧩 Task 01 — Check Your Current Location

Run:

```bash
pwd
```

### 🧠 Observation

Write down your current working directory:

```text
My current directory:
____________________________
```

---

# 🧩 Task 02 — Navigate to Root

Run:

```bash
cd /
```

Now check:

```bash
pwd
```

### Expected Result

```text
/
```

### 🧠 Question

What does `/` represent?

**Your Answer:**

---

# 🧩 Task 03 — Explore Root Directory

Run:

```bash
ls
```

Now run:

```bash
ls -la
```

Observe the directories inside `/`.

Try to identify:

```text
/home
/etc
/var
/usr
/tmp
```

---

# 🧩 Task 04 — Navigate Using an Absolute Path

From the Root Directory, run:

```bash
cd /etc
```

Check your location:

```bash
pwd
```

Expected:

```text
/etc
```

### 🧠 Observation

You used an **absolute path** because the path started with:

```text
/
```

---

# 🧩 Task 05 — Navigate to `/var/log`

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

List the contents:

```bash
ls
```

---

# 🧩 Task 06 — Move to the Parent Directory

You are currently in:

```text
/var/log
```

Run:

```bash
cd ..
```

Now check:

```bash
pwd
```

Expected:

```text
/var
```

### 🧠 Observation

The `..` symbol represents the **parent directory**.

---

# 🧩 Task 07 — Navigate Using a Relative Path

You are currently in:

```text
/var
```

Run:

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

### 🧠 Observation

`log` is a **relative path** because it does not start with `/`.

---

# 🧩 Task 08 — Go to Home Directory

Run:

```bash
cd ~
```

Check:

```bash
pwd
```

You should now be in your user's home directory.

### 🧠 Question

What does `~` represent?

**Your Answer:**

---

# 🧩 Task 09 — Use the `.` Symbol

Run:

```bash
ls .
```

Compare it with:

```bash
ls
```

### 🧠 Observation

The `.` symbol represents the current working directory.

---

# 🧩 Task 10 — Go to Parent Directory

From your home directory, run:

```bash
cd ..
```

Check:

```bash
pwd
```

You should now be in the parent directory of your home directory.

---

# 🧩 Task 11 — Return to Home

Run:

```bash
cd ~
```

Check:

```bash
pwd
```

---

# 🧩 Task 12 — Practice `cd -`

First navigate to:

```bash
cd /etc
```

Now navigate to:

```bash
cd /var
```

Check:

```bash
pwd
```

Now run:

```bash
cd -
```

Check:

```bash
pwd
```

### 🧠 Observation

The `cd -` command takes you to the previous working directory.

---

# 🧩 Task 13 — Explore Hidden Files

Go to your home directory:

```bash
cd ~
```

Run:

```bash
ls
```

Now run:

```bash
ls -a
```

Compare the results.

### 🧠 Observation

Files and directories beginning with `.` are hidden by default.

Examples:

```text
.bashrc
.profile
.gitconfig
```

---

# 🧩 Task 14 — Absolute Path Challenge

Without using `cd ..`, navigate directly to:

```text
/var/log
```

Use:

```bash
cd /var/log
```

Verify:

```bash
pwd
```

Expected:

```text
/var/log
```

---

# 🧩 Task 15 — Relative Path Challenge

Navigate to:

```text
/var
```

using:

```bash
cd /var
```

Now navigate to `/var/log` using only a relative path.

Your command:

```bash
____________________________
```

Expected answer:

```bash
cd log
```

---

# 🧠 Challenge — Path Symbols

Complete the following.

### Challenge 01

Root Directory:

```text
Answer: ______
```

### Challenge 02

Home Directory:

```text
Answer: ______
```

### Challenge 03

Current Directory:

```text
Answer: ______
```

### Challenge 04

Parent Directory:

```text
Answer: ______
```

### Challenge 05

Previous Directory:

```text
Answer: ______
```

---

# 🧩 Navigation Challenge

Start from your home directory.

### Step 1

```bash
cd ~
```

### Step 2

Navigate to:

```text
/home
```

using an absolute path.

```bash
________________
```

### Step 3

Navigate to your user directory using a relative path.

```bash
________________
```

### Step 4

Go to the parent directory.

```bash
________________
```

### Step 5

Return to your home directory.

```bash
________________
```

---

# 📝 Lab Questions

## Q1. What is the difference between an absolute path and a relative path?

**Your Answer:**

---

## Q2. What does `/` represent?

**Your Answer:**

---

## Q3. What does `~` represent?

**Your Answer:**

---

## Q4. What does `.` represent?

**Your Answer:**

---

## Q5. What does `..` represent?

**Your Answer:**

---

## Q6. What does `cd -` do?

**Your Answer:**

---

## Q7. What command shows your current working directory?

**Your Answer:**

---

## Q8. What command shows hidden files?

**Your Answer:**

---

# 🎯 Scenario-Based Practice

## Scenario 01

You are currently in:

```text
/home/rishika
```

You want to reach:

```text
/home/rishika/Documents
```

Write an absolute path command:

```bash
____________________________
```

---

## Scenario 02

You are currently in:

```text
/home/rishika
```

You want to reach:

```text
/home/rishika/Documents
```

Write a relative path command:

```bash
____________________________
```

---

## Scenario 03

You are currently in:

```text
/home/rishika/Documents
```

You want to go to:

```text
/home/rishika
```

Command:

```bash
____________________________
```

---

## Scenario 04

You are currently in:

```text
/etc
```

You navigate to:

```text
/var
```

Now you want to return to `/etc`.

Command:

```bash
____________________________
```

---

## Scenario 05

You don't know where you are in the file system.

Which command should you use?

```bash
____________________________
```

---

# 🏆 Mini Quest

Complete the following navigation sequence without looking at previous tasks.

```text
Start
  ↓
Home Directory
  ↓
Root Directory
  ↓
/var
  ↓
/var/log
  ↓
Parent Directory
  ↓
Previous Directory
  ↓
Home Directory
```

Write the commands:

```bash
# 1. Home
________________

# 2. Root
________________

# 3. /var
________________

# 4. /var/log
________________

# 5. Parent Directory
________________

# 6. Previous Directory
________________

# 7. Home
________________
```

---

# 📊 Path Practice Table

Complete this table.

| Current Location | Command | New Location |
|---|---|---|
| `/home/rishika` | `cd /var` | |
| `/var` | `cd log` | |
| `/var/log` | `cd ..` | |
| `/var` | `cd /etc` | |
| `/etc` | `cd -` | |
| Any location | `cd ~` | |

---

# ✅ Lab Completion Checklist

- [ ] Used `pwd`
- [ ] Used `ls`
- [ ] Used `ls -la`
- [ ] Navigated to `/`
- [ ] Navigated using an absolute path
- [ ] Navigated using a relative path
- [ ] Used `~`
- [ ] Used `.`
- [ ] Used `..`
- [ ] Used `cd -`
- [ ] Explored hidden files
- [ ] Completed Path Symbols Challenge
- [ ] Completed Navigation Challenge
- [ ] Completed Scenario-Based Practice
- [ ] Completed Mini Quest
- [ ] Completed Path Practice Table

---

# 🏆 Quest Complete

You have successfully completed:

> 🐧 **Level 02 — Lab 03: Linux File Paths & Navigation**

You can now navigate the Linux file system using absolute paths, relative paths, and special path symbols.

---

## 🔗 Navigation

⬅️ [Lesson 03 — Linux File Paths & Navigation](../../levels/level-02-file-system/03-linux-file-paths-and-navigation.md)

🖼️ [Linux File Paths & Navigation Diagram](../../assets/diagrams/linux-file-paths-navigation.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🏠 [Back to Linux Quest](../../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 03 Lab**

> *Practice the path. Master the navigation.*