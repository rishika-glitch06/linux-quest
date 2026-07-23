# 🐧 Lesson 03 — Linux File Paths & Navigation

> Learn how Linux identifies file locations and how to move efficiently through the file system using absolute and relative paths.

---

## 🎯 Learning Objectives

By the end of this lesson, you will understand:

- What is a Linux file path?
- What is an absolute path?
- What is a relative path?
- Difference between absolute and relative paths
- Current working directory
- Parent directory
- Home directory
- Root directory
- Special path symbols
- How to navigate using `cd`
- How to check your current location using `pwd`
- How to list directory contents using `ls`

---

# 1. 📍 What is a File Path?

A file path describes the location of a file or directory inside the Linux file system.

Example:

```text
/home/rishika/Documents/project
```

This path tells Linux where the `project` directory is located.

The path can be:

- Absolute
- Relative

---

# 2. 🌳 Absolute Path

An absolute path describes the complete location of a file or directory starting from the Root Directory `/`.

Example:

```text
/home/rishika/Documents/project
```

The path starts with:

```text
/
```

Therefore, it is an absolute path.

### Example

```bash
cd /home/rishika/Documents
```

This command directly navigates to the specified location.

---

## 🧠 Remember

> An absolute path always starts from `/`.

Example:

```text
/home/rishika/Documents
/var/log
/etc
/usr/bin
```

---

# 3. 📂 Relative Path

A relative path describes the location of a file or directory relative to the current working directory.

It does not start from `/`.

Example:

Suppose your current location is:

```text
/home/rishika
```

You can navigate to Documents using:

```bash
cd Documents
```

Here:

```text
Documents
```

is a relative path.

---

## 🧠 Remember

> A relative path depends on your current location.

---

# 4. ⚖️ Absolute Path vs Relative Path

| Feature | Absolute Path | Relative Path |
|---|---|---|
| Starts from `/` | Yes | No |
| Depends on current directory | No | Yes |
| Complete location | Yes | No |
| Example | `/home/rishika/Documents` | `Documents` |

### Example

If you are currently in:

```text
/home/rishika
```

Both commands can take you to Documents:

```bash
cd /home/rishika/Documents
```

Absolute path.

```bash
cd Documents
```

Relative path.

---

# 5. 📌 Current Working Directory

The current working directory is the directory where you are currently located.

Use:

```bash
pwd
```

`pwd` stands for:

```text
Print Working Directory
```

Example:

```bash
pwd
```

Output:

```text
/home/rishika
```

This means your current working directory is:

```text
/home/rishika
```

---

# 6. 🏠 Home Directory

Every normal Linux user has a home directory.

For example:

```text
/home/rishika
```

You can navigate to your home directory using:

```bash
cd ~
```

or simply:

```bash
cd
```

---

## 🧠 The `~` Symbol

The tilde:

```text
~
```

represents the current user's home directory.

Example:

```bash
cd ~
```

If your username is `rishika`, this is equivalent to:

```bash
cd /home/rishika
```

---

# 7. 🌳 Root Directory

The Root Directory is represented by:

```text
/
```

It is the starting point of the entire Linux file system.

Navigate to Root:

```bash
cd /
```

Check your location:

```bash
pwd
```

Output:

```text
/
```

---

# 8. ⬆️ Parent Directory

The special path:

```text
..
```

represents the parent directory.

Suppose you are here:

```text
/home/rishika/Documents
```

Run:

```bash
cd ..
```

You will move to:

```text
/home/rishika
```

---

# 9. 📍 Current Directory

The special symbol:

```text
.
```

represents the current directory.

For example:

```bash
ls .
```

This lists the contents of the current directory.

---

# 10. 🔙 Go Back to Previous Directory

The command:

```bash
cd -
```

takes you back to the previous working directory.

Example:

```bash
cd /etc
cd /var
cd -
```

You will return to:

```text
/etc
```

---

# 11. 🧭 The `cd` Command

The `cd` command is used to change directories.

Syntax:

```bash
cd <directory>
```

