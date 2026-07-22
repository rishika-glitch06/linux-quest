# 🌳 Linux File System Hierarchy

> A visual guide to understanding how the Linux file system is organized.

---

## 📌 Overview

The Linux file system follows a **hierarchical tree structure**.

Unlike Windows, Linux does not organize the entire system using drive letters such as `C:` or `D:`.

Instead, everything starts from a single top-level directory called the **Root Directory**:

```text
/
```

All files, directories, devices, configuration files, applications, and system resources exist somewhere under this root.

---

## 🌳 Linux File System Tree

```text
/
├── bin/
│   └── Essential user commands
│
├── boot/
│   └── Bootloader and kernel files
│
├── dev/
│   └── Device files
│
├── etc/
│   └── System-wide configuration files
│
├── home/
│   ├── user1/
│   ├── user2/
│   └── rishika/
│       ├── Documents/
│       ├── Downloads/
│       ├── Pictures/
│       └── Projects/
│
├── lib/
│   └── Essential system libraries
│
├── media/
│   └── Removable media
│
├── mnt/
│   └── Temporary mount points
│
├── opt/
│   └── Optional / third-party software
│
├── proc/
│   └── Process and kernel information
│
├── root/
│   └── Root user's home directory
│
├── run/
│   └── Runtime system information
│
├── sbin/
│   └── System administration commands
│
├── srv/
│   └── Data for system services
│
├── sys/
│   └── Kernel and hardware information
│
├── tmp/
│   └── Temporary files
│
├── usr/
│   ├── bin/
│   │   └── User commands
│   │
│   ├── lib/
│   │   └── User-space libraries
│   │
│   └── share/
│       └── Shared data and documentation
│
└── var/
    ├── log/
    │   └── System and application logs
    │
    ├── cache/
    │   └── Cached data
    │
    └── spool/
        └── Queued data
```

---

## 🧠 Understanding the Hierarchy

Think of the Linux file system as an inverted tree.

```text
                         /
                    Root Directory
                         │
        ┌────────────────┼────────────────┐
        │                │                │
      /etc             /home            /usr
        │                │                │
   Configuration      User Files      Applications
        │                │                │
        └────────────────┼────────────────┘
                         │
                       /var
                         │
                    Logs & Data
```

The Root Directory `/` is the starting point.

From `/`, the system branches into different directories, and those directories may contain additional subdirectories and files.

---

## 📂 Directory Categories

### ⚙️ System Configuration

```text
/etc
```

Contains configuration files for the system and services.

---

### 👤 User Data

```text
/home
```

Contains personal directories belonging to normal users.

Example:

```text
/home/rishika
```

---

### 💻 Applications & Commands

```text
/bin
/usr/bin
/usr
```

Contains executable programs and user-space applications.

---

### 🛠️ System Information

```text
/proc
/sys
/dev
```

These directories provide interfaces to processes, hardware, devices, and kernel information.

---

### 📝 Logs & Variable Data

```text
/var
/var/log
```

Contains data that changes during normal system operation, including logs.

---

### 🚀 System Startup

```text
/boot
```

Contains important files required during the system boot process.

---

### 🗑️ Temporary Data

```text
/tmp
```

Used for temporary files created by applications and users.

---

## 🔑 Most Important Directories

| Directory | Meaning | Main Purpose |
|---|---|---|
| `/` | Root | Top of the entire file system |
| `/bin` | Binaries | Essential commands |
| `/boot` | Boot | Startup and kernel files |
| `/dev` | Devices | Device interfaces |
| `/etc` | Etcetera | Configuration files |
| `/home` | Home | Normal user data |
| `/lib` | Libraries | Essential system libraries |
| `/media` | Media | Removable devices |
| `/mnt` | Mount | Temporary mount point |
| `/opt` | Optional | Third-party software |
| `/proc` | Processes | Process and kernel information |
| `/root` | Root Home | Root user's home directory |
| `/run` | Runtime | Runtime information |
| `/sbin` | System Binaries | Administration commands |
| `/srv` | Service | Service data |
| `/sys` | System | Hardware and kernel information |
| `/tmp` | Temporary | Temporary files |
| `/usr` | User | Applications and resources |
| `/var` | Variable | Logs and changing data |

---

## ⚠️ Important Difference

Do not confuse these two:

```text
/       → Root of the entire Linux file system

/root   → Home directory of the root user
```

Visual representation:

```text
/
├── home/
│   └── rishika/
│
├── etc/
│
├── var/
│
├── usr/
│
└── root/
    └── Root user's personal files
```

---

## 🧭 Navigation Example

A user may navigate through the hierarchy like this:

```text
/
│
└── home/
    │
    └── rishika/
        │
        └── Projects/
            │
            └── linux-quest/
```

The absolute path would be:

```text
/home/rishika/Projects/linux-quest
```

This shows how a location can be traced from the Root Directory `/`.

---

## 💻 Useful Commands

### Go to Root

```bash
cd /
```

### Check Current Location

```bash
pwd
```

### List Root Contents

```bash
ls /
```

### View Directory Details

```bash
ls -l /
```

### Explore `/etc`

```bash
ls /etc
```

### Explore `/home`

```bash
ls /home
```

### Explore `/var/log`

```bash
ls /var/log
```

---

## 🧠 Remember

```text
                    /
                    │
       ┌────────────┼────────────┐
       │            │            │
     /etc         /home         /usr
       │            │            │
  Configuration   Users      Applications

       ┌────────────┼────────────┐
       │            │            │
     /var         /tmp         /boot
       │            │            │
     Logs       Temporary     Startup
```

### The Golden Rule

> 🐧 **Everything in the Linux file system starts from the Root Directory `/`.**

---

## 🔗 Related Lesson

📖 [Lesson 01 — Linux File System Hierarchy](../../levels/level-02-file-system/01-linux-file-system-hierarchy.md)

➡️ [Lesson 02 — Important Linux Directories](../../levels/level-02-file-system/02-important-linux-directories.md)

🏠 [Back to Linux Quest](../../README.md)

---

> 🐧 **Linux Quest — Level 02**

> *Understand the structure. Navigate the system. Master Linux.*