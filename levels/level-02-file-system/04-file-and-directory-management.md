# 🐧 Lesson 04 — File & Directory Management

> Learn how to create, copy, move, rename, view, and delete files and directories using essential Linux commands.

---

## 🎯 Learning Objectives

By the end of this lesson, you will understand:

- How to create files
- How to create directories
- How to create nested directories
- How to copy files
- How to copy directories
- How to move files and directories
- How to rename files and directories
- How to delete files
- How to delete empty directories
- How to delete directories containing files
- How to view file contents
- How to use wildcards
- Safe file management practices

---

# 1. 📄 Creating Files

The `touch` command is used to create a new empty file.

### Syntax

```bash
touch filename
```

### Example

```bash
touch notes.txt
```

Check the file:

```bash
ls
```

You should see:

```text
notes.txt
```

---

# 2. 📁 Creating Directories

The `mkdir` command is used to create a new directory.

### Syntax

```bash
mkdir directory_name
```

### Example

```bash
mkdir Projects
```

Check:

```bash
ls
```

You should see:

```text
Projects
```

---

# 3. 📂 Creating Nested Directories

The `mkdir -p` command allows you to create multiple directories and parent directories at once.

### Example

```bash
mkdir -p Projects/Linux/Lesson04
```

This creates:

```text
Projects/
└── Linux/
    └── Lesson04/
```

The `-p` option creates missing parent directories automatically.

---

# 4. 📋 Copying Files

The `cp` command is used to copy files.

### Syntax

```bash
cp source destination
```

### Example

```bash
cp notes.txt backup.txt
```

Now you have:

```text
notes.txt
backup.txt
```

The original `notes.txt` remains unchanged.

---

# 5. 📁 Copying Directories

To copy a directory and all its contents, use `cp -r`.

### Example

```bash
cp -r Projects Projects_Backup
```

The `-r` option means **recursive**.

The result is:

```text
Projects/
Projects_Backup/
```

Both directories contain the copied content.

---

# 6. 🚚 Moving Files

The `mv` command is used to move files or directories.

### Example

```bash
mv notes.txt Projects/
```

Before:

```text
.
├── notes.txt
└── Projects/
```

After:

```text
.
└── Projects/
    └── notes.txt
```

The file is moved from the current directory into `Projects`.

---

# 7. ✏️ Renaming Files

The `mv` command can also be used to rename files.

### Example

```bash
mv notes.txt linux_notes.txt
```

The file:

```text
notes.txt
```

becomes:

```text
linux_notes.txt
```

No separate copy is created.

---

# 8. 📁 Renaming Directories

The same `mv` command can rename directories.

### Example

```bash
mv Projects Projects_Backup
```

The directory name changes from:

```text
Projects
```

to:

```text
Projects_Backup
```

---

# 9. 🗑️ Removing Files

The `rm` command is used to delete files.

### Example

```bash
rm notes.txt
```

The file is removed from the directory.

⚠️ Be careful because files deleted using `rm` are generally not moved to a recycle bin.

---

# 10. 🗑️ Removing Empty Directories

The `rmdir` command removes an empty directory.

### Example

```bash
rmdir EmptyFolder
```

The directory must be empty.

If the directory contains files, `rmdir` will fail.

---

# 11. 🗑️ Removing Directories with Contents

To remove a directory and everything inside it, use:

```bash
rm -r Projects
```

The `-r` option means recursive.

This removes:

```text
Projects/
├── file1.txt
├── file2.txt
└── Linux/
    └── lesson.md
```

and all its contents.

---

# 12. ⚠️ Force Recursive Delete

The command:

```bash
rm -rf Projects
```

means:

```text
rm  → Remove
-r  → Recursive
-f  → Force
```

It forcefully removes the directory and its contents.

### ⚠️ IMPORTANT WARNING

Use `rm -rf` extremely carefully.

Always check the path before running it:

```bash
pwd
```

and:

```bash
ls
```

Never blindly run:

```bash
rm -rf
```

on an unknown path.

---

# 13. 📖 Viewing File Contents

The `cat` command displays the contents of a file.

First create a file:

```bash
echo "Hello Linux Quest" > notes.txt
```

Now display its content:

```bash
cat notes.txt
```

Output:

```text
Hello Linux Quest
```

---

# 14. 📜 Viewing Large Files

For large files, you can use:

```bash
less filename.txt
```

or:

```bash
more filename.txt
```

