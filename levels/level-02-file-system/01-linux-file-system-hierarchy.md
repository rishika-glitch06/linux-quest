# 📂 Lesson 01 — Linux File System Hierarchy

> Understanding how Linux organizes files, directories, and system resources.

---

## 🎯 What Are We Studying?

In this lesson, we will learn about the **Linux File System Hierarchy**.

Unlike Windows, where you may be familiar with drives such as `C:` and `D:`, Linux uses a single hierarchical file system that starts from the **Root Directory**, represented by `/`.

We will learn:

- What the Linux file system is
- What the Root Directory `/` means
- How Linux organizes directories
- The purpose of important directories
- How to navigate the file system
- Why understanding the file system is important

---

# 🧠 What Is a File System?

A **file system** is the way an operating system organizes and stores files and directories on a storage device.

Linux follows a hierarchical structure.

This means directories are organized like a tree.

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

The top of this hierarchy is the **Root Directory**:

```text
/
```

Everything in the Linux file system exists somewhere under `/`.

---

# 🌳 The Root Directory `/`

The `/` directory is the **top-most directory** in Linux.

It is not the same as the `/root` directory.

```text
/       → Root of the entire file system

/root   → Home directory of the root user
```

Think of `/` as the **starting point of the entire Linux file system**.

---

# 📁 Important Linux Directories

## `/bin`

Contains essential executable programs and commands used by the system.

Examples:

```text
ls
cp
mv
rm
cat
```

---

## `/boot`

Contains files required for the system to boot.

It may contain:

- Linux Kernel
- Bootloader files
- Initial RAM filesystem

---

## `/dev`

Contains special files that represent hardware devices.

Examples:

```text
/dev/sda
/dev/null
/dev/tty
```

Linux treats many devices like files.

---

## `/etc`

Contains system-wide configuration files.

Examples include configuration for:

- Networking
- Users
- Services
- System settings

Example:

```text
/etc/passwd
/etc/hosts
```

---

## `/home`

Contains the personal directories of normal users.

For example:

```text
/home/rishika
/home/user1
/home/user2
```

Your personal files, documents, downloads, and projects are generally stored inside your home directory.

---

## `/lib`

Contains essential shared libraries required by system programs and commands.

Libraries provide reusable code that programs need to function.

---

## `/media`

Used as a mount point for removable media.

For example:

- USB drives
- External storage
- CDs/DVDs

---

## `/mnt`

Traditionally used as a temporary mount point for manually mounted file systems.

For example:

```text
/mnt/backup
/mnt/external-drive
```

---

## `/opt`

Used for optional or third-party software packages.

Applications that are installed outside the standard package management structure may be placed here.

---

## `/proc`

A virtual file system that provides information about running processes and the Linux kernel.

For example:

```text
/proc/cpuinfo
/proc/meminfo
```

The files here do not behave like normal files stored on your hard drive.

---

## `/root`

The home directory of the **root user**.

Remember:

```text
/       → Root of the entire file system

/root   → Home directory of the root user
```

---

## `/run`

Stores temporary runtime information for processes and services since the system was booted.

---

## `/sbin`

Contains important system administration commands.

These commands are generally used for system management and maintenance.

---

## `/srv`

Contains data used by services provided by the system.

For example, a web server may store website-related data here.

---

## `/sys`

A virtual file system that provides information about devices, hardware, and the Linux kernel.

It is mainly used by the kernel and system software.

---

## `/tmp`

Used for temporary files.

Files stored here may be automatically deleted when the system restarts, depending on the Linux distribution and configuration.

---

## `/usr`

Contains many user-space applications, libraries, documentation, and other resources.

Common directories include:

```text
/usr/bin
/usr/lib
/usr/share
```

---

## `/var`

Contains variable data that changes frequently while the system is running.

Examples include:

- Log files
- Cache files
- Spool files

A common location is:

```text
/var/log
```

which contains system and application logs.

---

# 🗺️ Linux File System Overview

```text
                         /
                         │
       ┌─────────────────┼─────────────────┐
       │                 │                 │
      /bin              /etc             /home
       │                 │                 │
   Commands         Configuration      User Files
       
       ┌─────────────────┼─────────────────┐
       │                 │                 │
     /boot             /dev              /var
       │                 │                 │
   Boot Files         Devices            Logs

       ┌─────────────────┼─────────────────┐
       │                 │                 │
      /tmp              /usr              /root
       │                 │                 │
  Temporary Files    Applications       Root User
```

---

# 🌍 Real-World Example

Imagine your Linux computer is like a **large office building**.

