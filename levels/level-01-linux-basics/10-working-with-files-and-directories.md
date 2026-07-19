# 📁 10 - Working with Files & Directories

## 📍 Where Are We?

**Linux Quest → Level 01: Linux Basics**

```text
✅ 01 - What is Linux?
✅ 02 - History of Linux
✅ 03 - Why Linux?
✅ 04 - Linux Kernel
✅ 05 - Linux Distributions
✅ 06 - GUI vs CLI
✅ 07 - Terminal Basics
✅ 08 - First Linux Commands
✅ 09 - Linux File System Navigation
🟢 10 - Working with Files & Directories (Current Lesson)
```

---

# 📚 In This Lesson You'll Learn

By the end of this lesson, you'll be able to:

- Copy files and folders
- Move and rename files
- Delete files safely
- Search for files
- Identify file types
- Use common file management commands like a Linux user

---

# 👋 Let's Start

Working with files and directories is one of the most common tasks in Linux.

Whether you're writing code, managing projects, editing configuration files, or organizing documents, you'll constantly copy, move, rename, search, and remove files.

The commands in this lesson are used every day by developers, system administrators, DevOps engineers, and cybersecurity professionals.

Let's begin!
---

# 📌 Command

```bash
cp
```

## 📖 What is it?

The `cp` command is used to copy files and directories from one location to another.

## ⚙️ Syntax

```bash
cp source destination
```

To copy a directory:

```bash
cp -r source_directory destination_directory
```

## 💻 Example

```bash
cp notes.txt backup_notes.txt
```

## 📤 Sample Output

A new file named `backup_notes.txt` is created with the same contents as `notes.txt`.

## 🌍 Real World Use

- Creating backups before editing files.
- Copying project files.
- Duplicating configuration files.

## ⚠️ Common Mistakes

- Forgetting `-r` while copying a directory.
- Accidentally overwriting an existing file.

## 💡 Pro Tip

Use:

```bash
cp -i source destination
```

The `-i` option asks for confirmation before overwriting an existing file.

## 🧪 Try It Yourself

```bash
touch notes.txt
cp notes.txt backup.txt
ls
```

---

# 📌 Command

```bash
mv
```

## 📖 What is it?

The `mv` command is used to move files or directories from one location to another. It is also used to rename files and folders.

## ⚙️ Syntax

```bash
mv source destination
```

## 💻 Example 1 – Move a File

```bash
mv notes.txt Documents/
```

## 💻 Example 2 – Rename a File

```bash
mv oldname.txt newname.txt
```

## 🌍 Real World Use

- Organizing project files.
- Renaming scripts.
- Moving log files into backup folders.

## ⚠️ Common Mistakes

- Moving a file to the wrong directory.
- Renaming a file by mistake because the destination doesn't exist.

## 💡 Pro Tip

Always run:

```bash
pwd
ls
```

before using `mv` so you know exactly where you are.

## 🧪 Try It Yourself

```bash
mkdir Practice
touch file1.txt
mv file1.txt Practice/
ls
cd Practice
ls
```

---

# 🔥 Interview Tip

### Question

What is the difference between `cp` and `mv`?

### Answer

- `cp` creates a copy of a file or directory while keeping the original.
- `mv` moves a file or directory to a new location or renames it. The original no longer remains in its previous location.

---

# 🌍 Real World Scenario

Suppose you're working on a project:

```bash
mkdir MyProject
touch app.py
cp app.py backup.py
mv backup.py MyProject/
```

Result:

```
MyProject/
└── backup.py
```

The original `app.py` remains in the current directory, while `backup.py` is moved into the `MyProject` folder.