# 📁 Linux File & Directory Management

> A visual guide to creating, copying, moving, renaming, and deleting files and directories in Linux.

---

# 🌳 File Management Overview

```text
                Linux File & Directory Management
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
          ▼                   ▼                   ▼
       CREATE              MODIFY             DELETE
          │                   │                   │
     ┌────┴────┐         ┌────┴────┐       ┌────┴────┐
     │         │         │         │       │         │
     ▼         ▼         ▼         ▼       ▼         ▼
  touch     mkdir       cp        mv      rm       rmdir
  File      Directory   Copy    Move    File    Empty Dir
                              │
                              ▼
                           Rename
```

---

# 1. 📄 Create a File

Use:

```bash
touch notes.txt
```

### Flow

```text
touch notes.txt
       │
       ▼
  notes.txt created
       │
       ▼
      ls
       │
       ▼
  notes.txt
```

---

# 2. 📁 Create a Directory

Use:

```bash
mkdir Projects
```

### Flow

```text
mkdir Projects
       │
       ▼
  Projects/
       │
       ▼
   Directory
   Created
```

---

# 3. 📂 Create Nested Directories

Use:

```bash
mkdir -p Projects/Linux/Lesson04
```

### Structure

```text
Projects/
    │
    └── Linux/
          │
          └── Lesson04/
```

The `-p` option creates parent directories automatically.

---

# 4. 📋 Copy a File

Use:

```bash
cp notes.txt backup.txt
```

### Flow

```text
             cp
             │
             ▼
notes.txt ──────────► backup.txt
   │                       │
   └──── Original ─────────┘
        remains
```

Result:

```text
notes.txt
backup.txt
```

The original file remains unchanged.

---

# 5. 📁 Copy a Directory

Use:

```bash
cp -r Projects Projects_Backup
```

### Flow

```text
Projects/
    │
    │ cp -r
    ▼
Projects_Backup/
```

The `-r` option means recursive.

It allows copying directories and their contents.

---

# 6. 🚚 Move a File

Use:

```bash
mv notes.txt Projects/
```

### Before

```text
Current Directory
│
├── notes.txt
└── Projects/
```

### Command

```bash
mv notes.txt Projects/
```

### After

```text
Current Directory
│
└── Projects/
      │
      └── notes.txt
```

The file is moved from one location to another.

---

# 7. ✏️ Rename a File

The `mv` command can also rename files.

Use:

```bash
mv notes.txt linux_notes.txt
```

### Flow

```text
notes.txt
    │
    │ mv
    ▼
linux_notes.txt
```

No new copy is created.

The original name changes.

---

# 8. 🗑️ Delete a File

Use:

```bash
rm notes.txt
```

### Flow

```text
notes.txt
    │
    │ rm
    ▼
  Deleted
```

⚠️ Be careful because deleted files may not be recoverable using normal Linux commands.

---

# 9. 🗑️ Remove an Empty Directory

Use:

```bash
rmdir EmptyFolder
```

### Flow

```text
EmptyFolder/
      │
      │ rmdir
      ▼
   Deleted
```

`rmdir` works only when the directory is empty.

---

# 10. 🗑️ Remove a Directory with Contents

Use:

```bash
rm -r Projects
```

### Flow

```text
Projects/
    │
    ├── file1.txt
    ├── file2.txt
    └── Linux/
          │
          └── lesson.md
          
              │
              │ rm -r
              ▼
          Everything
            Deleted
```

The `-r` option means recursive deletion.

---

# 11. ⚠️ Force Delete

Use:

```bash
rm -rf Projects
```

### Meaning

```text
rm
│
└── Remove

-r
│
└── Recursive

-f
│
└── Force
```

### ⚠️ WARNING

```text
rm -rf
   │
   ▼
Permanent Deletion
```

Use this command carefully.

Always verify the path before running it.

---

# 12. 📖 View File Contents

Create content:

```bash
echo "Hello Linux Quest" > notes.txt
```

