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
---

# 📌 Command

```bash
rm
```

## 📖 What is it?

The `rm` command is used to delete files and directories.

## ⚙️ Syntax

```bash
rm filename
```

To remove a directory and all its contents:

```bash
rm -r directory_name
```

## 💻 Example

```bash
rm notes.txt
```

## 🌍 Real World Use

- Removing unnecessary files
- Cleaning project folders
- Deleting temporary files

## ⚠️ Common Mistake

`rm` permanently deletes files. There is no Recycle Bin in the terminal.

## 💡 Pro Tip

Use:

```bash
rm -i filename
```

to ask for confirmation before deleting.

## 🧪 Try It Yourself

```bash
touch temp.txt
rm temp.txt
```

---

# 📌 Command

```bash
find
```

## 📖 What is it?

The `find` command searches for files and directories.

## ⚙️ Syntax

```bash
find location -name filename
```

## 💻 Example

```bash
find . -name "README.md"
```

## 📤 Sample Output

```text
./README.md
```

## 🌍 Real World Use

Finding configuration files, source code, logs, or documents in large projects.

## ⚠️ Common Mistake

Using the wrong search location.

`.` means **current directory**.

## 💡 Pro Tip

Search only for Python files:

```bash
find . -name "*.py"
```

---

# 📌 Command

```bash
file
```

## 📖 What is it?

The `file` command identifies the type of a file.

## ⚙️ Syntax

```bash
file filename
```

## 💻 Example

```bash
file notes.txt
```

## 📤 Sample Output

```text
notes.txt: ASCII text
```

## 🌍 Real World Use

Useful when a file has no extension or you want to verify its actual type.

## 🧪 Try It Yourself

```bash
touch demo.txt
file demo.txt
```

---

# 🔥 Interview Tip

### Question

What is the difference between `rm` and `rmdir`?

### Answer

- `rm` removes files and can also remove directories using `rm -r`.
- `rmdir` removes **only empty directories**.

---

# 🌍 Real World Scenario

Suppose your project contains old log files:

```bash
find . -name "*.log"
rm old.log
```

You first locate the unwanted log file and then delete it safely.
---

# 📋 Command Summary

| Command | Purpose |
|----------|----------|
| `cp` | Copy files or directories |
| `mv` | Move or rename files |
| `rm` | Remove files |
| `find` | Search for files |
| `file` | Identify file type |

> 🧠 **Remember This**

- `cp` → Copy
- `mv` → Move or Rename
- `rm` → Delete
- `find` → Search
- `file` → Identify file type

---

# 📝 Quick Recap

Today you learned:

- ✅ Copy files using `cp`
- ✅ Move and rename files using `mv`
- ✅ Delete files using `rm`
- ✅ Search files using `find`
- ✅ Identify file types using `file`

---

# 🎯 Mini Challenge

Without looking at the notes:

1. Create a folder named `Practice`.
2. Create a file named `demo.txt`.
3. Copy it as `demo_backup.txt`.
4. Move the backup into another folder named `Backup`.
5. Search for all `.txt` files.
6. Check the file type of `demo.txt`.
7. Delete both files.

---

# ☕ Coffee Break

Congratulations! 🎉

You can now confidently manage files and directories using the Linux terminal. These are the commands you'll use throughout your Linux journey.

---

# 💡 Fun Fact

Many developers rarely use a graphical file manager—they perform most file operations directly from the terminal because it's faster and easier to automate.

---

# 🧭 What's Next?

## 🏆 Level 01 Complete!

Before moving to Level 02, we'll create:

- 📋 Level 01 Cheat Sheet
- 📚 Complete Revision Notes
- 💼 50+ Interview Questions
- 🧪 Labs Index
- 🏅 Level 01 Completion Guide

This will make Linux Quest feel like a complete beginner course rather than just a collection of notes.