Example:

```bash
cd Documents
```

Using an absolute path:

```bash
cd /var/log
```

Go to Root:

```bash
cd /
```

Go to Home:

```bash
cd ~
```

Go to Parent:

```bash
cd ..
```

---

# 12. 📋 The `ls` Command

The `ls` command lists the contents of a directory.

Basic usage:

```bash
ls
```

Detailed listing:

```bash
ls -l
```

Show hidden files:

```bash
ls -a
```

Detailed listing with hidden files:

```bash
ls -la
```

List a specific directory:

```bash
ls /etc
```

---

# 13. 🔍 Hidden Files

Linux allows files and directories to be hidden.

A hidden file starts with:

```text
.
```

Example:

```text
.bashrc
.profile
.gitconfig
```

To see hidden files:

```bash
ls -a
```

---

# 14. 🛣️ Path Navigation Example

Suppose the file system looks like this:

```text
/
└── home
    └── rishika
        ├── Documents
        │   └── Linux
        ├── Downloads
        └── Projects
```

Starting from:

```text
/home/rishika
```

Navigate to Linux using a relative path:

```bash
cd Documents/Linux
```

Using an absolute path:

```bash
cd /home/rishika/Documents/Linux
```

Both commands reach the same location.

---

# 15. 🔄 Navigation Practice

Start from your home directory:

```bash
cd ~
```

Check location:

```bash
pwd
```

Go to Root:

```bash
cd /
```

Check:

```bash
pwd
```

Go to `/etc`:

```bash
cd /etc
```

Check:

```bash
pwd
```

Go back to Root:

```bash
cd /
```

Go to `/var/log`:

```bash
cd /var/log
```

Move one level up:

```bash
cd ..
```

You should now be in:

```text
/var
```

---

# 16. 🧠 Important Path Symbols

| Symbol | Meaning |
|---|---|
| `/` | Root directory |
| `~` | Current user's home directory |
| `.` | Current directory |
| `..` | Parent directory |
| `-` | Previous working directory |

---

# 17. 💻 Essential Navigation Commands

```bash
# Show current location
pwd

# List files
ls

# Detailed listing
ls -l

# Show hidden files
ls -a

# Change directory
cd <directory>

# Go to root
cd /

# Go to home
cd ~

# Go to parent directory
cd ..

# Go to previous directory
cd -
```

---

# 🧩 Quick Practice

Try these commands one by one:

```bash
pwd
```

```bash
ls
```

```bash
cd /
```

```bash
pwd
```

```bash
ls
```

```bash
cd /etc
```

```bash
pwd
```

```bash
cd ..
```

```bash
pwd
```

```bash
cd ~
```

```bash
pwd
```

---

# 🎯 Key Takeaways

- A file path identifies the location of a file or directory.
- Absolute paths start from `/`.
- Relative paths depend on the current working directory.
- `pwd` shows your current location.
- `cd` changes your location.
- `cd ~` takes you to your home directory.
- `cd ..` moves to the parent directory.
- `cd -` returns to the previous directory.
- `.` represents the current directory.
- `ls` lists directory contents.
- `ls -a` shows hidden files.

---

# 🏆 Lesson Complete

You now understand how Linux paths work and how to navigate through the Linux file system using absolute paths, relative paths, and essential navigation commands.

> 🐧 **Linux Quest — Level 02, Lesson 03 Complete**

---

## 🔗 Navigation

⬅️ [Previous Lesson — Important Linux Directories](./02-important-linux-directories.md)

➡️ [Next Lesson — Coming Soon](#)

🖼️ [Linux File System Hierarchy Diagram](../../assets/diagrams/linux-file-system-hierarchy.md)

🖼️ [Important Linux Directories Diagram](../../assets/diagrams/important-linux-directories.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [Linux File System Lab](../../labs/01-linux-file-system-lab.md)

🧪 [Important Linux Directories Lab](../../labs/02-important-linux-directories-lab.md)

🏠 [Back to Linux Quest](../../README.md)