View content:

```bash
cat notes.txt
```

### Flow

```text
echo
  │
  ▼
"Hello Linux Quest"
  │
  ▼
notes.txt
  │
  │ cat
  ▼
Terminal Output
```

---

# 13. 🔍 View Large Files

Use:

```bash
less notes.txt
```

or:

```bash
more notes.txt
```

### Flow

```text
Large File
    │
    ▼
 less / more
    │
    ▼
Read Page by Page
```

---

# 14. ⭐ Wildcards

Wildcards allow you to work with multiple files.

### `*` — Matches Multiple Characters

```bash
ls *.txt
```

Example:

```text
notes.txt
backup.txt
linux.txt
```

All `.txt` files are selected.

---

### `?` — Matches One Character

Example:

```bash
ls file?.txt
```

Can match:

```text
file1.txt
file2.txt
fileA.txt
```

---

# 15. 🧭 Complete File Management Flow

```text
                    FILE / DIRECTORY
                           │
                           ▼
                     What do you want?
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       CREATE           MODIFY           DELETE
          │                │                │
      ┌───┴───┐        ┌───┴───┐       ┌───┴───┐
      │       │        │       │       │       │
      ▼       ▼        ▼       ▼       ▼       ▼
    touch   mkdir      cp      mv      rm    rmdir
      │       │        │       │       │       │
      ▼       ▼        ▼       ▼       ▼       ▼
    File    Folder    Copy   Move    File    Empty
                                    Directory
                                       │
                                       ▼
                                     rm -r
```

---

# 16. 📊 Command Decision Map

```text
Need to create a file?
        │
        └──► touch


Need to create a directory?
        │
        └──► mkdir


Need to create nested directories?
        │
        └──► mkdir -p


Need to copy a file?
        │
        └──► cp


Need to copy a directory?
        │
        └──► cp -r


Need to move a file?
        │
        └──► mv


Need to rename a file?
        │
        └──► mv


Need to delete a file?
        │
        └──► rm


Need to delete an empty directory?
        │
        └──► rmdir


Need to delete a directory with contents?
        │
        └──► rm -r
```

---

# 17. 🧠 Quick Memory Map

```text
touch
  ↓
CREATE FILE

mkdir
  ↓
CREATE DIRECTORY

cp
  ↓
COPY

mv
  ↓
MOVE / RENAME

rm
  ↓
DELETE FILE

rmdir
  ↓
DELETE EMPTY DIRECTORY

rm -r
  ↓
DELETE DIRECTORY + CONTENTS

cat
  ↓
READ FILE

less / more
  ↓
READ LARGE FILES
```

---

# 18. 📊 Command Summary

| Command | Purpose |
|---|---|
| `touch` | Create an empty file |
| `mkdir` | Create a directory |
| `mkdir -p` | Create nested directories |
| `cp` | Copy a file |
| `cp -r` | Copy a directory |
| `mv` | Move a file or directory |
| `mv` | Rename a file or directory |
| `rm` | Delete a file |
| `rmdir` | Delete an empty directory |
| `rm -r` | Delete a directory recursively |
| `rm -rf` | Force recursive deletion |
| `cat` | Display file contents |
| `less` | View file contents page by page |
| `more` | View file contents page by page |

---

# 🎯 Key Takeaway

```text
CREATE
  │
  ├── touch → File
  └── mkdir → Directory

COPY
  │
  ├── cp → File
  └── cp -r → Directory

MOVE / RENAME
  │
  └── mv

DELETE
  │
  ├── rm → File
  ├── rmdir → Empty Directory
  └── rm -r → Directory + Contents
```

---

## 🔗 Related Resources

📖 [Lesson 04 — File & Directory Management](../../levels/level-02-file-system/04-file-and-directory-management.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [Linux File & Directory Management Lab](../../labs/04-file-and-directory-management-lab.md)

🏠 [Back to Linux Quest](../../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 04**

> *Create. Copy. Move. Manage.*