Example:

```bash
less notes.txt
```

Press:

```text
q
```

to exit `less`.

---

# 15. ⭐ Wildcards

Wildcards allow you to work with multiple files.

## The `*` Wildcard

The `*` wildcard matches zero or more characters.

Example:

```bash
ls *.txt
```

This can match:

```text
notes.txt
backup.txt
linux.txt
```

You can also use:

```bash
rm *.txt
```

⚠️ Be careful. This deletes all matching `.txt` files in the current directory.

---

## The `?` Wildcard

The `?` wildcard matches exactly one character.

Example:

```bash
ls file?.txt
```

This may match:

```text
file1.txt
file2.txt
fileA.txt
```

---

# 16. 🧭 File Management Workflow

A typical file management workflow may look like this:

```text
Create
  │
  ▼
touch notes.txt
  │
  ▼
View
  │
  ▼
cat notes.txt
  │
  ▼
Copy
  │
  ▼
cp notes.txt backup.txt
  │
  ▼
Move / Rename
  │
  ▼
mv backup.txt Projects/
  │
  ▼
Delete
  │
  ▼
rm backup.txt
```

---

# 17. 📊 Command Summary

| Command | Purpose |
|---|---|
| `touch` | Create an empty file |
| `mkdir` | Create a directory |
| `mkdir -p` | Create nested directories |
| `cp` | Copy a file |
| `cp -r` | Copy a directory recursively |
| `mv` | Move a file or directory |
| `mv` | Rename a file or directory |
| `rm` | Delete a file |
| `rmdir` | Delete an empty directory |
| `rm -r` | Delete a directory recursively |
| `rm -rf` | Force recursive deletion |
| `cat` | Display file contents |
| `less` | View files page by page |
| `more` | View files page by page |

---

# 18. 🧠 Important Differences

## `cp` vs `mv`

```text
cp
│
└── Creates a copy
    Original remains

mv
│
└── Moves or renames
    Original location/name changes
```

---

## `rmdir` vs `rm -r`

```text
rmdir
│
└── Removes empty directories only

rm -r
│
└── Removes directories
    and their contents
```

---

## `rm -r` vs `rm -rf`

```text
rm -r
│
└── Recursive deletion

rm -rf
│
├── Recursive
└── Force
```

`rm -rf` should be used with extreme caution.

---

# 19. 💻 Practice

Run the following commands one by one:

### Create a practice directory

```bash
mkdir LinuxPractice
```

### Enter the directory

```bash
cd LinuxPractice
```

### Create a file

```bash
touch file1.txt
```

### Add content

```bash
echo "Linux File Management" > file1.txt
```

### View content

```bash
cat file1.txt
```

### Create a copy

```bash
cp file1.txt file2.txt
```

### Rename the copy

```bash
mv file2.txt file3.txt
```

### Create a directory

```bash
mkdir Archive
```

### Move the file

```bash
mv file3.txt Archive/
```

### Check the directory

```bash
ls
```

### Check Archive

```bash
ls Archive
```

---

# 🎯 Key Takeaways

- `touch` creates files.
- `mkdir` creates directories.
- `mkdir -p` creates nested directories.
- `cp` copies files.
- `cp -r` copies directories.
- `mv` moves files and directories.
- `mv` can also rename files and directories.
- `rm` deletes files.
- `rmdir` removes empty directories.
- `rm -r` removes directories recursively.
- `rm -rf` forcefully removes directories recursively.
- `cat` displays file contents.
- `less` and `more` help view files page by page.
- `*` matches multiple characters.
- `?` matches one character.
- Always verify paths before using destructive commands.

---

# 🏆 Lesson Complete

You now understand the essential Linux commands used to manage files and directories.

You can now:

```text
Create
   ↓
Copy
   ↓
Move
   ↓
Rename
   ↓
View
   ↓
Delete
```

> 🐧 **Linux Quest — Level 02, Lesson 04 Complete**

> *Create. Copy. Move. Manage.*

---

## 🔗 Navigation

⬅️ [Previous Lesson — Linux File Paths & Navigation](./03-linux-file-paths-and-navigation.md)

➡️ [Next Lesson — Coming Soon](#)

🖼️ [File & Directory Management Diagram](../../assets/diagrams/file-and-directory-management.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [File & Directory Management Lab](../../labs/04-file-and-directory-management-lab.md)

🏠 [Back to Linux Quest](../../README.md)