# 📂 Lesson 01 — Linux File System Hierarchy

> Understanding how Linux organizes files, directories, and system resources.

---

## 🎯 What Are We Studying?

In this lesson, we will understand the **Linux File System Hierarchy** and how Linux organizes files and directories.

Unlike Windows, where you may see drives such as `C:` and `D:`, Linux uses a single hierarchical file system that starts from the **Root Directory `/`**.

We will learn:

- What a Linux file system is
- What the Root Directory `/` means
- How Linux organizes files and directories
- The purpose of important directories
- How to navigate the Linux file system
- How to explore directories using terminal commands

---

# 🧠 What Is a File System?

A **file system** is a method used by an operating system to organize, store, and manage files and directories on a storage device.

Linux follows a **hierarchical file system structure**.

This structure looks like a tree:

```text
                         /
                         │
        ┌────────────────┼────────────────┐
        │                │                │
       /bin             /etc             /home
        │                │                │
    Commands        Configuration      User Files
                         
        ┌────────────────┼────────────────┐
        │                │                │
      /boot             /dev             /var
        │                │                │
   Boot Files         Devices            Logs

        ┌────────────────┼────────────────┐
        │                │                │
       /tmp             /usr             /root
        │                │                │
 Temporary Files   Applications       Root User
```

The top of this hierarchy is the **Root Directory**:

```text
/
```

Everything in the Linux file system exists somewhere under `/`.

---

# 🌳 Understanding the Root Directory `/`

The `/` directory is the **top-most directory** in Linux.

All other directories and files exist below it.

For example:

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

### ⚠️ Important

Do not confuse:

```text
/       → Root of the entire file system

/root   → Home directory of the root user
```

These are two completely different things.

---

# 📂 Important Directories

The Linux file system contains many directories, each serving a specific purpose.

| Directory | Purpose |
|---|---|
| `/` | Root of the entire file system |
| `/bin` | Essential commands |
| `/boot` | Boot-related files |
| `/dev` | Device files |
| `/etc` | System configuration |
| `/home` | Normal users' home directories |
| `/lib` | Essential system libraries |
| `/media` | Removable media |
| `/mnt` | Temporary mount point |
| `/opt` | Optional software |
| `/proc` | Process and kernel information |
| `/root` | Root user's home directory |
| `/run` | Runtime information |
| `/sbin` | System administration commands |
| `/srv` | Service data |
| `/sys` | Kernel and hardware information |
| `/tmp` | Temporary files |
| `/usr` | User applications and resources |
| `/var` | Variable data and logs |

---

# 🖼️ Linux File System Hierarchy Diagram

```text
                              /
                              │
       ┌──────────┬───────────┼───────────┬──────────┐
       │          │           │           │          │
     /bin       /boot       /dev        /etc       /home
       │          │           │           │          │
   Commands   Boot Files   Devices   Configuration  Users

       ┌──────────┬───────────┼───────────┬──────────┐
       │          │           │           │          │
     /lib       /media      /mnt        /opt       /proc
       │          │           │           │          │
   Libraries  Removable   Mount Point  Software   Processes

       ┌──────────┬───────────┼───────────┬──────────┐
       │          │           │           │          │
     /root      /run        /sbin       /sys       /tmp
       │          │           │           │          │
  Root User   Runtime     Admin Cmds   Hardware   Temporary

                         ┌──────────┐
                         │          │
                        /usr       /var
                         │          │
                    Applications   Logs
                    & Resources   & Data
```

### 💡 Key Idea

The Linux file system is organized like a tree.

```text
/
│
├── Directories
│     │
│     └── Subdirectories
│            │
│            └── Files
```

The Root Directory `/` is the starting point of this entire structure.

---

# 🌍 Real-World Example

Think of the Linux file system as a **large organization**.

```text
/           → Entire Organization

/home       → Employees' Personal Offices

/etc        → Organization Rules & Configuration

/bin        → Commonly Used Tools

/var/log    → Activity Records

/tmp        → Temporary Workspace

/root       → Administrator's Office

/boot       → System Startup Department
```

Just like an organization separates responsibilities into different departments, Linux separates files and resources into different directories.

This makes the system easier to manage, maintain, and troubleshoot.

---

# 💻 Exploring the File System Using Terminal

Now let's explore the Linux file system.

---

## 1️⃣ Go to the Root Directory

```bash
cd /
```

The `cd` command is used to change directories.

---

## 2️⃣ Check Your Current Location

```bash
pwd
```

Expected output:

```text
/
```

The `pwd` command means:

```text
Print Working Directory
```

It shows your current location in the file system.

---

## 3️⃣ List Files and Directories

```bash
ls
```

To get a detailed listing:

```bash
ls -l
```

The `ls` command displays the contents of a directory.

---

## 4️⃣ Navigate to `/etc`

```bash
cd /etc
```

Check your current location:

```bash
pwd
```

Expected output:

```text
/etc
```

---

## 5️⃣ Return to Your Home Directory

You can use:

```bash
cd ~
```

Or simply:

```bash
cd
```

---

# 🧪 Hands-on Practice

Try the following commands in your Linux terminal:

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
ls -l
```

```bash
cd /etc
```

```bash
pwd
```

```bash
cd /home
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

# 🎯 Mini Challenge