```text
/          → The entire building

/home      → Employees' personal offices

/etc       → Building rules and configuration

/bin       → Tools everyone can use

/var/log   → Security and activity records

/tmp       → Temporary workspace

/root      → Administrator's private office

/boot      → The system that starts the building
```

Just like an office building has different rooms for different purposes, Linux organizes its files and resources into different directories.

This organization makes the system easier to manage and maintain.

---

# 💻 Exploring the File System

Let's explore the Linux file system using the terminal.

## Step 1 — Go to the Root Directory

```bash
cd /
```

---

## Step 2 — Check Your Location

```bash
pwd
```

Expected output:

```text
/
```

---

## Step 3 — List Root Directories

```bash
ls
```

For a detailed listing:

```bash
ls -l
```

---

## Step 4 — Explore the `/etc` Directory

```bash
cd /etc
```

Then:

```bash
pwd
```

You should see:

```text
/etc
```

---

## Step 5 — Return to Your Home Directory

```bash
cd ~
```

Or simply:

```bash
cd
```

---

# 🧪 Hands-on Practice

Try the following commands:

```bash
cd /

pwd

ls

cd /etc

pwd

cd /home

pwd

cd ~

pwd
```

### 🎯 Challenge

Without looking at the lesson:

1. Go to `/`.
2. List its contents.
3. Navigate to `/etc`.
4. Return to your home directory.
5. Confirm your current location using `pwd`.

---

# 🔍 Quick Check

Answer these questions:

### 1. What is the top-most directory in Linux?

Answer:

```text
/
```

### 2. Where are normal users' home directories stored?

Answer:

```text
/home
```

### 3. Where are system configuration files stored?

Answer:

```text
/etc
```

### 4. Where are temporary files commonly stored?

Answer:

```text
/tmp
```

### 5. What is the difference between `/` and `/root`?

Answer:

```text
/       → Root of the entire Linux file system

/root   → Home directory of the root user
```

---

# 💡 Key Takeaway

The Linux file system follows a **hierarchical tree structure** that begins at `/`.

The most important directories to remember are:

```text
/       → Root of the file system
/home   → Normal users' home directories
/root   → Root user's home directory
/etc    → System configuration
/bin    → Essential commands
/boot   → Boot-related files
/dev    → Device files
/tmp    → Temporary files
/usr    → User applications and resources
/var    → Variable data and logs
```

Understanding these directories is essential for working confidently with Linux.

---

# 💼 Interview Questions

## Q1. What is the Linux File System Hierarchy?

**Answer:**

The Linux File System Hierarchy is a standardized structure that organizes files and directories in a tree-like hierarchy starting from the Root Directory `/`.

---

## Q2. What is the Root Directory?

**Answer:**

The Root Directory `/` is the top-most directory in the Linux file system. All other files and directories exist below it.

---

## Q3. What is the purpose of `/home`?

**Answer:**

`/home` contains the personal home directories of normal users.

---

## Q4. What is stored in `/etc`?

**Answer:**

`/etc` contains system-wide configuration files used to configure the operating system and various services.

---

## Q5. What is the difference between `/` and `/root`?

**Answer:**

`/` is the root of the entire Linux file system, while `/root` is the home directory of the root user.

---

## Q6. What is the purpose of `/tmp`?

**Answer:**

`/tmp` is used to store temporary files created by users and applications.

---

## Q7. What is `/var` used for?

**Answer:**

`/var` stores variable data that changes frequently, such as logs, caches, and spool files.

---

## Q8. What is `/proc`?

**Answer:**

`/proc` is a virtual file system that provides information about running processes and the Linux kernel.

---

# 🧠 Remember This

```text
/       → Root
/home   → Users
/root   → Root User
/etc    → Configuration
/bin    → Commands
/boot   → Boot
/dev    → Devices
/tmp    → Temporary
/usr    → Applications
/var    → Variable Data
```

---

# 🎯 Lesson Complete

You now understand the basic structure of the Linux File System Hierarchy.

You learned:

- ✅ What a file system is
- ✅ What `/` represents
- ✅ Important Linux directories
- ✅ The difference between `/` and `/root`
- ✅ How to navigate the file system
- ✅ How to explore directories using terminal commands

---

# 🧭 Linux Quest Navigation

⬅️ [Back to Level 01 — Linux Basics](../level-01-linux-basics/README.md)

🏠 [Linux Quest Home](../../README.md)

➡️ **Next Lesson: Important Linux Directories**

---

> 🐧 **The Quest Continues...**

> 💡 *Learn the structure. Master the system.*