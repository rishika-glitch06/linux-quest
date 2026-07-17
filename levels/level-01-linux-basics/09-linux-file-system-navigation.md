# 📂 09 - Linux File System Navigation

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
🟢 09 - Linux File System Navigation (Current Lesson)
⬜ 10 - Working with Files & Directories
```

---

# 📚 In This Lesson You'll Learn

By the end of this lesson, you'll understand:

- Linux File System
- Root Directory
- Home Directory
- Absolute Path
- Relative Path
- Important Linux Directories
- File System Hierarchy Standard (FHS)

---

# 👋 Let's Start

Imagine your computer is a huge city.

Every folder is like a building.

Every file is like a room inside that building.

Linux organizes everything using one giant tree-like structure called the **File System**.

Unlike Windows, Linux doesn't have drives like **C:** or **D:**.

Everything starts from one single location:

```
/
```

This is called the **Root Directory**.

Every file, folder, application, user account, and system configuration exists somewhere under this root.

Once you understand the Linux file system, navigating Linux becomes much easier.
## 💡 Did You Know?

In Linux, everything is treated as a file—including hardware devices, disks, terminals, and even running processes.
---

# 🌳 Understanding the Linux File System

Unlike Windows, Linux does not organize files into different drives like **C:** or **D:**.

Instead, everything starts from a single directory called the **Root Directory (`/`)**.

Every folder, file, application, and device is located somewhere under this root.

Think of it like a giant family tree where every branch starts from one common root.

---

# 📂 Root Directory (`/`)

The **Root Directory** is the top-most directory in Linux.

It is represented by:

```text
/
```

Everything inside Linux begins here.

Example:

```text
/
├── home
├── etc
├── usr
├── var
├── bin
└── tmp
```

> ⚠️ Don't confuse the **Root Directory (`/`)** with the **Root User**. They are two completely different concepts.

---

# 🏠 Home Directory (`~`)

Every user gets a personal home directory.

For example:

```text
/home/rishika
```

The symbol:

```text
~
```

is a shortcut for your current user's home directory.

Example:

```bash
cd ~
```

takes you directly to your home folder.

---

# 🧭 Absolute Path

An **absolute path** always starts from the root directory (`/`).

Example:

```text
/home/rishika/Documents/notes.txt
```

No matter where you are in Linux, an absolute path always points to the same location.

---

# 📍 Relative Path

A **relative path** starts from your current directory.

Example:

```bash
cd Documents
```

If you're already inside:

```text
/home/rishika
```

then Linux understands that you want to go to:

```text
/home/rishika/Documents
```

---

# ⚖️ Absolute Path vs Relative Path

| Absolute Path | Relative Path |
|---------------|---------------|
| Starts with `/` | Starts from current location |
| Same everywhere | Depends on current directory |
| Longer | Shorter |
| More precise | More convenient |

---

# ❌ Common Beginner Mistakes

- Confusing `/` with `~`
- Thinking `~` means the root directory
- Forgetting where you are before using a relative path
- Using relative paths in scripts where absolute paths are safer

---

# 💡 Did You Know?

In Linux, almost everything is treated as a file—including hard disks, USB drives, keyboards, terminals, and even running processes.