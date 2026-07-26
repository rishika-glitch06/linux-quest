# 🧪 Lab 04 — File & Directory Management

> Practice creating, copying, moving, renaming, viewing, and deleting files and directories in Linux.

---

# 🎯 Lab Objectives

By completing this lab, you will learn how to:

- Create files using `touch`
- Create directories using `mkdir`
- Create nested directories using `mkdir -p`
- Copy files using `cp`
- Copy directories using `cp -r`
- Move files using `mv`
- Rename files using `mv`
- Delete files using `rm`
- Delete empty directories using `rmdir`
- Delete directories recursively using `rm -r`
- View file contents using `cat`
- Use `less` and `more`
- Practice wildcards

---

# 🧰 Commands Used

```bash
touch
mkdir
mkdir -p
cp
cp -r
mv
rm
rmdir
rm -r
cat
less
more
```

---

# 🧩 Task 01 — Create a Practice Directory

Create a directory named:

```text
file-management-lab
```

Run:

```bash
mkdir file-management-lab
```

Enter the directory:

```bash
cd file-management-lab
```

Verify your location:

```bash
pwd
```

---

# 🧩 Task 02 — Create Files

Create three files:

```bash
touch notes.txt
touch backup.txt
touch linux.txt
```

Check:

```bash
ls
```

Expected files:

```text
notes.txt
backup.txt
linux.txt
```

---

# 🧩 Task 03 — Create a Directory

Create:

```bash
mkdir Projects
```

Check:

```bash
ls
```

Expected:

```text
Projects
```

---

# 🧩 Task 04 — Create Nested Directories

Run:

```bash
mkdir -p Projects/Linux/Lesson04
```

Check:

```bash
ls -R
```

Expected structure:

```text
Projects/
└── Linux/
    └── Lesson04/
```

---

# 🧩 Task 05 — Add Content to a File

Run:

```bash
echo "Linux Quest Lesson 04" > notes.txt
```

View the content:

```bash
cat notes.txt
```

Expected:

```text
Linux Quest Lesson 04
```

---

# 🧩 Task 06 — Copy a File

Copy `notes.txt` to `notes_backup.txt`.

Run:

```bash
cp notes.txt notes_backup.txt
```

Check:

```bash
ls
```

You should now have:

```text
notes.txt
notes_backup.txt
```

---

# 🧩 Task 07 — Copy a Directory

Copy the entire `Projects` directory.

Run:

```bash
cp -r Projects Projects_Backup
```

Check:

```bash
ls
```

Expected:

```text
Projects
Projects_Backup
```

---

# 🧩 Task 08 — Move a File

Move `linux.txt` into the `Projects` directory.

Run:

```bash
mv linux.txt Projects/
```

Check:

```bash
ls
```

Then:

```bash
ls Projects
```

You should find:

```text
linux.txt
```

---

# 🧩 Task 09 — Rename a File

Rename:

```text
backup.txt
```

to:

```text
backup_old.txt
```

Run:

```bash
mv backup.txt backup_old.txt
```

Check:

```bash
ls
```

---

# 🧩 Task 10 — Delete a File

Delete:

```text
backup_old.txt
```

Run:

```bash
rm backup_old.txt
```

Verify:

```bash
ls
```

---

# 🧩 Task 11 — Remove an Empty Directory

Create an empty directory:

```bash
mkdir EmptyFolder
```

Remove it:

```bash
rmdir EmptyFolder
```

Verify:

```bash
ls
```

---

# 🧩 Task 12 — Delete a Directory with Contents

Create a test directory:

```bash
mkdir TestFolder
```

Create a file inside it:

```bash
touch TestFolder/test.txt
```

Try:

```bash
rmdir TestFolder
```

Observe the result.

The command should fail because the directory is not empty.

Now remove it recursively:

```bash
rm -r TestFolder
```

Verify:

```bash
ls
```

---

# 🧩 Task 13 — Practice `rm -rf`

⚠️ **WARNING: Be extremely careful with this command.**

Create a test directory:

```bash
mkdir ForceDeleteTest
```

Create a file:

```bash
touch ForceDeleteTest/test.txt
```

Remove it using:

```bash
rm -rf ForceDeleteTest
```

Verify:

```bash
ls
```

The directory should no longer exist.

---

# 🧩 Task 14 — View File Contents

Create a file:

```bash
echo "Welcome to Linux Quest" > welcome.txt
```

Display the content:

```bash
cat welcome.txt
```

---

# 🧩 Task 15 — Practice `less`

Run:

```bash
less welcome.txt
```

Press:

```text
q
```

to exit.

---

# 🧩 Task 16 — Practice Wildcards

Create multiple text files:

```bash
touch file1.txt
touch file2.txt
touch file3.txt
```

List all text files:

```bash
ls *.txt
```

---

# 🧩 Task 17 — Practice the `?` Wildcard

Run:

```bash
ls file?.txt
```

This should match:

