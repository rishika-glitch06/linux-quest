# 💼 Linux File System — Interview Preparation

> Complete interview preparation guide for Level 02 — Linux File System.

---

# 📚 Topics Covered

This interview guide covers:

- Linux File System Hierarchy
- Root Directory `/`
- Important Linux Directories
- File System Navigation
- Virtual File Systems
- Configuration Files
- User Directories
- System Files
- Logs and Temporary Files
- Common Linux File System Commands

---

# 🟢 Beginner Level

## Q1. What is a file system?

**Answer:**

A file system is a method used by an operating system to organize, store, manage, and access files and directories on a storage device.

Linux uses a hierarchical file system structure.

---

## Q2. What is the Linux File System Hierarchy?

**Answer:**

The Linux File System Hierarchy is a standardized structure that organizes files and directories in a tree-like structure.

The entire hierarchy starts from the Root Directory:

```text
/
```

All other directories and files exist somewhere below the Root Directory.

---

## Q3. What is the Root Directory `/`?

**Answer:**

The Root Directory `/` is the top-most directory in the Linux file system.

It is the starting point of the entire Linux file system hierarchy.

Example:

```text
/
├── home
├── etc
├── usr
├── var
└── tmp
```

---

## Q4. What is the difference between `/` and `/root`?

**Answer:**

These two directories are different.

```text
/       → Root of the entire file system

/root   → Home directory of the root user
```

The `/` directory contains the entire file system, while `/root` is the personal home directory of the root user.

---

## Q5. What is the purpose of `/home`?

**Answer:**

The `/home` directory contains the home directories of normal users.

Example:

```text
/home/rishika
/home/user1
/home/user2
```

Each normal user generally has a separate directory inside `/home`.

---

## Q6. What is the purpose of `/etc`?

**Answer:**

`/etc` contains system-wide configuration files.

These files are used to configure the operating system and various services.

Examples:

```text
/etc/passwd
/etc/hosts
/etc/hostname
```

---

## Q7. What is the purpose of `/bin`?

**Answer:**

`/bin` traditionally contains essential executable commands used by users and the system.

Examples include:

```text
ls
cp
mv
cat
```

On many modern Linux distributions, `/bin` may be a symbolic link to `/usr/bin`.

---

## Q8. What is the purpose of `/boot`?

**Answer:**

`/boot` contains files required during the Linux boot process.

It may contain:

- Linux Kernel
- Bootloader-related files
- Initial RAM filesystem

---

## Q9. What is the purpose of `/tmp`?

**Answer:**

`/tmp` is used to store temporary files created by applications and users.

Depending on the Linux distribution and system configuration, temporary files may be automatically removed after a reboot.

---

## Q10. What is the purpose of `/var`?

**Answer:**

`/var` contains variable data that changes frequently while the system is running.

Examples include:

- Log files
- Cache files
- Spool files
- Application data

An important directory is:

```text
/var/log
```

---

# 🟡 Intermediate Level

## Q11. What is `/dev`?

**Answer:**

`/dev` contains special files that represent hardware devices and other device interfaces.

Examples include:

```text
/dev/sda
/dev/null
/dev/tty
```

Linux provides file-like interfaces to interact with many devices.

---

## Q12. What is `/proc`?

**Answer:**

`/proc` is a virtual file system that provides information about running processes and the Linux kernel.

Examples include:

```text
/proc/cpuinfo
/proc/meminfo
```

The contents of `/proc` are generated dynamically by the kernel.

---

## Q13. What is `/sys`?

**Answer:**

`/sys` is a virtual file system that provides information about the Linux kernel, hardware devices, and device drivers.

It is commonly used to inspect hardware-related information exposed by the kernel.

---

## Q14. What is the difference between `/proc` and `/sys`?

**Answer:**

```text
/proc → Process and kernel-related information

/sys  → Hardware, devices, drivers, and kernel information
```

Both are virtual file systems, but they provide different types of system information.

---

## Q15. What is `/usr`?

**Answer:**

`/usr` contains many user-space applications, libraries, documentation, and shared resources.

Common directories include:

```text
/usr/bin
/usr/lib
/usr/share
```

---

## Q16. What is `/lib`?

**Answer:**

`/lib` traditionally contains essential shared libraries required by system programs and commands.

