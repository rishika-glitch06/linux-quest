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

---

# 🛠️ Lesson 04 — File & Directory Management Interview Preparation

## Q96. Which command is used to create an empty file?

**Answer:**

The `touch` command is used to create an empty file.

```bash
touch notes.txt
```

---

## Q97. Which command is used to create a directory?

**Answer:**

The `mkdir` command creates a new directory.

```bash
mkdir Projects
```

---

## Q98. What is the purpose of `mkdir -p`?

**Answer:**

`mkdir -p` creates parent directories automatically when they do not already exist.

Example:

```bash
mkdir -p Projects/Linux/Lesson04
```

This creates:

```text
Projects/
└── Linux/
    └── Lesson04/
```

---

## Q99. Which command is used to copy a file?

**Answer:**

The `cp` command is used to copy files.

Example:

```bash
cp notes.txt backup.txt
```

The original file remains unchanged.

---

## Q100. How do you copy a directory in Linux?

**Answer:**

Use the recursive option `-r` with `cp`.

```bash
cp -r Projects Projects_Backup
```

The `-r` option allows the directory and its contents to be copied.

---

## Q101. Which command is used to move a file?

**Answer:**

The `mv` command is used to move a file.

Example:

```bash
mv notes.txt Projects/
```

---

## Q102. Can `mv` be used to rename a file?

**Answer:**

Yes. The `mv` command is also used to rename files and directories.

Example:

```bash
mv notes.txt linux_notes.txt
```

The file is renamed from `notes.txt` to `linux_notes.txt`.

---

## Q103. What is the difference between `cp` and `mv`?

**Answer:**

`cp` creates a copy while keeping the original.

`mv` moves the original file to another location or changes its name.

Example:

```bash
cp notes.txt backup.txt
```

The original `notes.txt` remains.

```bash
mv notes.txt backup.txt
```

The original name `notes.txt` no longer exists at the original location.

---

## Q104. Which command is used to delete a file?

**Answer:**

The `rm` command is used to remove files.

Example:

```bash
rm notes.txt
```

---

## Q105. How do you remove an empty directory?

**Answer:**

Use:

```bash
rmdir EmptyFolder
```

`rmdir` works only when the directory is empty.

---

## Q106. How do you remove a directory containing files?

**Answer:**

Use:

```bash
rm -r Projects
```

The `-r` option means recursive and allows the directory and its contents to be removed.

---

## Q107. What is the difference between `rmdir` and `rm -r`?

**Answer:**

`rmdir` removes only empty directories.

```bash
rmdir EmptyFolder
```

`rm -r` removes directories recursively, including their contents.

```bash
rm -r Projects
```

---

## Q108. What does `rm -rf` do?

**Answer:**

`rm -rf` forcefully and recursively removes a directory and its contents.

```bash
rm -rf Projects
```

Where:

```text
-r → Recursive
-f → Force
```

⚠️ It should be used carefully because it can permanently delete large amounts of data.

---

## Q109. What is the difference between `rm -r` and `rm -rf`?

**Answer:**

Both recursively remove directories and their contents.

```bash
rm -r Projects
```

removes recursively and may ask for confirmation depending on permissions and conditions.

```bash
rm -rf Projects
```

uses force mode and suppresses many confirmation prompts and errors.

`rm -rf` is more dangerous and should be used carefully.

---

## Q110. Which command is used to display the contents of a file?

**Answer:**

The `cat` command displays the contents of a file.

Example:

```bash
cat notes.txt
```

---

## Q111. How can you view a large file page by page?

**Answer:**

Use:

```bash
less filename.txt
```

or:

```bash
more filename.txt
```

---

## Q112. What is a wildcard in Linux?

**Answer:**

A wildcard is a special character used to match multiple file names.

The `*` wildcard matches zero or more characters.

Example:

```bash
ls *.txt
```

This lists all files ending with `.txt`.

---

## Q113. What does `*.txt` mean?

**Answer:**

It matches all files whose names end with `.txt`.

Example:

```text
notes.txt
backup.txt
linux.txt
```

Command:

```bash
ls *.txt
```

---

# 🧩 Scenario-Based Interview Questions

## Q114. You need to create a file named `linux.txt`. Which command will you use?

**Answer:**

```bash
touch linux.txt
```

---

## Q115. You need to create a directory named `LinuxQuest`. Which command will you use?

**Answer:**

```bash
mkdir LinuxQuest
```

---

## Q116. You need to create the following directory structure in one command:

```text
LinuxQuest/
└── Level02/
    └── Lesson04/
```

**Answer:**

```bash
mkdir -p LinuxQuest/Level02/Lesson04
```

---

## Q117. You want to create a backup copy of `notes.txt` named `notes_backup.txt`.

**Answer:**

```bash
cp notes.txt notes_backup.txt
```

---