Try completing the following challenge without looking at the commands above.

### Challenge:

1. Go to the Root Directory `/`.
2. Check your current location.
3. List all files and directories.
4. Navigate to `/etc`.
5. Check your current location.
6. Navigate to `/home`.
7. Return to your home directory.
8. Verify your current location.

### Expected Command Flow

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

---

# 🔍 Quick Check

### Q1. What is the top-most directory in Linux?

Answer:

```text
/
```

---

### Q2. Where are normal users' home directories stored?

Answer:

```text
/home
```

---

### Q3. Where are system configuration files stored?

Answer:

```text
/etc
```

---

### Q4. What is the difference between `/` and `/root`?

Answer:

```text
/       → Root of the entire file system

/root   → Home directory of the root user
```

---

### Q5. Which command shows your current location?

Answer:

```bash
pwd
```

---

# 💡 Key Takeaways

The Linux file system follows a **hierarchical tree structure**.

The entire file system begins at:

```text
/
```

Important directories include:

```text
/       → Root of file system
/home   → Normal users
/root   → Root user's home
/etc    → Configuration
/bin    → Essential commands
/boot   → Boot files
/dev    → Devices
/tmp    → Temporary files
/usr    → Applications and resources
/var    → Variable data and logs
```

The most important concept to remember is:

> **Everything in the Linux file system starts from the Root Directory `/`.**

---

# 💼 Interview Questions

## Q1. What is the Linux File System Hierarchy?

**Answer:**

The Linux File System Hierarchy is a standardized structure that organizes files and directories in a tree-like hierarchy starting from the Root Directory `/`.

---

## Q2. What is the Root Directory in Linux?

**Answer:**

The Root Directory `/` is the top-most directory in the Linux file system.

All files and directories exist somewhere below it.

---

## Q3. What is the difference between `/` and `/root`?

**Answer:**

`/` is the root of the entire Linux file system.

`/root` is the home directory of the root user.

```text
/       → Root of the entire file system

/root   → Root user's home directory
```

---

## Q4. What is the purpose of `/home`?

**Answer:**

`/home` contains the personal home directories of normal users.

For example:

```text
/home/user1
/home/user2
```

---

## Q5. What is stored in `/etc`?

**Answer:**

`/etc` contains system-wide configuration files used to configure the operating system and various services.

---

## Q6. What is the purpose of `/var`?

**Answer:**

`/var` contains variable data that changes frequently while the system is running.

Examples include:

- Log files
- Cache files
- Spool files

---

## Q7. What is `/proc`?

**Answer:**

`/proc` is a virtual file system that provides information about running processes and the Linux kernel.

Examples:

```text
/proc/cpuinfo
/proc/meminfo
```

---

## Q8. What is `/dev`?

**Answer:**

`/dev` contains special files that represent hardware devices and other device interfaces.

Examples include:

```text
/dev/sda
/dev/null
/dev/tty
```

---

## Q9. What is the purpose of `/tmp`?

**Answer:**

`/tmp` is used to store temporary files created by users and applications.

---

## Q10. What is the purpose of `/usr`?

**Answer:**

`/usr` contains many user-space applications, libraries, documentation, and shared resources.

---

## Q11. What is the purpose of `/boot`?

**Answer:**

`/boot` contains files required to start the Linux operating system, including the Linux kernel and bootloader-related files.

---

## Q12. What is the purpose of `/bin`?

**Answer:**

`/bin` traditionally contains essential executable commands required by users and the system.

On many modern Linux distributions, `/bin` may be a symbolic link to `/usr/bin`.

---

## Q13. What is the purpose of `/sbin`?

**Answer:**

`/sbin` traditionally contains system administration commands used for system management and maintenance.

---

## Q14. Why is understanding the Linux File System Hierarchy important?

**Answer:**

Understanding the hierarchy helps users navigate Linux systems, locate configuration files, find logs, manage files, troubleshoot problems, and understand how the operating system is organized.

---

# 🧠 Interview Quick Revision

```text
/       → Root of the entire file system
/bin    → Essential commands
/boot   → Boot-related files
/dev    → Device files
/etc    → Configuration files
/home   → Normal users
/lib    → Essential libraries
/media  → Removable media
/mnt    → Temporary mount point
/opt    → Optional software
/proc   → Process information
/root   → Root user's home
/run    → Runtime information
/sbin   → System administration commands
/srv    → Service data
/sys    → Hardware and kernel information
/tmp    → Temporary files
/usr    → User applications and resources
/var    → Variable data and logs
```

---

# 🏆 Lesson Completion Checklist

- [x] Understand what a Linux file system is
- [x] Understand the Root Directory `/`
- [x] Understand the Linux File System Hierarchy
- [x] Learn important Linux directories
- [x] Explore the file system using terminal commands
- [x] Complete hands-on practice
- [x] Review key takeaways
- [x] Prepare for interview questions

---

# 🧭 Linux Quest Navigation

⬅️ [Previous Lesson — Level 01 Linux Basics](../level-01-linux-basics/README.md)

🏠 [Linux Quest Home](../../README.md)

➡️ [Next Lesson — Important Linux Directories](02-important-linux-directories.md)

---

> 🐧 **The Quest Continues...**

> 💡 *Understand the structure. Navigate the system. Master Linux.*