On many modern Linux distributions, `/lib` may be a symbolic link to a directory under `/usr`.

---

## Q17. What is `/sbin`?

**Answer:**

`/sbin` traditionally contains system administration commands used for system management and maintenance.

Modern Linux distributions may use a merged `/usr` layout where `/sbin` is linked to `/usr/sbin`.

---

## Q18. What is `/media`?

**Answer:**

`/media` is commonly used as a mount point for removable storage devices.

Examples include:

- USB drives
- External storage
- CDs/DVDs

---

## Q19. What is `/mnt`?

**Answer:**

`/mnt` is traditionally used as a temporary mount point for manually mounted file systems.

Example:

```text
/mnt/backup
/mnt/external-drive
```

---

## Q20. What is the difference between `/media` and `/mnt`?

**Answer:**

`/media` is commonly used for removable devices that are automatically mounted by the system.

`/mnt` is traditionally used as a temporary mount point for manually mounted file systems.

---

## Q21. What is `/opt`?

**Answer:**

`/opt` is used for optional or third-party software packages.

Applications installed outside the standard system software structure may be placed in `/opt`.

Example:

```text
/opt/application
```

---

## Q22. What is `/srv`?

**Answer:**

`/srv` contains data used by services provided by the system.

For example, a server application may store service-related data in this directory.

---

## Q23. What is `/run`?

**Answer:**

`/run` contains temporary runtime information about the running system.

It may contain information related to:

- Running services
- Processes
- System state

This information is generally created during system startup.

---

# 🔴 Advanced Level

## Q24. What does "Everything is a file" mean in Linux?

**Answer:**

"Everything is a file" is a common Linux concept that means many system resources are represented through file-like interfaces.

For example:

```text
/dev/sda    → Storage device
/dev/null   → Special device
/proc       → Process information
```

This design provides a consistent way for programs to interact with different system resources.

---

## Q25. What is a virtual file system?

**Answer:**

A virtual file system does not represent regular files stored permanently on a physical disk.

Instead, it provides a file-like interface to dynamically generated information from the kernel and system.

Examples include:

```text
/proc
/sys
```

---

## Q26. Why is `/proc` called a virtual file system?

**Answer:**

`/proc` is called a virtual file system because its contents are generated dynamically by the Linux kernel.

The files inside `/proc` provide information about:

- Running processes
- CPU
- Memory
- Kernel

The information can change as the system runs.

---

## Q27. What is the purpose of `/var/log`?

**Answer:**

`/var/log` stores log files generated by the operating system, services, and applications.

These logs are useful for:

- Troubleshooting
- Monitoring
- Debugging
- Security analysis

---

## Q28. How can you find your current location in Linux?

**Answer:**

Use the `pwd` command.

```bash
pwd
```

`pwd` stands for:

```text
Print Working Directory
```

---

## Q29. How do you navigate to the Root Directory?

**Answer:**

Use:

```bash
cd /
```

---

## Q30. How do you list the contents of the Root Directory?

**Answer:**

Use:

```bash
ls /
```

For detailed information:

```bash
ls -l /
```

---

## Q31. How do you navigate to your home directory?

**Answer:**

You can use:

```bash
cd ~
```

or simply:

```bash
cd
```

The `~` symbol represents the current user's home directory.

---

## Q32. How do you explore the `/etc` directory?

**Answer:**

Use:

```bash
ls /etc
```

To navigate into it:

```bash
cd /etc
```

---

## Q33. How do you check system logs?

**Answer:**

Many Linux systems store logs under:

```text
/var/log
```

You can list the available logs using:

```bash
ls /var/log
```

---

## Q34. How can you check CPU information using `/proc`?

**Answer:**

Use:

```bash
cat /proc/cpuinfo
```

This displays information about the system's CPU.

---

## Q35. How can you check memory information using `/proc`?

**Answer:**

Use:

```bash
cat /proc/meminfo
```

This displays information about system memory.

---

# 🧩 Scenario-Based Questions

## Q36. You need to find a system configuration file. Which directory would you check first?

**Answer:**

I would check:

```text
/etc
```

because it contains system-wide configuration files.

---

## Q37. A user wants to find their personal files. Which directory should they check?

**Answer:**

The user should check their home directory under:

```text
/home
```

For example:

```text
/home/rishika
```

---