## Q118. You want to copy the entire `Projects` directory to `Projects_Backup`.

**Answer:**

```bash
cp -r Projects Projects_Backup
```

---

## Q119. You want to move `notes.txt` into the `Documents` directory.

**Answer:**

```bash
mv notes.txt Documents/
```

---

## Q120. You want to rename `old.txt` to `new.txt`.

**Answer:**

```bash
mv old.txt new.txt
```

---

## Q121. You want to delete a file named `temporary.txt`.

**Answer:**

```bash
rm temporary.txt
```

---

## Q122. You want to delete an empty directory named `Test`.

**Answer:**

```bash
rmdir Test
```

---

## Q123. You want to delete a directory named `Test` containing files and subdirectories.

**Answer:**

```bash
rm -r Test
```

---

## Q124. You want to permanently force-remove a directory and all its contents.

**Answer:**

```bash
rm -rf Test
```

⚠️ This command should be used with extreme caution.

---

## Q125. You want to display the contents of `notes.txt`.

**Answer:**

```bash
cat notes.txt
```

---

## Q126. You want to list all `.log` files in the current directory.

**Answer:**

```bash
ls *.log
```

---

## Q127. You accidentally created an empty directory and want to remove it.

**Answer:**

```bash
rmdir DirectoryName
```

---

## Q128. You tried to use `rmdir` on a directory containing files. What will happen?

**Answer:**

The command will fail because `rmdir` can remove only empty directories.

To remove a directory containing files, use:

```bash
rm -r DirectoryName
```

---

# 🧠 Conceptual Questions

## Q129. Why is `rm -rf` considered dangerous?

**Answer:**

Because it recursively and forcefully deletes files and directories without asking for many confirmations.

If used on the wrong path, it can cause significant data loss.

---

## Q130. Does `cp` remove the original file?

**Answer:**

No.

`cp` creates a copy and keeps the original.

---

## Q131. Does `mv` create a second copy of the file?

**Answer:**

No.

`mv` moves the original file or renames it.

---

## Q132. What does the `-r` option generally mean?

**Answer:**

`-r` generally means **recursive**.

It allows a command to operate on a directory and its contents recursively.

Examples:

```bash
cp -r
rm -r
```

---

## Q133. What does the `-f` option mean in `rm -rf`?

**Answer:**

`-f` means **force**.

It suppresses many prompts and ignores certain errors.

---

# ⚡ Rapid-Fire Revision

| Question | Answer |
|---|---|
| Create an empty file | `touch` |
| Create a directory | `mkdir` |
| Create nested directories | `mkdir -p` |
| Copy a file | `cp` |
| Copy a directory | `cp -r` |
| Move a file | `mv` |
| Rename a file | `mv` |
| Delete a file | `rm` |
| Delete an empty directory | `rmdir` |
| Delete a directory recursively | `rm -r` |
| Force recursive deletion | `rm -rf` |
| Display file contents | `cat` |
| View large files | `less` / `more` |
| Match multiple characters | `*` |
| Match one character | `?` |

---

# 🎯 Interview Checklist — Lesson 04

- [ ] Explain `touch`
- [ ] Explain `mkdir`
- [ ] Explain `mkdir -p`
- [ ] Explain `cp`
- [ ] Explain `cp -r`
- [ ] Explain `mv`
- [ ] Explain file renaming using `mv`
- [ ] Explain `rm`
- [ ] Explain `rmdir`
- [ ] Explain `rm -r`
- [ ] Explain `rm -rf`
- [ ] Explain `cat`
- [ ] Explain `less`
- [ ] Explain `more`
- [ ] Explain wildcards
- [ ] Differentiate `cp` and `mv`
- [ ] Differentiate `rmdir` and `rm -r`
- [ ] Understand the risks of `rm -rf`
- [ ] Solve file management scenarios
- [ ] Practice rapid-fire questions

---

## 🔗 Related Resources

📖 [Lesson 04 — File & Directory Management](../levels/level-02-file-system/04-file-and-directory-management.md)

🖼️ [File & Directory Management Diagram](../assets/diagrams/file-and-directory-management.md)