```text
file1.txt
file2.txt
file3.txt
```

---

# 🧩 Task 18 — File Management Challenge

Complete the following sequence without looking at previous tasks.

### Step 1

Create:

```text
LinuxPractice
```

```bash
mkdir LinuxPractice
```

### Step 2

Enter it:

```bash
cd LinuxPractice
```

### Step 3

Create:

```text
notes.txt
```

```bash
touch notes.txt
```

### Step 4

Add content:

```bash
echo "Linux File Management" > notes.txt
```

### Step 5

Create a backup:

```bash
cp notes.txt backup.txt
```

### Step 6

Rename the backup:

```bash
mv backup.txt notes_backup.txt
```

### Step 7

Create a directory:

```bash
mkdir Archive
```

### Step 8

Move the backup into Archive:

```bash
mv notes_backup.txt Archive/
```

### Step 9

Check:

```bash
ls
```

### Step 10

Check Archive:

```bash
ls Archive
```

---

# 🧠 Challenge Questions

## Q1. Which command creates an empty file?

```text
Answer:
```

---

## Q2. Which command creates a directory?

```text
Answer:
```

---

## Q3. Which command creates nested directories?

```text
Answer:
```

---

## Q4. How do you copy a file?

```text
Answer:
```

---

## Q5. How do you copy a directory?

```text
Answer:
```

---

## Q6. Which command is used for moving and renaming?

```text
Answer:
```

---

## Q7. How do you delete a file?

```text
Answer:
```

---

## Q8. How do you delete an empty directory?

```text
Answer:
```

---

## Q9. How do you delete a directory containing files?

```text
Answer:
```

---

## Q10. What is the difference between `rm -r` and `rm -rf`?

```text
Answer:
```

---

# 🧩 Scenario-Based Practice

## Scenario 01

Create a file named:

```text
project.txt
```

Command:

```bash
________________________
```

---

## Scenario 02

Create a directory named:

```text
Projects
```

Command:

```bash
________________________
```

---

## Scenario 03

Copy:

```text
project.txt
```

to:

```text
project_backup.txt
```

Command:

```bash
________________________
```

---

## Scenario 04

Rename:

```text
project.txt
```

to:

```text
linux_project.txt
```

Command:

```bash
________________________
```

---

## Scenario 05

Move:

```text
linux_project.txt
```

into:

```text
Projects/
```

Command:

```bash
________________________
```

---

## Scenario 06

Delete:

```text
project_backup.txt
```

Command:

```bash
________________________
```

---

## Scenario 07

Create the following structure:

```text
LinuxQuest/
└── Level02/
    └── Lesson04/
```

Command:

```bash
________________________
```

---

# ⚡ Rapid-Fire Practice

Complete the commands:

```text
Create file:
________________

Create directory:
________________

Create nested directories:
________________

Copy file:
________________

Copy directory:
________________

Move file:
________________

Rename file:
________________

Delete file:
________________

Delete empty directory:
________________

Delete directory recursively:
________________

Display file:
________________

View large file:
________________
```

---

# 🎯 Final Mini Quest

Starting from your home directory, complete this sequence:

```text
Home
  │
  ▼
Create LinuxQuest
  │
  ▼
Enter LinuxQuest
  │
  ▼
Create Level02
  │
  ▼
Enter Level02
  │
  ▼
Create notes.txt
  │
  ▼
Write content
  │
  ▼
Create backup
  │
  ▼
Create Archive
  │
  ▼
Move backup to Archive
  │
  ▼
Rename backup
```

Try to complete the entire quest using Linux commands.

---

# ✅ Lab Completion Checklist

- [ ] Created files using `touch`
- [ ] Created directories using `mkdir`
- [ ] Created nested directories using `mkdir -p`
- [ ] Copied files using `cp`
- [ ] Copied directories using `cp -r`
- [ ] Moved files using `mv`
- [ ] Renamed files using `mv`
- [ ] Deleted files using `rm`
- [ ] Deleted empty directories using `rmdir`
- [ ] Deleted directories using `rm -r`
- [ ] Practiced `rm -rf` safely
- [ ] Viewed files using `cat`
- [ ] Practiced `less`
- [ ] Practiced wildcards
- [ ] Completed Scenario-Based Practice
- [ ] Completed Rapid-Fire Practice
- [ ] Completed Final Mini Quest

---

# 🏆 Quest Complete

You have successfully completed:

> 🐧 **Level 02 — Lab 04: File & Directory Management**

You can now create, copy, move, rename, view, and delete files and directories using Linux commands.

---

## 🔗 Navigation

⬅️ [Lesson 04 — File & Directory Management](../levels/level-02-file-system/04-file-and-directory-management.md)

🖼️ [File & Directory Management Diagram](../assets/diagrams/file-and-directory-management.md)

💼 [Linux File System Interview Preparation](../interview-prep/linux-file-system.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 04 Lab**

> *Create. Copy. Move. Manage.*