## Q38. You need to investigate system logs after an application failure. Where would you look?

**Answer:**

I would check:

```text
/var/log
```

because system and application logs are commonly stored there.

---

## Q39. You want information about running processes. Which directory would you inspect?

**Answer:**

I would inspect:

```text
/proc
```

For example:

```bash
ls /proc
```

---

## Q40. You want to inspect hardware and device information exposed by the kernel. Which directories would you check?

**Answer:**

I would check:

```text
/sys
```

and potentially:

```text
/dev
```

`/sys` provides kernel and hardware information, while `/dev` provides device interfaces.

---

# ⚡ Rapid Fire Revision

| Question | Answer |
|---|---|
| Root of Linux file system? | `/` |
| Normal users' home directories? | `/home` |
| Root user's home? | `/root` |
| Configuration files? | `/etc` |
| Essential commands? | `/bin` |
| System administration commands? | `/sbin` |
| Boot files? | `/boot` |
| Device files? | `/dev` |
| Process information? | `/proc` |
| Hardware and kernel information? | `/sys` |
| Temporary files? | `/tmp` |
| User applications? | `/usr` |
| Logs and variable data? | `/var` |
| Removable media? | `/media` |
| Temporary mount point? | `/mnt` |
| Optional software? | `/opt` |
| Service data? | `/srv` |
| Runtime information? | `/run` |
| Current directory command? | `pwd` |
| Change directory command? | `cd` |
| List directory contents? | `ls` |

---

# 🧠 Important Commands to Remember

```bash
# Show current location
pwd

# Change directory
cd <directory>

# Go to root
cd /

# Go to home directory
cd ~

# List directory contents
ls

# Detailed directory listing
ls -l

# List root contents
ls /

# Explore /etc
ls /etc

# Explore /home
ls /home

# Explore system logs
ls /var/log

# View CPU information
cat /proc/cpuinfo

# View memory information
cat /proc/meminfo
```

---

# 🎯 Interview Preparation Checklist

- [ ] Understand the Linux File System Hierarchy
- [ ] Understand the Root Directory `/`
- [ ] Know the difference between `/` and `/root`
- [ ] Know the purpose of important Linux directories
- [ ] Understand `/proc` and `/sys`
- [ ] Understand `/dev`
- [ ] Know where configuration files are stored
- [ ] Know where system logs are stored
- [ ] Know how to navigate directories
- [ ] Practice `cd`, `pwd`, and `ls`
- [ ] Understand virtual file systems
- [ ] Practice scenario-based questions

---

# 🔗 Related Resources

📖 [Lesson 01 — Linux File System Hierarchy](../levels/level-02-file-system/01-linux-file-system-hierarchy.md)

🖼️ [Linux File System Hierarchy Diagram](../assets/diagrams/linux-file-system-hierarchy.md)