🧪 [File & Directory Management Lab](../labs/04-file-and-directory-management-lab.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 04 Interview Preparation**

> *Create. Copy. Move. Manage.*

---

# 🔐 Lesson 05 — File Permissions & Ownership Interview Preparation

## Q134. What are Linux file permissions?

**Answer:**

Linux file permissions control who can read, write, or execute a file or access a directory.

The three basic permissions are:

```text
r → Read
w → Write
x → Execute
```

---

## Q135. What are the three permission categories in Linux?

**Answer:**

Linux permissions are assigned to:

```text
u → User / Owner
g → Group
o → Others
```

Example:

```text
-rwxr-xr--
```

Means:

```text
User    → rwx
Group   → r-x
Others  → r--
```

---

## Q136. What does `r` mean?

**Answer:**

`r` means **read**.

For a file:

```text
Read the contents
```

For a directory:

```text
List the contents
```

---

## Q137. What does `w` mean?

**Answer:**

`w` means **write**.

For a file:

```text
Modify the contents
```

For a directory:

```text
Create, delete, or rename entries
```

---

## Q138. What does `x` mean?

**Answer:**

`x` means **execute**.

For a file:

```text
Run the file as a program
```

For a directory:

```text
Access or enter the directory
```

---

## Q139. How do you view file permissions?

**Answer:**

Use:

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 rishika users 120 Jul 27 notes.txt
```

The first part:

```text
-rw-r--r--
```

represents the file type and permissions.

---

## Q140. What does the first character in `ls -l` output represent?

**Answer:**

It represents the file type.

```text
- → Regular file
d → Directory
l → Symbolic link
```

Example:

```text
-rw-r--r--
```

The first character `-` means it is a regular file.

---

## Q141. Explain `-rwxr-xr--`.

**Answer:**

Break it into groups:

```text
-rwxr-xr--
│ │   │   │
│ │   │   └── Others
│ │   └────── Group
│ └────────── User
└──────────── File type
```

Therefore:

```text
User    → rwx → Read + Write + Execute
Group   → r-x → Read + Execute
Others  → r-- → Read only
```

---

## Q142. What is `chmod`?

**Answer:**

`chmod` stands for **change mode**.

It is used to change file and directory permissions.

Example:

```bash
chmod u+x script.sh
```

This adds execute permission for the owner.

---

## Q143. What are symbolic permission modes?

**Answer:**

Symbolic modes use:

```text
u → User
g → Group
o → Others
a → All
```

Operators:

```text
+ → Add permission
- → Remove permission
= → Set exact permission
```

Example:

```bash
chmod u+x script.sh
```

---

## Q144. How do you add execute permission to the owner?

**Answer:**

```bash
chmod u+x script.sh
```

---

## Q145. How do you add write permission to the group?

**Answer:**

```bash
chmod g+w notes.txt
```

---

## Q146. How do you remove write permission from others?

**Answer:**

```bash
chmod o-w notes.txt
```

---

## Q147. How do you give execute permission to everyone?

**Answer:**

```bash
chmod a+x script.sh
```

---

## Q148. What are numeric permissions?

**Answer:**

Linux permissions can be represented using numbers.

```text
Read    = 4
Write   = 2
Execute = 1
```

The values are added together.

Examples:

```text
r-- = 4
-w- = 2
--x = 1
rw- = 6
r-x = 5
rwx = 7
```

---

## Q149. What does `chmod 755` mean?

**Answer:**

```bash
chmod 755 filename
```

Means:

```text
User    → 7 → rwx
Group   → 5 → r-x
Others  → 5 → r-x
```

So the permission becomes:

```text
rwxr-xr-x
```

---

## Q150. What does `chmod 644` mean?

**Answer:**

```bash
chmod 644 notes.txt
```

Means:

```text
User    → 6 → rw-
Group   → 4 → r--
Others  → 4 → r--
```

Result:

```text
rw-r--r--
```

This is a common permission for regular files.

---

## Q151. What does `chmod 777` mean?

**Answer:**

```bash
chmod 777 filename
```

Means:

```text
User    → rwx
Group   → rwx
Others  → rwx
```

Everyone has full permissions.

⚠️ This is generally discouraged unless there is a specific reason.

---

## Q152. Why is `chmod 777` dangerous?

**Answer:**

It gives everyone read, write, and execute permissions.

This can allow unauthorized users or processes to modify or execute files.

It violates the principle of least privilege when used unnecessarily.

---

## Q153. What is the Principle of Least Privilege?

**Answer:**

The Principle of Least Privilege means giving users and processes only the permissions they actually need.

For example, if a file only needs to be readable, do not give it write or execute permissions.

---

## Q154. What is file ownership?

**Answer:**

Every Linux file has:

```text
Owner
Group
```

Example:

```text
-rw-r--r-- 1 rishika developers 120 notes.txt
```

Here:

```text
Owner → rishika
Group → developers
```

---

## Q155. What is `chown`?

**Answer:**

`chown` stands for **change owner**.

It is used to change the owner of a file or directory.

Example:

```bash
sudo chown alice notes.txt
```

---

## Q156. How do you change both owner and group?

**Answer:**

Use:

```bash
sudo chown alice:developers notes.txt
```

This changes:

```text
Owner → alice
Group → developers
```

---

## Q157. What is `chgrp`?

**Answer:**

`chgrp` stands for **change group**.

It changes the group ownership of a file or directory.

Example:

```bash
sudo chgrp developers notes.txt
```

---

## Q158. What is the difference between `chmod` and `chown`?

**Answer:**

```text
chmod
│
└── Changes permissions

chown
│
└── Changes ownership
```

Example:

```bash
chmod 644 notes.txt
```

Changes permissions.

```bash
sudo chown alice notes.txt
```

Changes ownership.

---

## Q159. What is the difference between `chown` and `chgrp`?

**Answer:**

```text
chown
│
└── Changes file owner
    and optionally group

chgrp
│
└── Changes group ownership
```

---

## Q160. How are directory permissions different from file permissions?

**Answer:**

For files:

```text
r → Read contents
w → Modify contents
x → Execute
```

For directories:

```text
r → List contents
w → Create/delete/rename entries
x → Enter/access directory
```

---

## Q161. What does execute permission mean for a directory?

**Answer:**

Execute permission on a directory allows a user to access or enter the directory and access entries within it, subject to other permissions.

Example:

```bash
cd Projects
```

requires execute permission on the directory.

---

## Q162. What does `chmod 754` mean?

**Answer:**

```bash
chmod 754 filename
```

Breakdown:

```text
7 → rwx → User
5 → r-x → Group
4 → r-- → Others
```

Final permission:

```text
rwxr-xr--
```

---

# 🧩 Scenario-Based Interview Questions

## Q163. You want the owner to have full permissions and everyone else to have read-only access. Which command?

**Answer:**

```bash
chmod 744 filename
```

Result:

```text
rwxr--r--
```

---

## Q164. You want a script to be executable by the owner.

**Answer:**

```bash
chmod u+x script.sh
```

---

## Q165. You want everyone to be able to execute a script.

**Answer:**

```bash
chmod a+x script.sh
```

---

## Q166. You want to remove write permission from everyone.

**Answer:**

```bash
chmod a-w filename
```

---

## Q167. You want to change the owner of `notes.txt` to `alice`.

**Answer:**

```bash
sudo chown alice notes.txt
```

---

## Q168. You want to change the group of `notes.txt` to `developers`.

**Answer:**

```bash
sudo chgrp developers notes.txt
```

---

## Q169. You want to change both owner and group.

**Answer:**

```bash
sudo chown alice:developers notes.txt
```

---

## Q170. A file has permissions `-rw-r--r--`. What can the owner do?

**Answer:**

The owner has:

```text
rw-
```

Therefore, the owner can:

```text
Read
Write
```

But cannot execute the file.

---

## Q171. A file has permissions `-rwxr-x---`. Who has access?

**Answer:**

```text
User:
rwx → Full permissions

Group:
r-x → Read + Execute

Others:
--- → No permissions
```

Only the owner and group have access.

---

## Q172. You see `chmod 777` in a production server. What would you do?

**Answer:**

I would first investigate why the permission was set to `777`.

I would avoid changing it blindly, because changing permissions without understanding the application's requirements could break functionality.

If full permissions are unnecessary, I would apply the principle of least privilege and use the minimum permissions required.

---

# ⚡ Rapid-Fire Revision

| Question | Answer |
|---|---|
| Read permission | `r` |
| Write permission | `w` |
| Execute permission | `x` |
| Owner | `u` |
| Group | `g` |
| Others | `o` |
| All | `a` |
| View permissions | `ls -l` |
| Change permissions | `chmod` |
| Change owner | `chown` |
| Change group | `chgrp` |
| Read value | `4` |
| Write value | `2` |
| Execute value | `1` |
| Full permissions | `7` |
| Common file permission | `644` |
| Common executable permission | `755` |
| Full access for everyone | `777` |
| Recursive permission change | `chmod -R` |

---

# 🎯 Interview Checklist — Lesson 05

- [ ] Explain Linux file permissions
- [ ] Explain `r`, `w`, and `x`
- [ ] Explain User, Group, and Others
- [ ] Read `ls -l` output
- [ ] Understand permission notation
- [ ] Explain `chmod`
- [ ] Use symbolic permissions
- [ ] Understand numeric permissions
- [ ] Calculate permissions using 4, 2, and 1
- [ ] Explain `chmod 644`
- [ ] Explain `chmod 755`
- [ ] Explain why `chmod 777` can be dangerous
- [ ] Explain `chown`
- [ ] Explain `chgrp`
- [ ] Understand directory permissions
- [ ] Understand the Principle of Least Privilege
- [ ] Solve permission scenarios
- [ ] Solve ownership scenarios
- [ ] Complete rapid-fire revision

---

## 🔗 Related Resources

📖 [Lesson 05 — File Permissions & Ownership](../levels/level-02-file-system/05-file-permissions-and-ownership.md)

🖼️ [File Permissions & Ownership Diagram](../assets/diagrams/file-permissions-and-ownership.md)

🧪 [File Permissions & Ownership Lab](../labs/05-file-permissions-and-ownership-lab.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 05 Interview Preparation**

> *Understand permissions. Control access. Secure the system.*