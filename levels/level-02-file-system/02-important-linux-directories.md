# 📂 Lesson 02 — Important Linux Directories

> Understanding the purpose of the most important directories in the Linux file system.

---

## 🎯 What Are We Studying?

In the previous lesson, we learned about the **Linux File System Hierarchy** and how everything begins from the Root Directory `/`.

In this lesson, we will explore the most important directories in Linux and understand what each directory is used for.

We will learn:

- 📂 The purpose of important Linux directories
- ⚙️ Where system files are stored
- 👤 Where user files are stored
- 🛠️ Where configuration files are located
- 📝 Where logs and temporary files are stored
- 💻 How to explore these directories using terminal commands

---

# 🌳 Linux File System at a Glance

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

Each directory has a specific purpose.

Let's explore them one by one.

---

# 1️⃣ `/` — Root Directory

The `/` directory is the **top-most directory** in the Linux file system.

Everything in Linux exists under `/`.

Example:

```text
/
├── home
├── etc
├── usr
├── var
└── tmp
```

To navigate to the root directory:

```bash
cd /
```

To check your location:

```bash
pwd
```

Expected output:

```text
/
```

### 💡 Remember

```text
/ = Root of the entire Linux file system
```

---

# 2️⃣ `/bin` — Essential User Commands

`/bin` contains essential executable programs and commands that are available to users.

Examples include commands such as:

```text
ls
cp
mv
rm
cat
```

You can explore it using:

```bash
ls /bin
```

### 💡 Remember

```text
/bin = Essential commands
```

> Note: On many modern Linux distributions, `/bin` may be a symbolic link to `/usr/bin`.

---

# 3️⃣ `/boot` — Boot Files

The `/boot` directory contains files required to start the Linux operating system.

It may contain:

- Linux Kernel
- Bootloader configuration
- Initial RAM filesystem

You can view its contents using:

```bash
ls /boot
```

### 💡 Remember

```text
/boot = Files required during system startup
```

---

# 4️⃣ `/dev` — Device Files

The `/dev` directory contains special files that represent hardware devices and virtual devices.

Examples:

```text
/dev/sda
/dev/null
/dev/tty
```

Linux follows the concept:

```text
Everything is a file
```

This means many hardware devices can be accessed through file-like interfaces.

Explore it using:

```bash
ls /dev
```

### 💡 Remember

```text
/dev = Devices
```

---

# 5️⃣ `/etc` — Configuration Files

The `/etc` directory contains system-wide configuration files.

Examples:

```text
/etc/passwd
/etc/hosts
/etc/hostname
```

You can explore it using:

```bash
ls /etc
```

To view the contents of a configuration file:

```bash
cat /etc/hostname
```

### 💡 Remember

```text
/etc = System configuration
```

---

# 6️⃣ `/home` — User Home Directories

The `/home` directory contains the home directories of normal users.

Example:

```text
/home
├── rishika
├── user1
└── user2
```

To see the directories:

```bash
ls /home
```

Your home directory can be accessed using:

```bash
cd ~
```

or simply:

```bash
cd
```

### 💡 Remember

```text
/home = Personal directories of normal users
```

---

# 7️⃣ `/lib` — Essential Libraries

The `/lib` directory contains essential shared libraries required by system programs and commands.

Libraries provide reusable code that applications and system programs depend on.

Explore it using:

```bash
ls /lib
```

### 💡 Remember

```text
/lib = Essential system libraries
```

> Note: On many modern distributions, `/lib` may be a symbolic link to a directory under `/usr`.

---

# 8️⃣ `/media` — Removable Media

The `/media` directory is commonly used as a mount point for removable storage devices.

Examples:

- USB drives
- External hard drives
- CDs/DVDs

Example:

```text
/media/user/USB
```

Explore it using:

```bash
ls /media
```

### 💡 Remember

```text
/media = Removable storage
```

---

# 9️⃣ `/mnt` — Temporary Mount Point

The `/mnt` directory is traditionally used for manually mounted file systems.

For example:

```text
/mnt/backup
/mnt/external-drive
```

### 💡 Remember

```text
/mnt = Temporary or manual mount point
```

---

# 🔟 `/opt` — Optional Software

The `/opt` directory is used for optional or third-party software packages.

For example, software installed outside the standard package management system may be placed here.

Example:

```text
/opt/application
```

### 💡 Remember

```text
/opt = Optional or third-party software
```

---

# 1️⃣1️⃣ `/proc` — Process Information

`/proc` is a **virtual file system**.

It provides information about:

- Running processes
- CPU
- Memory
- Kernel

Examples:

```text
/proc/cpuinfo
/proc/meminfo
```

You can check CPU information using:

```bash
cat /proc/cpuinfo
```

Check memory information:

```bash
cat /proc/meminfo
```

### 💡 Remember

```text
/proc = Processes and kernel information
```

---

# 1️⃣2️⃣ `/root` — Root User's Home Directory

`/root` is the home directory of the **root user**.

Remember the important difference:

```text
/       = Root of the entire file system

/root   = Home directory of the root user
```

### 💡 Remember

```text
/root = Root user's home
```

---

# 1️⃣3️⃣ `/run` — Runtime Data

The `/run` directory contains temporary runtime information about the system.

It may contain information related to:

- Running services
- Processes
- System state

This data is generally created during system startup.

### 💡 Remember

```text
/run = Runtime information
```

---

# 1️⃣4️⃣ `/sbin` — System Administration Commands

The `/sbin` directory traditionally contains commands used for system administration and maintenance.

These commands are generally intended for system management.

You can explore it using:

```bash
ls /sbin
```

### 💡 Remember

```text
/sbin = System administration commands
```

> Note: On many modern Linux distributions, `/sbin` may be a symbolic link to `/usr/sbin`.

---

# 1️⃣5️⃣ `/srv` — Service Data

The `/srv` directory contains data used by services provided by the system.

For example, a server application may store service-related data here.

### 💡 Remember

```text
/srv = Data for system services
```

---

# 1️⃣6️⃣ `/sys` — System and Hardware Information

`/sys` is another virtual file system.

It provides information about:

- Hardware devices
- Kernel
- Device drivers

Explore it using:

```bash
ls /sys
```

### 💡 Remember

```text
/sys = Kernel and hardware information
```

---

# 1️⃣7️⃣ `/tmp` — Temporary Files

The `/tmp` directory is used for temporary files created by users and applications.

Example:

```bash
cd /tmp
```

You can see its contents using:

```bash
ls
```

Temporary files may be automatically deleted after a reboot depending on the Linux distribution and system configuration.

### 💡 Remember

```text
/tmp = Temporary files
```

---

# 1️⃣8️⃣ `/usr` — User Programs and Resources

The `/usr` directory contains many user-space applications, libraries, documentation, and other resources.

Common directories include:

```text
/usr/bin
/usr/lib
/usr/share
```

Examples:

```text
/usr/bin  → User commands
/usr/lib  → Libraries
/usr/share → Shared data and documentation
```

### 💡 Remember

```text
/usr = User applications and resources
```

---

# 1️⃣9️⃣ `/var` — Variable Data

The `/var` directory contains data that changes frequently while the system is running.

Examples include:

- Log files
- Cache files
- Spool files
- Application data

One of the most important directories is:

```text
/var/log
```

You can explore logs using:

```bash
ls /var/log
```

### 💡 Remember

```text
/var = Variable data
```

---

# 📊 Quick Revision Table

| Directory | Purpose |
|---|---|
| `/` | Root of the file system |
| `/bin` | Essential user commands |
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
| `/run` | Runtime system information |
| `/sbin` | System administration commands |
| `/srv` | Service data |
| `/sys` | Kernel and hardware information |
| `/tmp` | Temporary files |
| `/usr` | User applications and resources |
| `/var` | Variable data and logs |

---

# 🧪 Hands-on Practice

Try these commands in your Linux terminal:

### Task 1 — Explore Root

```bash
cd /
pwd
ls
```