📖 [Lesson 02 — Important Linux Directories](../levels/level-02-file-system/02-important-linux-directories.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02 Interview Preparation**

> *Understand the system. Answer with confidence. Keep learning.*

---

# 📂 Lesson 02 — Important Linux Directories

## Q41. Which directory contains system-wide configuration files?

**Answer:**

The `/etc` directory contains system-wide configuration files.

Examples include:

```text
/etc/passwd
/etc/hosts
/etc/hostname
```

---

## Q42. Where are normal users' home directories stored?

**Answer:**

Normal users' home directories are generally stored under:

```text
/home
```

Example:

```text
/home/rishika
```

---

## Q43. What is `/root`?

**Answer:**

`/root` is the home directory of the root user.

It should not be confused with `/`, which is the root of the entire file system.

```text
/      → Root of entire file system
/root  → Root user's home directory
```

---

## Q44. What is the purpose of `/bin`?

**Answer:**

`/bin` traditionally contains essential executable commands used by users and the system.

Examples include:

```text
ls
cp
mv
cat
```

On modern Linux distributions, `/bin` may be a symbolic link to `/usr/bin`.

---

## Q45. What is the purpose of `/sbin`?

**Answer:**

`/sbin` traditionally contains system administration commands used for system management and maintenance.

On systems using a merged `/usr` layout, `/sbin` may be linked to `/usr/sbin`.

---

## Q46. What is stored in `/boot`?

**Answer:**

`/boot` contains files required for the Linux boot process.

It may contain:

- Linux Kernel
- Bootloader-related files
- Initial RAM filesystem

---

## Q47. What is the purpose of `/dev`?

**Answer:**

`/dev` contains special files representing devices and device interfaces.

Examples:

```text
/dev/sda
/dev/null
/dev/tty
```

---

## Q48. What is the purpose of `/lib`?

**Answer:**

`/lib` traditionally contains essential shared libraries required by system programs and commands.

On many modern distributions, `/lib` may be a symbolic link under the merged `/usr` layout.

---

## Q49. What is `/media` used for?

**Answer:**

`/media` is commonly used as a mount point for removable storage devices.

Examples include:

- USB drives
- External drives
- CDs/DVDs

---

## Q50. What is `/mnt` used for?

**Answer:**

`/mnt` is traditionally used as a temporary mount point for manually mounted file systems.

Example:

```text
/mnt/backup
/mnt/external-drive
```

---

## Q51. What is the difference between `/media` and `/mnt`?

**Answer:**

`/media` is commonly used for removable devices that are automatically mounted by the system.

`/mnt` is traditionally used as a temporary mount point for manually mounted file systems.

---

## Q52. What is `/opt`?

**Answer:**

`/opt` is used for optional or third-party software packages.

Example:

```text
/opt/application
```

---

## Q53. What is `/proc`?

**Answer:**

`/proc` is a virtual file system that provides information about running processes and the Linux kernel.

Examples:

```text
/proc/cpuinfo
/proc/meminfo
```

---

## Q54. What is `/run`?

**Answer:**

`/run` contains temporary runtime information about the running system.

It may contain information related to:

- Running services
- Processes
- System state

---

## Q55. What is `/srv`?

**Answer:**

`/srv` contains data used by services provided by the system.

For example, a web server may store service-related data in `/srv`.

---

## Q56. What is `/sys`?

**Answer:**

`/sys` is a virtual file system that provides information about:

- Hardware
- Devices
- Device drivers
- Linux kernel

---

## Q57. What is `/tmp`?

**Answer:**

`/tmp` is used for temporary files created by applications and users.

Temporary files may be automatically removed depending on the system configuration.

---

## Q58. What is `/usr`?

**Answer:**

`/usr` contains user-space applications, libraries, documentation, and shared resources.

Common directories include:

```text
/usr/bin
/usr/lib
/usr/sbin
/usr/share
```

---

## Q59. What is `/var`?

**Answer:**

`/var` contains variable data that changes during normal system operation.

Examples include:

- Logs
- Cache
- Spool data
- Application data

An important subdirectory is:

```text
/var/log
```

---

# 🧩 Scenario-Based Questions — Important Directories

## Q60. You need to modify a system configuration file. Where would you normally look?

**Answer:**

I would look in:

```text
/etc
```

because it contains system-wide configuration files.

---

## Q61. A user wants to access their personal documents. Where would you look?

**Answer:**

I would look under the user's home directory:

```text
/home/<username>
```

For example:

```text
/home/rishika/Documents
```

---

## Q62. You need to investigate why a service failed. Which directory might contain useful information?

**Answer:**

I would check:

```text
/var/log
```

because system and application logs are commonly stored there.

---

## Q63. You need to inspect information about the CPU and memory. Which directory can provide this information?

**Answer:**

I would inspect:

```text
/proc
```

For example:

```bash
cat /proc/cpuinfo
cat /proc/meminfo
```

---

## Q64. You need to inspect hardware information exposed by the Linux kernel. Which directory would you check?

**Answer:**

I would check:

```text
/sys
```

---

## Q65. You connect a USB device to a Linux system. Which directory might be used for its mount point?

**Answer:**

A removable device may be automatically mounted under:

```text
/media
```

The exact behavior depends on the desktop environment and system configuration.

---

## Q66. You manually mount a file system temporarily. Which directory would traditionally be used?

**Answer:**

The traditional location is:

```text
/mnt
```

---

## Q67. You install a third-party application that is kept separate from the standard system software. Which directory might be suitable?

**Answer:**

The application could be installed under:

```text
/opt
```

---

## Q68. Where would you look for files required during system startup?

**Answer:**

I would look in:

```text
/boot
```

---

# ⚡ Rapid Fire — Lesson 02

| Question | Answer |
|---|---|
| Configuration files? | `/etc` |
| Normal users' home? | `/home` |
| Root user's home? | `/root` |
| Essential commands? | `/bin` |
| System administration commands? | `/sbin` |
| Boot files? | `/boot` |
| Device interfaces? | `/dev` |
| Essential libraries? | `/lib` |
| Removable media? | `/media` |
| Temporary mount point? | `/mnt` |
| Optional software? | `/opt` |
| Process information? | `/proc` |
| Runtime information? | `/run` |
| Service data? | `/srv` |
| Hardware/kernel information? | `/sys` |
| Temporary files? | `/tmp` |
| User applications? | `/usr` |
| Variable data/logs? | `/var` |

---

# 🎯 Level 02 Interview Checklist

- [ ] Explain the Linux File System Hierarchy
- [ ] Explain the Root Directory `/`
- [ ] Differentiate `/` and `/root`
- [ ] Explain `/etc`
- [ ] Explain `/home`
- [ ] Explain `/bin` and `/sbin`
- [ ] Explain `/boot`
- [ ] Explain `/dev`
- [ ] Explain `/proc`
- [ ] Explain `/sys`
- [ ] Explain `/tmp`
- [ ] Explain `/usr`
- [ ] Explain `/var`
- [ ] Differentiate `/media` and `/mnt`
- [ ] Explain `/opt`
- [ ] Explain `/run`
- [ ] Explain `/srv`
- [ ] Practice directory-based scenarios

---

## 🔗 Related Resources

🖼️ [Linux File System Hierarchy Diagram](../assets/diagrams/linux-file-system-hierarchy.md)

🖼️ [Important Linux Directories Diagram](../assets/diagrams/important-linux-directories.md)

📖 [Level 02 — Linux File System](../levels/level-02-file-system/README.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02 Interview Preparation**

> *Know the directories. Understand the system. Answer with confidence.*

---

# 🛣️ Lesson 03 — Linux File Paths & Navigation

## Q69. What is a file path in Linux?

**Answer:**

A file path describes the location of a file or directory within the Linux file system.

Example:

```text
/home/rishika/Documents
```

---

## Q70. What is an absolute path?

**Answer:**

An absolute path specifies the complete location of a file or directory starting from the Root Directory `/`.

Example:

```text
/home/rishika/Documents
```

An absolute path does not depend on the current working directory.

---

## Q71. What is a relative path?

**Answer:**

A relative path specifies a location relative to the current working directory.

Example:

```text
Documents/Linux
```

A relative path does not start with `/`.

---

## Q72. What is the difference between an absolute path and a relative path?

**Answer:**

An absolute path starts from the Root Directory `/` and provides the complete location.

A relative path starts from the current working directory and depends on the current location.

Example:

```text
Absolute:
/home/rishika/Documents

Relative:
Documents
```

---

## Q73. What does the `/` symbol represent?

**Answer:**

`/` represents the Root Directory of the Linux file system.

All other directories exist under the Root Directory.

Example:

```text
/
├── home
├── etc
├── var
└── usr
```

---

## Q74. What does `~` represent in Linux?

**Answer:**

The `~` symbol represents the current user's home directory.

For example:

```bash
cd ~
```

takes the user to their home directory.

---

## Q75. What does `.` represent?

**Answer:**

`.` represents the current working directory.

Example:

```bash
ls .
```

This lists the contents of the current directory.

---

## Q76. What does `..` represent?

**Answer:**

`..` represents the parent directory of the current working directory.

Example:

If the current location is:

```text
/home/rishika/Documents
```

Then:

```bash
cd ..
```

moves to:

```text
/home/rishika
```

---

## Q77. What does `cd -` do?

**Answer:**

`cd -` switches to the previous working directory.

Example:

```bash
cd /etc
cd /var
cd -
```

The last command takes you back to:

```text
/etc
```

---

## Q78. What is the purpose of the `pwd` command?

**Answer:**

`pwd` stands for **Print Working Directory**.

It displays the absolute path of the current working directory.

Example:

```bash
pwd
```

Output:

```text
/home/rishika
```

---

## Q79. What is the purpose of the `cd` command?

**Answer:**

`cd` stands for **Change Directory**.

It is used to navigate between directories.

Examples:

```bash
cd /etc
cd Documents
cd ..
cd ~
```

---

## Q80. What does the `ls` command do?

**Answer:**

`ls` lists the contents of a directory.

Examples:

```bash
ls
ls -l
ls -a
ls -la
```

---

## Q81. How do you go to the Root Directory?

**Answer:**

Use:

```bash
cd /
```

---

## Q82. How do you go to your Home Directory?

**Answer:**

Use:

```bash
cd ~
```

or simply:

```bash
cd
```

---

## Q83. How do you move one directory up?

**Answer:**

Use:

```bash
cd ..
```

This moves to the parent directory.

---

## Q84. How do you check your current location?

**Answer:**

Use:

```bash
pwd
```

---

## Q85. How do you list hidden files?

**Answer:**

Use:

```bash
ls -a
```

Hidden files in Linux usually begin with a `.`.

Examples:

```text
.bashrc
.profile
.gitconfig
```

---

# 🧩 Scenario-Based Interview Questions

## Q86. You are currently in `/home/rishika` and want to go to `/home/rishika/Documents`. How can you do it using a relative path?

**Answer:**

Use:

```bash
cd Documents
```

---

## Q87. You are currently in `/home/rishika` and want to go to `/home/rishika/Documents`. How can you do it using an absolute path?

**Answer:**

Use:

```bash
cd /home/rishika/Documents
```

---

## Q88. You are currently in `/home/rishika/Documents`. How do you go back to `/home/rishika`?

**Answer:**

Use:

```bash
cd ..
```

---

## Q89. You are currently in `/var/log`. How do you go directly to the Root Directory?

**Answer:**

Use:

```bash
cd /
```

---

## Q90. You are currently in `/etc` and then navigate to `/var`. How can you return to `/etc`?

**Answer:**

Use:

```bash
cd -
```

---

## Q91. You don't know your current location. Which command should you use?

**Answer:**

Use:

```bash
pwd
```

---

## Q92. You want to see hidden files in the current directory. Which command should you use?

**Answer:**

Use:

```bash
ls -a
```

---

## Q93. What happens if you use `cd ..` while you are in `/home`?

**Answer:**

You move to the parent directory:

```text
/
```

Because `/` is the parent of `/home`.

---

## Q94. What happens if you use `cd ..` while you are already in `/`?

**Answer:**

You remain in:

```text
/
```

The Root Directory has no parent directory above it.

---

## Q95. Why is an absolute path more predictable than a relative path?

**Answer:**

An absolute path always starts from `/` and identifies the complete location of a file or directory.

A relative path depends on the current working directory, so the same relative path may point to different locations depending on where the user currently is.

---

# ⚡ Rapid Fire — Lesson 03

| Question | Answer |
|---|---|
| Root Directory symbol? | `/` |
| Home Directory symbol? | `~` |
| Current Directory symbol? | `.` |
| Parent Directory symbol? | `..` |
| Previous Directory? | `-` with `cd` |
| Show current location? | `pwd` |
| Change directory? | `cd` |
| List files? | `ls` |
| Show hidden files? | `ls -a` |
| Absolute path starts with? | `/` |
| Relative path depends on? | Current working directory |
| Go to Root? | `cd /` |
| Go to Home? | `cd ~` |
| Go to Parent? | `cd ..` |
| Go to Previous Directory? | `cd -` |

---

# 🎯 Interview Checklist — Lesson 03

- [ ] Explain file paths
- [ ] Explain absolute paths
- [ ] Explain relative paths
- [ ] Differentiate absolute and relative paths
- [ ] Explain `/`
- [ ] Explain `~`
- [ ] Explain `.`
- [ ] Explain `..`
- [ ] Explain `cd -`
- [ ] Explain `pwd`
- [ ] Explain `cd`
- [ ] Explain `ls`
- [ ] Explain hidden files
- [ ] Solve navigation scenarios
- [ ] Practice rapid-fire questions

---

## 🔗 Related Resources

📖 [Lesson 03 — Linux File Paths & Navigation](../levels/level-02-file-system/03-linux-file-paths-and-navigation.md)

🖼️ [Linux File Paths & Navigation Diagram](../assets/diagrams/linux-file-paths-navigation.md)

🧪 [Linux File System Lab](../labs/01-linux-file-system-lab.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 03 Interview Preparation**

> *Master the path. Master the terminal.*