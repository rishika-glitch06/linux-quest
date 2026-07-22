# 📂 Important Linux Directories

> A visual guide to the purpose and role of important directories in the Linux file system.

---

## 🌳 Linux Directory Overview

```text
/
│
├── /bin      → Essential user commands
│
├── /boot     → Boot and kernel files
│
├── /dev      → Device files
│
├── /etc      → System configuration files
│
├── /home     → Normal users' home directories
│
├── /lib      → Essential shared libraries
│
├── /media    → Removable media mount points
│
├── /mnt      → Temporary mount points
│
├── /opt      → Optional / third-party software
│
├── /proc     → Process and kernel information
│
├── /root     → Root user's home directory
│
├── /run      → Runtime system information
│
├── /sbin     → System administration commands
│
├── /srv      → Data for system services
│
├── /sys      → Hardware and kernel information
│
├── /tmp      → Temporary files
│
├── /usr      → User applications and resources
│
└── /var      → Variable data and logs
```

---

## ⚙️ Configuration

```text
/etc
```

### Purpose

Stores system-wide configuration files.

```text
/etc
├── passwd
├── hosts
├── hostname
└── ssh/
```

### Remember

> `/etc` = **System Configuration**

---

## 👤 User Home Directories

```text
/home
```

### Purpose

Stores personal directories of normal users.

```text
/home
├── rishika/
│   ├── Documents/
│   ├── Downloads/
│   ├── Pictures/
│   └── Projects/
│
├── user1/
└── user2/
```

### Remember

> `/home` = **Normal Users' Personal Space**

---

## 👑 Root User's Home

```text
/root
```

### Purpose

The home directory of the root user.

```text
/
└── root/
    ├── Documents/
    ├── Downloads/
    └── configuration files
```

### Important

```text
/      → Root of the entire file system

/root  → Home directory of the root user
```

---

## 💻 Essential Commands

```text
/bin
```

Contains essential executable commands.

Examples:

```text
ls
cp
mv
cat
```

### Remember

> `/bin` = **Essential User Commands**

---

## 🛠️ System Administration Commands

```text
/sbin
```

Traditionally contains commands used for system administration.

Examples may include commands related to:

- Disk management
- Networking
- System maintenance

### Remember

> `/sbin` = **System Administration**

---

## 🚀 Boot Files

```text
/boot
```

Contains files required during system startup.

```text
/boot
├── Linux Kernel
├── Bootloader files
└── Initial RAM filesystem
```

### Remember

> `/boot` = **System Startup**

---

## 🔌 Device Files

```text
/dev
```

Contains special files representing devices.

```text
/dev
├── sda
├── tty
├── null
└── random
```

### Remember

> `/dev` = **Devices**

---

## 📚 Libraries

```text
/lib
```

Contains essential shared libraries required by system programs.

### Remember

> `/lib` = **System Libraries**

---

## 💾 Removable Media

```text
/media
```

Commonly used for automatically mounted removable devices.

Examples:

```text
/media
└── rishika/
    └── USB_DRIVE/
```

### Remember

> `/media` = **Removable Media**

---

## 📌 Temporary Mount Point

```text
/mnt
```

Traditionally used as a temporary mount point for manually mounted file systems.

Example:

```text
/mnt
└── external-drive/
```

### Remember

> `/mnt` = **Temporary Mount**

---

## 📦 Optional Software

```text
/opt
```

Used for optional or third-party software.

Example:

```text
/opt
└── application/
```

### Remember

> `/opt` = **Optional Software**

---

## 🔬 Process Information

```text
/proc
```

A virtual file system that provides information about:

- Running processes
- CPU
- Memory
- Kernel

Example:

```text
/proc
├── cpuinfo
├── meminfo
└── <process-id>/
```

### Remember

> `/proc` = **Processes and Kernel Information**

---

## ⚡ Runtime Information

```text
/run
```

Contains temporary runtime information created while the system is running.

```text
/run
├── systemd/
├── user/
└── services/
```

### Remember

> `/run` = **Runtime Information**

---

## 🌐 Service Data

```text
/srv
```

Contains data used by services provided by the system.

Example:

```text
/srv
└── website/
    └── web-data
```

### Remember

> `/srv` = **Service Data**

---

## 🧠 Kernel and Hardware Information

```text
/sys
```

A virtual file system that provides information about:

- Hardware
- Devices
- Drivers
- Kernel

### Remember

> `/sys` = **System and Hardware Information**

---

## 🗑️ Temporary Files

```text
/tmp
```

Used for temporary files created by applications and users.

```text
/tmp
├── temporary-file-1
├── temporary-file-2
└── application-temp-data
```

### Remember

> `/tmp` = **Temporary Files**

---

## 🧰 User Applications and Resources

```text
/usr
```

Contains user-space applications, libraries, documentation, and shared resources.

```text
/usr
├── bin/
├── lib/
├── sbin/
└── share/
```

### Remember

> `/usr` = **User Applications and Resources**

---

## 📝 Variable Data

```text
/var
```

Contains data that changes frequently during system operation.

```text
/var
├── log/
│   └── System and application logs
│
├── cache/
│   └── Cached data
│
└── spool/
    └── Queued data
```

### Remember

> `/var` = **Variable Data**

---

# 🧠 Quick Memory Map

```text
                 LINUX FILE SYSTEM
                         │
        ┌────────────────┼────────────────┐
        │                │                │
    CONFIGURATION      USERS            SYSTEM
        │                │                │
       /etc            /home            /boot
                                          │
                                          ├── /bin
                                          ├── /sbin
                                          └── /lib

        ┌────────────────┼────────────────┐
        │                │                │
     DEVICES          PROCESSES          DATA
        │                │                │
       /dev            /proc             /var
        │                │                │
       /sys             /run             /tmp
```

---

# 🎯 Directory Cheat Sheet

| Directory | Purpose | Memory Trick |
|---|---|---|
| `/` | Root of entire file system | Everything starts here |
| `/bin` | Essential commands | Binaries |
| `/boot` | Boot files | Startup |
| `/dev` | Device files | Devices |
| `/etc` | Configuration | Edit/Configuration |
| `/home` | Normal user data | Home |
| `/lib` | Essential libraries | Libraries |
| `/media` | Removable media | Media |
| `/mnt` | Temporary mounts | Mount |
| `/opt` | Optional software | Optional |
| `/proc` | Process information | Processes |
| `/root` | Root user's home | Root user |
| `/run` | Runtime information | Running system |
| `/sbin` | System commands | System binaries |
| `/srv` | Service data | Services |
| `/sys` | Hardware/kernel information | System |
| `/tmp` | Temporary files | Temporary |
| `/usr` | User applications | User |
| `/var` | Variable data/logs | Variable |

---

## 🧠 Golden Memory Trick

```text
/etc   → Configuration
/home  → Users
/root  → Root User
/bin   → Commands
/boot  → Startup
/dev   → Devices
/proc  → Processes
/sys   → System Hardware
/tmp   → Temporary
/usr   → User Applications
/var   → Variable Data
```

---

## 🔗 Related Resources

📖 [Level 02 — Linux File System](../../levels/level-02-file-system/README.md)

📖 [Lesson 01 — Linux File System Hierarchy](../../levels/level-02-file-system/01-linux-file-system-hierarchy.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🏠 [Back to Linux Quest](../../README.md)

---

> 🐧 **Linux Quest — Level 02**

> *Understand every directory. Navigate Linux with confidence.*