### Task 2 — Explore Configuration

```bash
cd /etc
pwd
ls
```

### Task 3 — Explore User Directories

```bash
cd /home
pwd
ls
```

### Task 4 — Explore Temporary Files

```bash
cd /tmp
pwd
ls
```

### Task 5 — Explore System Information

```bash
ls /proc
ls /sys
```

### Task 6 — Explore Logs

```bash
ls /var/log
```

---

# 🎯 Mini Challenge

Without looking at the previous sections, answer:

1. Where are system configuration files stored?
2. Where are normal users' home directories stored?
3. Which directory contains temporary files?
4. Which directory contains system logs?
5. Which directory represents devices?
6. Which directory contains information about running processes?
7. What is the difference between `/` and `/root`?

---

# 💡 Key Takeaways

The Linux file system is organized into directories, and each directory has a specific responsibility.

The most important directories to remember are:

```text
/       → Root
/bin    → Essential commands
/boot   → Boot files
/dev    → Devices
/etc    → Configuration
/home   → Users
/lib    → Libraries
/media  → Removable media
/mnt    → Mount point
/opt    → Optional software
/proc   → Processes
/root   → Root user's home
/run    → Runtime data
/sbin   → System administration
/srv    → Service data
/sys    → System and hardware
/tmp    → Temporary files
/usr    → User programs
/var    → Variable data and logs
```

Understanding these directories makes it easier to navigate Linux systems and troubleshoot problems.

---

# 💼 Interview Questions

## Q1. What is the purpose of `/etc`?

**Answer:**

`/etc` contains system-wide configuration files used to configure the operating system and services.

---

## Q2. What is the difference between `/` and `/root`?

**Answer:**

`/` is the root directory of the entire Linux file system, while `/root` is the home directory of the root user.

---

## Q3. What is stored in `/home`?

**Answer:**

`/home` contains the personal home directories of normal users.

---

## Q4. What is `/var/log` used for?

**Answer:**

`/var/log` contains system and application log files that record events and activities.

---

## Q5. What is `/proc`?

**Answer:**

`/proc` is a virtual file system that provides information about running processes and the Linux kernel.

---

## Q6. What is the purpose of `/tmp`?

**Answer:**

`/tmp` is used to store temporary files created by users and applications.

---

## Q7. What is the difference between `/media` and `/mnt`?

**Answer:**

`/media` is commonly used for automatically mounted removable media such as USB drives, while `/mnt` is traditionally used as a temporary mount point for manually mounted file systems.

---

## Q8. What is `/usr`?

**Answer:**

`/usr` contains many user-space programs, libraries, documentation, and shared resources.

---

## Q9. What is `/dev`?

**Answer:**

`/dev` contains special files that represent hardware devices and other device interfaces.

---

## Q10. What is the purpose of `/boot`?

**Answer:**

`/boot` contains files required for the Linux system to start, including the kernel and bootloader-related files.

---

# 🧠 Remember This

```text
Configuration  → /etc
Users          → /home
Root User      → /root
Commands       → /bin
System Admin   → /sbin
Devices        → /dev
Boot           → /boot
Temporary      → /tmp
Logs           → /var/log
Processes      → /proc
Hardware       → /sys
Applications   → /usr
```

---

# 🎯 Lesson Complete

You now understand the purpose of the major directories in the Linux file system.

You learned:

- ✅ The purpose of important Linux directories
- ✅ Where user files are stored
- ✅ Where configuration files are stored
- ✅ Where logs and temporary files are located
- ✅ How to explore directories using terminal commands
- ✅ The difference between `/`, `/root`, `/home`, and other important directories

---

# 🧭 Linux Quest Navigation

⬅️ [Previous Lesson — Linux File System Hierarchy](01-linux-file-system-hierarchy.md)

🏠 [Linux Quest Home](../../README.md)

➡️ [Next Lesson — Absolute & Relative Paths](03-absolute-and-relative-paths.md)

---

> 🐧 **The Quest Continues...**

> 💡 *Learn the structure. Understand the system. Master Linux.*