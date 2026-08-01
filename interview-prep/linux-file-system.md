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

---

# 👤 Lesson 06 — Linux Users & Groups Interview Preparation

> Interview preparation covering Linux users, groups, UID, GID, root, authentication files, user management, group management, and `sudo`.

---

# 🟢 Basic Interview Questions

## Q173. What is a user in Linux?

**Answer:**

A user in Linux represents an identity that can interact with the operating system.

A user can:

- Own files
- Access resources
- Run processes
- Execute commands
- Have specific permissions

Each user has a unique **UID (User ID)**.

---

## Q174. What is a group in Linux?

**Answer:**

A group is a collection of users.

Groups simplify permission management because permissions can be assigned to a group instead of configuring each user individually.

Example:

```text
developers
    │
    ├── Alice
    ├── Bob
    └── Charlie
```

All members of the group can receive permissions assigned to the group.

---

## Q175. What is UID?

**Answer:**

UID stands for **User ID**.

It is a unique numeric identifier assigned to a Linux user.

Check the current user's UID:

```bash
id -u
```

Check another user's UID:

```bash
id -u username
```

Example:

```text
1000
```

---

## Q176. What is GID?

**Answer:**

GID stands for **Group ID**.

It is a unique numeric identifier assigned to a Linux group.

You can view GID information using:

```bash
id
```

Example:

```text
uid=1000(rishika) gid=1000(rishika)
```

Here:

```text
UID = 1000
GID = 1000
```

---

## Q177. What is the UID of the root user?

**Answer:**

The root user's UID is:

```text
0
```

You can verify it using:

```bash
id root
```

---

## Q178. Who is the root user?

**Answer:**

Root is the superuser in Linux.

The root user has extensive privileges and can perform administrative operations such as:

- Creating and deleting users
- Changing file ownership
- Changing permissions
- Managing system services
- Modifying system configuration
- Installing software

Root has:

```text
UID = 0
```

---

## Q179. What is the difference between a normal user and root?

**Answer:**

```text
Normal User
    ↓
Limited permissions

Root
    ↓
Extensive administrative privileges
```

A normal user generally needs `sudo` to perform privileged operations.

---

# 🔍 User Identification Commands

## Q180. What does `whoami` do?

**Answer:**

`whoami` displays the username of the currently logged-in user.

```bash
whoami
```

Example output:

```text
rishika
```

---

## Q181. What does the `id` command do?

**Answer:**

The `id` command displays information about a user's identity.

It can show:

- UID
- GID
- Group memberships

Example:

```bash
id
```

Example output:

```text
uid=1000(rishika) gid=1000(rishika) groups=1000(rishika)
```

---

## Q182. How do you find the UID of a user?

**Answer:**

Use:

```bash
id -u username
```

Example:

```bash
id -u alice
```

---

## Q183. How do you find a user's group membership?

**Answer:**

Use:

```bash
groups username
```

Example:

```bash
groups alice
```

You can also use:

```bash
id alice
```

---

## Q184. What is the difference between `who`, `w`, and `users`?

**Answer:**

```text
who
 ↓
Shows logged-in users with basic information

w
 ↓
Shows detailed information about logged-in users

users
 ↓
Shows usernames of currently logged-in users
```

Commands:

```bash
who
```

```bash
w
```

```bash
users
```

---

# 📄 Linux User and Group Files

## Q185. What is `/etc/passwd`?

**Answer:**

`/etc/passwd` is a system file that stores basic information about Linux user accounts.

It typically contains:

- Username
- Password placeholder
- UID
- GID
- User information
- Home directory
- Login shell

View it using:

```bash
cat /etc/passwd
```

---

## Q186. Explain the fields in `/etc/passwd`.

**Answer:**

A typical entry looks like:

```text
rishika:x:1000:1000:Rishika:/home/rishika:/bin/bash
```

The fields are:

```text
1. Username
2. Password placeholder
3. UID
4. GID
5. User information / GECOS
6. Home directory
7. Login shell
```

---

## Q187. What is `/etc/shadow`?

**Answer:**

`/etc/shadow` stores password-related information and authentication data for Linux users.

It contains sensitive information and therefore has restricted access.

Access generally requires administrative privileges:

```bash
sudo cat /etc/shadow
```

---

## Q188. What is `/etc/group`?

**Answer:**

`/etc/group` stores information about Linux groups.

It contains information such as:

- Group name
- GID
- Group members

View it using:

```bash
cat /etc/group
```

Example:

```text
developers:x:1001:alice,bob
```

---

## Q189. What is the difference between `/etc/passwd` and `/etc/shadow`?

**Answer:**

```text
/etc/passwd
    ↓
Basic user account information

/etc/shadow
    ↓
Password and authentication-related information
```

The `/etc/shadow` file is more restricted because it contains sensitive authentication information.

---

## Q190. What is the difference between `/etc/passwd` and `/etc/group`?

**Answer:**

```text
/etc/passwd
    ↓
Stores user account information

/etc/group
    ↓
Stores group information
```

---

# ⭐ Primary and Secondary Groups

## Q191. What is a primary group?

**Answer:**

A primary group is the default group associated with a user.

It is represented by the user's GID.

Example:

```bash
id alice
```

Output may contain:

```text
uid=1001(alice) gid=1001(developers)
```

Here:

```text
Primary Group = developers
```

---

## Q192. What are secondary groups?

**Answer:**

Secondary groups are additional groups that a user belongs to.

Example:

```text
User: Alice

Primary Group:
developers

Secondary Groups:
docker
sudo
```

Check using:

```bash
groups alice
```

---

## Q193. What is the difference between primary and secondary groups?

**Answer:**

```text
Primary Group
    ↓
Default group associated with the user

Secondary Groups
    ↓
Additional groups the user belongs to
```

A user can have multiple secondary groups.

---

# ➕ User Management

## Q194. How do you create a user?

**Answer:**

Use:

```bash
sudo useradd alice
```

To create a user with a home directory:

```bash
sudo useradd -m alice
```

---

## Q195. What is the difference between `useradd` and `adduser`?

**Answer:**

`useradd` is a lower-level command used to create users.

```bash
sudo useradd alice
```

`adduser` is generally a more interactive utility available on many Debian-based systems.

```bash
sudo adduser alice
```

`adduser` may guide you through additional configuration such as:

- Password
- Full name
- User information

---

## Q196. How do you set a user's password?

**Answer:**

Use:

```bash
sudo passwd alice
```

---

## Q197. How do you modify a user?

**Answer:**

Use:

```bash
sudo usermod
```

Example:

```bash
sudo usermod -s /bin/bash alice
```

This changes the user's login shell.

---

## Q198. How do you add a user to a secondary group?

**Answer:**

Use:

```bash
sudo usermod -aG developers alice
```

Where:

```text
-a → Append
-G → Supplementary / secondary group
```

Verify:

```bash
groups alice
```

---

## Q199. Why is the `-a` option important in `usermod -aG`?

**Answer:**

The `-a` option means **append**.

It ensures that the user is added to the new group without removing the user from existing supplementary groups.

Example:

```bash
sudo usermod -aG developers alice
```

Without `-a`, existing supplementary group memberships may be replaced.

---

## Q200. How do you remove a user from a group?

**Answer:**

One common command is:

```bash
sudo gpasswd -d alice developers
```

Verify:

```bash
groups alice
```

---

## Q201. How do you delete a user?

**Answer:**

Use:

```bash
sudo userdel alice
```

To also remove the user's home directory:

```bash
sudo userdel -r alice
```

⚠️ The `-r` option can permanently remove the user's home directory and data.

---

# 👥 Group Management

## Q202. How do you create a group?

**Answer:**

Use:

```bash
sudo groupadd developers
```

Verify:

```bash
getent group developers
```

---

## Q203. How do you rename a group?

**Answer:**

Use:

```bash
sudo groupmod -n programmers developers
```

This changes:

```text
developers
    ↓
programmers
```

---

## Q204. How do you delete a group?

**Answer:**

Use:

```bash
sudo groupdel developers
```

Make sure the group is no longer required before deleting it.

---

# 🛡️ sudo and Privileges

## Q205. What is `sudo`?

**Answer:**

`sudo` allows an authorized user to execute a command with elevated privileges.

Example:

```bash
sudo apt update
```

It provides elevated privileges for the specific command rather than requiring the user to operate as root all the time.

---

## Q206. Why is `sudo` preferred over logging in as root?

**Answer:**

Using `sudo` is generally safer because:

- Privileges can be limited
- Commands can be audited
- The user does not need to remain in a root shell
- Accidental administrative actions are reduced

It follows the principle of least privilege more closely.

---

## Q207. What is the difference between `sudo` and `su`?

**Answer:**

```text
sudo
 ↓
Run a specific command with elevated privileges

su
 ↓
Switch to another user account
```

Example:

```bash
sudo apt update
```

Switch to root:

```bash
su -
```

---

# 🧩 Scenario-Based Questions

## Q208. A user needs access to the `developers` group. What command would you use?

**Answer:**

```bash
sudo usermod -aG developers username
```

Then verify:

```bash
groups username
```

---

## Q209. A user was added to a group, but the group does not appear in the current session. What could be the reason?

**Answer:**

The current login session may not have refreshed the user's group membership.

The user may need to:

- Log out and log back in
- Start a new session
- Use an appropriate command such as `newgrp` when suitable

Verify membership using:

```bash
id username
```

---

## Q210. You need to create a user with a home directory. What command would you use?

**Answer:**

```bash
sudo useradd -m username
```

---

## Q211. You need to create a user and set a password. What commands can you use?

**Answer:**

```bash
sudo useradd -m alice
```

Then:

```bash
sudo passwd alice
```

Alternatively, on systems supporting it:

```bash
sudo adduser alice
```

---

## Q212. How would you check whether a user exists?

**Answer:**

You can use:

```bash
id username
```

Or:

```bash
getent passwd username
```

---

## Q213. How would you check whether a group exists?

**Answer:**

Use:

```bash
getent group groupname
```

---

## Q214. A user should have access to Docker without using `sudo` for every Docker command. What would you investigate?

**Answer:**

I would first check whether the system uses a `docker` group and whether the user is a member of it.

For example:

```bash
groups username
```

If appropriate:

```bash
sudo usermod -aG docker username
```

The user may need to start a new login session for the membership change to take effect.

I would also consider the security implications because membership in privileged groups can provide significant access.

---

## Q215. A user has UID 0 but is not named `root`. What does this mean?

**Answer:**

UID `0` represents the superuser identity.

A user account with UID `0` effectively has root-level privileges, regardless of the username.

This should be treated as a serious security concern unless intentionally configured.

---

## Q216. What happens if you delete a user with `userdel -r`?

**Answer:**

The user account is removed and the user's home directory and associated local mail files may also be removed.

Example:

```bash
sudo userdel -r alice
```

This should be used carefully because user data may be permanently deleted.

---

## Q217. Why should unused user accounts be removed or disabled?

**Answer:**

Unused accounts increase the attack surface.

Removing or disabling unnecessary accounts helps:

- Reduce unauthorized access
- Improve security
- Simplify account management
- Follow least privilege principles

---

## Q218. Why should `/etc/shadow` be protected?

**Answer:**

`/etc/shadow` contains sensitive password and authentication-related information.

Unauthorized access could help attackers attempt password cracking or other attacks.

Therefore, access should be restricted.

---

# 🔥 Advanced Interview Questions

## Q219. What is the relationship between UID and username?

**Answer:**

The username is a human-readable identity, while the UID is the numeric identity used internally by the Linux system.

Example:

```text
Username:
alice

UID:
1001
```

Linux processes and file ownership are ultimately associated with numeric IDs.

---

## Q220. What is the relationship between GID and group name?

**Answer:**

The group name is the human-readable name, while the GID is the numeric identifier used internally.

Example:

```text
Group:
developers

GID:
1001
```

---

## Q221. How does Linux identify file ownership?

**Answer:**

Linux associates files with:

```text
User ID (UID)
Group ID (GID)
```

When displayed using commands such as:

```bash
ls -l
```

the system typically shows the corresponding usernames and group names.

---

## Q222. What happens if a user is deleted but their files remain?

**Answer:**

The files may still exist and retain the numeric UID of the deleted user as the file owner.

The username may no longer resolve to that UID.

You can inspect numeric ownership using:

```bash
ls -ln
```

---

## Q223. What is the purpose of `getent`?

**Answer:**

`getent` retrieves entries from configured system databases.

Examples:

```bash
getent passwd username
```

```bash
getent group developers
```

It is useful for checking user and group information through the system's configured name service sources.

---

## Q224. What is the principle of least privilege in user management?

**Answer:**

The principle of least privilege means giving users only the access and privileges they need to perform their tasks.

For example:

```text
Normal User
    ↓
Normal Permissions

Administrative Task
    ↓
Use sudo when authorized

No Need for Root
    ↓
Do not grant Root Access
```

---

# ⚡ Rapid-Fire Revision

| Question | Answer |
|---|---|
| User identifier | UID |
| Group identifier | GID |
| Root UID | `0` |
| Current user | `whoami` |
| User identity | `id` |
| User groups | `groups` |
| Logged-in users | `who` |
| Detailed logged-in users | `w` |
| Usernames currently logged in | `users` |
| Basic user database | `/etc/passwd` |
| Password database | `/etc/shadow` |
| Group database | `/etc/group` |
| Create user | `useradd` |
| Interactive user creation | `adduser` |
| Modify user | `usermod` |
| Delete user | `userdel` |
| Create group | `groupadd` |
| Modify group | `groupmod` |
| Delete group | `groupdel` |
| Set password | `passwd` |
| Execute as authorized elevated user | `sudo` |
| Primary group | User's default group |
| Secondary groups | Additional groups |
| Check user existence | `id username` |
| Check group existence | `getent group groupname` |

---

# 🎯 Interview Checklist — Lesson 06

- [ ] Explain Linux users
- [ ] Explain Linux groups
- [ ] Explain UID
- [ ] Explain GID
- [ ] Explain root user
- [ ] Explain UID 0
- [ ] Use `whoami`
- [ ] Use `id`
- [ ] Use `who`
- [ ] Use `w`
- [ ] Use `users`
- [ ] Use `groups`
- [ ] Explain `/etc/passwd`
- [ ] Explain `/etc/shadow`
- [ ] Explain `/etc/group`
- [ ] Explain primary groups
- [ ] Explain secondary groups
- [ ] Create users with `useradd`
- [ ] Understand `adduser`
- [ ] Modify users with `usermod`
- [ ] Add users to groups
- [ ] Remove users from groups
- [ ] Delete users safely
- [ ] Create groups
- [ ] Modify groups
- [ ] Delete groups
- [ ] Understand `sudo`
- [ ] Understand `sudo` vs `su`
- [ ] Understand least privilege
- [ ] Solve user-management scenarios
- [ ] Solve group-management scenarios

---

# 🧠 Quick Interview Revision

```text
USER
  │
  ├── UID
  │
  ├── Primary Group
  │
  ├── Secondary Groups
  │
  └── Home Directory

GROUP
  │
  └── GID

ROOT
  │
  └── UID 0

/etc/passwd
  │
  └── User Account Information

/etc/shadow
  │
  └── Password / Authentication Information

/etc/group
  │
  └── Group Information

sudo
  │
  └── Controlled Elevated Privileges
```

---

# 🏆 Lesson 06 Interview Goal

By the end of this section, you should be able to confidently answer:

> **"How does Linux manage users, groups, identities, and privileges?"**

A strong answer:

```text
Linux identifies users using UIDs and groups using GIDs.
User account information is maintained through system databases
such as /etc/passwd, while password-related information is stored
in /etc/shadow and group information in /etc/group.

Users can have a primary group and multiple secondary groups.
Administrators can create and manage users and groups using commands
such as useradd, usermod, userdel, groupadd, groupmod, and groupdel.

For administrative operations, authorized users can use sudo to
execute commands with elevated privileges while following the
principle of least privilege.
```

---

## 🔗 Related Resources

📖 [Lesson 06 — Linux Users & Groups](../levels/level-02-file-system/06-linux-users-and-groups.md)

🖼️ [Linux Users & Groups Diagram](../assets/diagrams/linux-users-and-groups.md)

🧪 [Linux Users & Groups Lab](../labs/06-linux-users-and-groups-lab.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 06 Interview Preparation**

> *Understand identities. Manage users. Control privileges. Secure the system.*

# 🐧 Linux Quest — Level 02
# Linux File System — Interview Preparation

> Common Linux File System interview questions with concise, interview-ready answers.

---

## 🟢 Basic Questions

### 1. What is a file system in Linux?

A file system is the method Linux uses to organize, store, manage, and access files and directories on storage devices.

Examples include:

- ext4
- XFS
- Btrfs
- FAT32
- NTFS

---

### 2. What is the Linux file system hierarchy?

Linux follows a hierarchical directory structure starting from the root directory `/`.

Important directories include:

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

# 🐧 Linux Quest — Level 02
# Chapter 08: Linux File Permissions & Ownership — Interview Preparation

---

## 1. What are Linux File Permissions?

Linux file permissions control who can read, write, or execute files and directories.

Permissions are assigned to three categories:

- User (Owner)
- Group
- Others

The three basic permissions are:

- `r` → Read
- `w` → Write
- `x` → Execute

---

## 2. What do r, w, and x mean?

### Read (r)

For a file:
- Allows reading the contents.

For a directory:
- Allows listing its contents.

### Write (w)

For a file:
- Allows modifying the contents.

For a directory:
- Allows creating, deleting, and renaming entries, subject to other permission checks.

### Execute (x)

For a file:
- Allows executing the file if it is executable.

For a directory:
- Allows entering or traversing the directory.

---

## 3. What are User, Group, and Others?

Linux permissions are divided into three classes:

- User (u) → Owner of the file
- Group (g) → Users belonging to the file's group
- Others (o) → Everyone else

Example:

-rwxr-xr--

Breakdown:

User    → rwx
Group   → r-x
Others  → r--

---

## 4. How do you read ls -l output?

Command:

ls -l

Example:

-rwxr-xr-- 1 rishika developers 1200 Jul 30 script.sh

Breakdown:

-rwxr-xr--  → Permissions
1           → Hard link count
rishika     → Owner
developers  → Group
1200        → File size
Jul 30      → Modification date
script.sh   → File name

---

## 5. What is chmod?

`chmod` stands for Change Mode.

It is used to change file and directory permissions.

Example:

chmod 755 script.sh

This gives:

User    → rwx
Group   → r-x
Others  → r-x

---

## 6. What are Numeric Permissions?

Linux permissions have numeric values:

Read      = 4
Write     = 2
Execute   = 1

Examples:

rwx = 4 + 2 + 1 = 7
rw- = 4 + 2 + 0 = 6
r-x = 4 + 0 + 1 = 5
r-- = 4 + 0 + 0 = 4
-w- = 0 + 2 + 0 = 2
--x = 0 + 0 + 1 = 1
--- = 0 + 0 + 0 = 0

---

## 7. What does chmod 755 mean?

Command:

chmod 755 file

Meaning:

User    → rwx → 7
Group   → r-x → 5
Others  → r-x → 5

Therefore:

755 = rwxr-xr-x

---

## 8. What does chmod 644 mean?

Command:

chmod 644 file

Meaning:

User    → rw- → 6
Group   → r-- → 4
Others  → r-- → 4

Therefore:

644 = rw-r--r--

It is commonly used for normal readable files.

---

## 9. What does chmod 600 mean?

Command:

chmod 600 secret.txt

Meaning:

User    → rw-
Group   → ---
Others  → ---

Therefore:

600 = rw-------

This is useful for private files.

---

## 10. What is Symbolic chmod?

Symbolic permissions use:

u → User
g → Group
o → Others
a → All

Operators:

+ → Add permission
- → Remove permission
= → Set exact permission

Examples:

chmod u+x script.sh

Add execute permission for the owner.

chmod g+w file.txt

Add write permission for the group.

chmod o-r file.txt

Remove read permission from others.

chmod a+r file.txt

Add read permission for everyone.

---

## 11. Difference Between Numeric and Symbolic chmod

Numeric:

chmod 755 script.sh

Symbolic:

chmod u+x script.sh

Numeric permissions use values such as 755, 644, and 600.

Symbolic permissions use u, g, o, and a with +, -, and =.

---

## 12. What is chown?

`chown` stands for Change Owner.

It changes the owner of a file or directory.

Example:

sudo chown rishika notes.txt

To change owner and group:

sudo chown rishika:developers notes.txt

---

## 13. What is chgrp?

`chgrp` stands for Change Group.

It changes the group ownership of a file or directory.

Example:

sudo chgrp developers notes.txt

---

## 14. Difference Between chmod, chown, and chgrp

chmod → Changes permissions

chown → Changes owner

chgrp → Changes group ownership

Examples:

chmod 644 file.txt

chown user file.txt

chgrp developers file.txt

---

## 15. What is the Difference Between File Owner and Group?

The owner is the user associated with the file.

The group is associated with a set of users who can share access according to group permissions.

Example:

-rw-r--r-- 1 rishika developers file.txt

Owner → rishika
Group → developers

---

## 16. What are Directory Permissions?

Directory permissions have different meanings:

r → List directory contents
w → Create, delete, or rename entries
x → Enter or traverse the directory

Without x permission, a user generally cannot access files inside a directory.

---

## 17. What is umask?

`umask` controls which permission bits are removed from the default permissions of newly created files and directories.

Check current umask:

umask

Typical default permission bases:

Files       → 666
Directories → 777

The umask removes permission bits from these defaults.

---

## 18. What is sudo?

`sudo` allows an authorized user to execute commands with elevated privileges.

Example:

sudo apt update

Another example:

sudo chown root file.txt

It should be used carefully because commands run with elevated privileges.

---

## 19. What is SUID?

SUID stands for Set User ID.

When SUID is set on an executable file, the program runs with the privileges of the file owner.

Numeric value:

4000

Example:

chmod 4755 program

The permission may appear as:

-rwsr-xr-x

SUID should be carefully managed because it can create security risks if misused.

---

## 20. What is SGID?

SGID stands for Set Group ID.

For executable files, SGID can cause the process to run with the file's group privileges.

For directories, newly created files generally inherit the directory's group ownership.

Numeric value:

2000

Example:

chmod 2755 directory

---

## 21. What is the Sticky Bit?

The Sticky Bit is commonly used on shared directories.

It restricts users from deleting or renaming files owned by other users in the directory, subject to directory ownership and privileges.

Numeric value:

1000

Example:

chmod 1777 shared

The permission may appear as:

drwxrwxrwt

A common example is:

/tmp

---

## 22. Difference Between SUID, SGID, and Sticky Bit

SUID
→ Program runs with file owner's privileges
→ Numeric value: 4000

SGID
→ Program can run with file group's privileges
→ Directory can provide group inheritance
→ Numeric value: 2000

Sticky Bit
→ Used mainly on shared directories
→ Restricts deletion of files owned by other users
→ Numeric value: 1000

---

## 23. Why is chmod 777 Dangerous?

Command:

chmod 777 file

gives:

User    → rwx
Group   → rwx
Others  → rwx

Everyone gets read, write, and execute permissions.

This can allow unauthorized users to modify or execute files.

Instead, follow the Principle of Least Privilege.

Give users only the permissions they actually need.

---

## 24. What is the Principle of Least Privilege?

The Principle of Least Privilege means giving users and processes only the minimum permissions required to perform their tasks.

Example:

Instead of:

chmod 777 file

Use the minimum required permission, such as:

chmod 644 file

or:

chmod 600 secret.txt

---

## 25. How do you Troubleshoot "Permission Denied"?

First check the current user:

whoami

Check user and group information:

id

Check file permissions and ownership:

ls -l file.txt

Check permissions along the complete path:

namei -l /path/to/file.txt

Then ask:

1. Am I the owner?
2. Am I part of the owning group?
3. What permissions does the owner have?
4. What permissions does the group have?
5. What permissions do others have?
6. Do I have execute permission on parent directories?
7. Do I need elevated privileges?

---

# 🎯 Scenario-Based Interview Questions

## Scenario 1: Script Permission Denied

You run:

./script.sh

and get:

Permission denied

### Answer:

First check permissions:

ls -l script.sh

If execute permission is missing:

chmod +x script.sh

Then run:

./script.sh

---

## Scenario 2: Private File

You want a file to be readable and writable only by its owner.

### Answer:

chmod 600 file.txt

Permissions:

User    → rw-
Group   → ---
Others  → ---

---

## Scenario 3: Private Directory

You want only the owner to access a directory.

### Answer:

chmod 700 private/

Permissions:

User    → rwx
Group   → ---
Others  → ---

---

## Scenario 4: User Cannot Enter Directory

A user can see a directory but cannot enter it.

Which permission might be missing?

### Answer:

Execute (x) permission on the directory may be missing.

The x permission allows a user to traverse/access a directory.

---

## Scenario 5: User Cannot List Directory Contents

A user can access a directory but cannot list its contents.

Which permission might be missing?

### Answer:

Read (r) permission on the directory may be missing.

---

## Scenario 6: Developer Cannot Modify a File

A developer needs to modify a file but receives:

Permission denied

### Answer:

Check:

ls -l file.txt

Then check:

- File owner
- File group
- User's group membership
- Group permissions

Use:

id username

If appropriate, ownership or permissions may need to be changed.

---

## Scenario 7: Explain This Permission

-rwxr-x---

### Answer:

User:

rwx = 7

Group:

r-x = 5

Others:

--- = 0

Numeric permission:

750

Therefore:

750 = rwxr-x---

---

## Scenario 8: Explain This Permission

-rw-------

### Answer:

User:

rw- = 6

Group:

--- = 0

Others:

--- = 0

Numeric permission:

600

Therefore:

600 = rw-------

---

## Scenario 9: Give Execute Permission to Owner

How do you give execute permission only to the owner?

### Answer:

chmod u+x file

---

## Scenario 10: Remove Write Permission from Others

### Answer:

chmod o-w file

---

## Scenario 11: Give Read Permission to Everyone

### Answer:

chmod a+r file

---

## Scenario 12: Change File Owner

### Answer:

sudo chown username file.txt

---

## Scenario 13: Change Group Ownership

### Answer:

sudo chgrp groupname file.txt

---

## Scenario 14: Change Owner and Group Together

### Answer:

sudo chown username:groupname file.txt

---

# ⚡ Rapid Fire Revision

r = Read = 4
w = Write = 2
x = Execute = 1

u = User
g = Group
o = Others
a = All

chmod = Change permissions
chown = Change owner
chgrp = Change group
umask = Controls default permission removal
sudo = Run command with elevated privileges

SUID = 4000
SGID = 2000
Sticky Bit = 1000

755 = rwxr-xr-x
644 = rw-r--r--
600 = rw-------
700 = rwx------
750 = rwxr-x---

777 = rwxrwxrwx

---

# 🧠 Important Commands Cheat Sheet

ls -l
→ View permissions and ownership.

chmod 755 file
→ Set numeric permissions.

chmod u+x file
→ Add execute permission for owner.

chmod g+w file
→ Add write permission for group.

chmod o-r file
→ Remove read permission from others.

chown user file
→ Change owner.

chown user:group file
→ Change owner and group.

chgrp group file
→ Change group.

umask
→ View current umask.

whoami
→ Show current user.

id
→ Show user ID, group ID, and group memberships.

namei -l /path/to/file
→ Inspect permissions along a path.

---

# 🏆 Interview Tip

When answering a Linux permissions question in an interview, explain:

Concept → Command → Example

Example Answer:

`chmod` is used to modify file permissions. Linux permissions are divided into User, Group, and Others, with Read, Write, and Execute permissions.

For example:

chmod 755 script.sh

This gives the owner read, write, and execute permissions, while the group and others get read and execute permissions.

---

# ✅ Chapter 08 Interview Preparation Checklist

- [ ] Understand Linux permissions
- [ ] Understand Read, Write, Execute
- [ ] Understand User, Group, Others
- [ ] Read ls -l
- [ ] Understand numeric permissions
- [ ] Understand symbolic permissions
- [ ] Know chmod
- [ ] Know chown
- [ ] Know chgrp
- [ ] Understand umask
- [ ] Understand sudo
- [ ] Understand SUID
- [ ] Understand SGID
- [ ] Understand Sticky Bit
- [ ] Troubleshoot Permission Denied
- [ ] Understand Least Privilege
- [ ] Practice scenario-based questions

---

# 🏁 Chapter 08 Status

Linux File Permissions & Ownership

Theory              → ⬜
Diagram              → ⬜
Interview Prep       → 🟢 Complete
Hands-on Lab         → ⬜
README               → ⬜
Git Commits          → ⬜

# 🐧 Linux Interview Preparation — Lesson 09
# 🔗 Linux File Links: Hard Links & Symbolic Links

> This chapter covers Inodes, Hard Links, Symbolic Links, Link Counts, Broken Symlinks, Filesystem Boundaries, and Interview Questions.

---

# 1. What is a Link in Linux?

A link in Linux is a way to create another reference to a file.

Linux mainly provides two types of links:

1. Hard Link
2. Symbolic Link (Soft Link)

                    LINUX LINKS
                         │
                ┌────────┴────────┐
                │                 │
                ▼                 ▼
           HARD LINK        SYMBOLIC LINK
                │                 │
                ▼                 ▼
           Same Inode        Stores Path
                │                 │
                ▼                 ▼
           Same Data         Target File

---

# 2. What is an Inode?

An inode is a data structure maintained by the Linux filesystem that stores metadata about a file.

An inode generally contains:

- File type
- File permissions
- Owner UID
- Group GID
- File size
- Timestamps
- Number of hard links
- Pointers to data blocks

An inode does NOT normally store the filename.

The filename is stored in a directory entry that maps the filename to the inode number.

    Filename
        │
        ▼
    Directory Entry
        │
        ▼
    Inode
        │
        ├── Permissions
        ├── Owner
        ├── Group
        ├── Size
        ├── Timestamps
        ├── Link Count
        │
        ▼
    Data Blocks

### Interview Answer

> An inode is a filesystem data structure that stores metadata and pointers to a file's data blocks. The filename itself is stored in the directory entry, which maps the filename to the inode.

---

# 3. What is a Hard Link?

A hard link is an additional directory entry that points directly to the same inode as the original file.

    original.txt ───────┐
                        │
                        ▼
                    Inode #1234
                        │
                        ▼
                    File Data
                        ▲
                        │
    hardlink.txt ───────┘

Create a hard link:

    ln original.txt hardlink.txt

Check inode numbers:

    ls -li original.txt hardlink.txt

Both files should show the same inode number.

### Important Point

A hard link is NOT a copy of the file.

Both filenames point to the same underlying inode and data.

---

# 4. What is a Symbolic Link?

A symbolic link, also called a soft link, is a special file that stores the path to another file or directory.

    symlink.txt
          │
          ▼
    "original.txt"
          │
          ▼
    original.txt
          │
          ▼
        Inode
          │
          ▼
      File Data

Create a symbolic link:

    ln -s original.txt symlink.txt

View the link:

    ls -l symlink.txt

Example:

    symlink.txt -> original.txt

### Important Point

A symbolic link has its own inode and stores the path of the target.

---

# 5. Hard Link vs Symbolic Link

| Feature | Hard Link | Symbolic Link |
|---|---|---|
| Points to | Inode | File path |
| Inode | Same as target | Different inode |
| File data | Same | Accesses target data |
| Can point to directory | Normally no | Yes |
| Cross filesystem | Generally no | Yes |
| Can become broken | No | Yes |
| Target deleted | Link still works if another hard link exists | Link becomes broken |
| Command | ln | ln -s |
| Inode check | Same inode | Different inode |

### Easy Way to Remember

    HARD LINK
        ↓
    Same Inode
        ↓
    Same Data

    SYMBOLIC LINK
        ↓
    Stores Path
        ↓
    Points to Target

---

# 6. What Happens When You Delete the Original File?

Suppose:

    original.txt ───────┐
                        ▼
                    Inode #1234
                        ▲
                        │
    hardlink.txt ───────┘

Now run:

    rm original.txt

Result:

    original.txt ❌

    hardlink.txt
          │
          ▼
    Inode #1234
          │
          ▼
      File Data

The hard link still works.

Why?

Because the inode still has another directory entry pointing to it.

The actual data is removed only when:

1. The hard link count becomes zero.
2. No process is keeping the file open.

### Interview Answer

> Deleting the original filename does not delete the actual file data if another hard link still exists. The inode remains accessible through the remaining hard link.

---

# 7. What Happens When You Delete the Target of a Symbolic Link?

Suppose:

    symlink.txt
          │
          ▼
    original.txt
          │
          ▼
      File Data

Delete the target:

    rm original.txt

Now:

    symlink.txt
          │
          ▼
    original.txt ❌
          │
          X
    Target Missing

The symbolic link becomes a broken or dangling symlink.

### Interview Answer

> A symbolic link stores a path, not the actual inode reference. If its target is deleted or moved, the symbolic link becomes dangling or broken.

---

# 8. What is a Broken or Dangling Symlink?

A broken symbolic link is a symbolic link whose target path no longer exists.

Example:

    symlink.txt
          │
          ▼
    /home/user/original.txt
          │
          X
    File does not exist

Find broken symlinks:

    find . -xtype l

---

# 9. How Do You Check Whether Two Files Are Hard Links?

Use inode numbers:

    ls -li file1 file2

Example output:

    12345 -rw-r--r-- 2 user user 100 Jul 30 file1
    12345 -rw-r--r-- 2 user user 100 Jul 30 file2

Both have inode:

    12345

Therefore, they are hard links to the same underlying file.

### Interview Answer

> I can compare the inode numbers using ls -li. If two filenames have the same inode number on the same filesystem, they refer to the same underlying file through hard links.

---

# 10. How Do You Identify a Symbolic Link?

Use:

    ls -l

Example:

    lrwxrwxrwx 1 user user 12 Jul 30 symlink.txt -> original.txt

The first character is:

    l

which indicates a symbolic link.

You can also use:

    readlink symlink.txt

Output:

    original.txt

---

# 11. What Does the First Character in ls -l Mean?

Example:

    lrwxrwxrwx

The first character represents the file type.

Common types:

    -   Regular file
    d   Directory
    l   Symbolic link
    c   Character device
    b   Block device
    s   Socket
    p   Named pipe

Examples:

    -rw-r--r--   → Regular file
    drwxr-xr-x   → Directory
    lrwxrwxrwx   → Symbolic link

---

# 12. Why Do Hard Links Share the Same Inode?

A hard link is simply another directory entry pointing to the same inode.

    Directory Entry 1
          │
          ▼
      Inode #100
          │
          ▼
      File Data
          ▲
          │
    Directory Entry 2

Therefore:

    file1 ──► Inode 100
    file2 ──► Inode 100

Both represent the same underlying file.

---

# 13. Why Can't Hard Links Usually Cross Filesystems?

An inode belongs to a specific filesystem.

A hard link directly references an inode.

Therefore, a hard link generally cannot point to an inode belonging to another filesystem.

    Filesystem A
         │
         ▼
      Inode 1234
         ▲
         │
      Hard Link
         │
         X
    Filesystem B

This may fail with:

    Invalid cross-device link

Symbolic links do not have this limitation because they store paths.

---

# 14. Can a Symbolic Link Cross Filesystems?

Yes.

A symbolic link stores a path.

For example:

    Filesystem A

    symlink.txt
          │
          │ /mnt/data/file.txt
          ▼

    Filesystem B

    file.txt

Because the symlink stores a pathname, it can point to a file located on another filesystem.

---

# 15. Can You Create Hard Links to Directories?

Normally, no.

Regular users cannot create hard links to directories.

This restriction helps prevent filesystem cycles and maintains filesystem consistency.

    Hard Link → Regular File ✅

    Hard Link → Directory ❌ Normally Not Allowed

The special entries:

    .
    ..

are filesystem-managed directory links and are not normal user-created hard links.

---

# 16. Can Symbolic Links Point to Directories?

Yes.

Example:

    ln -s /var/log logs

Now:

    logs
      │
      ▼
    /var/log

You can access the directory using:

    cd logs

Symbolic links can point to:

- Regular files
- Directories
- Other symbolic links
- Absolute paths
- Relative paths

---

# 17. Difference Between ln and ln -s

### ln

Creates a hard link by default.

    ln source target

Relationship:

    source ─────┐
                ▼
             Same Inode
                ▲
                │
    target ─────┘

### ln -s

Creates a symbolic link.

    ln -s source target

Relationship:

    target
       │
       ▼
    Path to source
       │
       ▼
    source

### Interview Answer

> ln creates a hard link by default, while ln -s creates a symbolic link.

---

# 18. What is Link Count?

The link count is the number of directory entries that reference an inode through hard links.

Example:

    original.txt ───────┐
                        │
    hardlink.txt ───────┼──► Inode #1234
                        │
    backup.txt ─────────┘

The inode link count is:

    3

Check using:

    ls -l

Example:

    -rw-r--r-- 3 user user 100 file.txt

The number 3 represents the hard link count.

---

# 19. What Happens to Link Count When a Hard Link Is Created?

Initially:

    original.txt
         │
         ▼
       Inode
    Link Count = 1

Create:

    ln original.txt hardlink.txt

Now:

    original.txt ───────┐
                        ▼
                    Inode
                Link Count = 2
                        ▲
                        │
    hardlink.txt ───────┘

The link count increases by one.

---

# 20. What Happens to Link Count When a Hard Link Is Deleted?

Suppose:

    original.txt ───────┐
                        ▼
                    Inode
                Link Count = 2
                        ▲
                        │
    hardlink.txt ───────┘

Run:

    rm hardlink.txt

Now:

    original.txt
         │
         ▼
       Inode
    Link Count = 1

The link count decreases by one.

When the link count reaches zero and no process has the file open, the filesystem can reclaim the inode and data blocks.

---

# 21. Hard Link Deletion vs File Data Deletion

Important concept:

    rm original.txt

does not necessarily mean:

    Delete File Data Immediately

Instead, it removes a directory entry.

Before:

    original.txt ───────┐
                        ▼
                    Inode
                Link Count = 2
                        ▲
                        │
    hardlink.txt ───────┘

After:

    rm original.txt

    original.txt ❌

    hardlink.txt
          │
          ▼
        Inode
    Link Count = 1
          │
          ▼
    File Data Still Exists

---

# 22. Removing a Symlink vs Removing Its Target

Suppose:

    symlink.txt
          │
          ▼
    original.txt

Run:

    rm symlink.txt

Result:

    symlink.txt ❌
    original.txt ✅

Only the symlink is removed.

The target remains.

If you run:

    rm original.txt

Result:

    original.txt ❌
    symlink.txt 💔

The symlink remains but becomes broken.

---

# 23. Absolute vs Relative Symbolic Links

A symbolic link can contain an absolute or relative path.

### Absolute Symlink

    ln -s /home/user/project/file.txt link.txt

The link points to:

    /home/user/project/file.txt

### Relative Symlink

    ln -s ../project/file.txt link.txt

The link uses a relative path.

### Interview Tip

Relative symbolic links can be useful when moving an entire directory structure because the relationship between files remains relative.

---

# 24. Common Commands for Links

Create hard link:

    ln source target

Create symbolic link:

    ln -s source target

List links:

    ls -l

Show inode numbers:

    ls -li

Show symlink target:

    readlink link

Resolve full symlink path:

    readlink -f link

Find symbolic links:

    find . -type l

Find broken symbolic links:

    find . -xtype l

View metadata:

    stat file

---

# 25. Common Interview Questions

## Q1. What is an inode?

### Answer

> An inode is a filesystem data structure that stores metadata about a file and pointers to its data blocks. It does not normally store the filename.

## Q2. What is a hard link?

### Answer

> A hard link is another directory entry that points to the same inode as an existing file. Both names refer to the same underlying file data.

## Q3. What is a symbolic link?

### Answer

> A symbolic link is a special file that stores the pathname of another file or directory.

## Q4. What happens if the original file is deleted but a hard link exists?

### Answer

> The hard link continues to work because it points to the same inode. The data remains accessible until the last hard link is removed and no process is keeping the file open.

## Q5. What happens if the target of a symbolic link is deleted?

### Answer

> The symbolic link becomes a broken or dangling symbolic link because its stored target path no longer exists.

## Q6. How do you identify a hard link?

### Answer

> Compare inode numbers using ls -li. If two filenames have the same inode number on the same filesystem, they are hard links to the same file.

## Q7. How do you identify a symbolic link?

### Answer

> Use ls -l. A symbolic link starts with l in the file type field and displays an arrow pointing to its target.

## Q8. Can hard links cross filesystems?

### Answer

> Generally no, because a hard link directly references an inode, and an inode belongs to a specific filesystem.

## Q9. Can symbolic links cross filesystems?

### Answer

> Yes. Symbolic links store paths, so the target can exist on another filesystem.

## Q10. Can hard links point to directories?

### Answer

> Normally no for regular users. Filesystem-managed directory links such as . and .. are special cases.

## Q11. Can symbolic links point to directories?

### Answer

> Yes. Symbolic links can point to both regular files and directories.

## Q12. What is a dangling symlink?

### Answer

> A dangling symlink is a symbolic link whose target path no longer exists.

## Q13. What is the difference between ln and ln -s?

### Answer

> ln creates a hard link by default, while ln -s creates a symbolic link.

## Q14. What is link count?

### Answer

> Link count represents the number of hard-link directory entries referencing an inode.

## Q15. What happens when the link count reaches zero?

### Answer

> When no hard links reference an inode and no process has the file open, the filesystem can reclaim the inode and associated data blocks.

---

# 26. Scenario-Based Interview Questions

## Scenario 1

You have:

    file.txt
    hard.txt

Both have the same inode number.

What does it mean?

### Answer

They are hard links to the same underlying file.

---

## Scenario 2

You delete file.txt, but hard.txt still exists.

What happens?

### Answer

hard.txt continues to work because it still references the same inode.

---

## Scenario 3

You have:

    link.txt -> file.txt

You delete file.txt.

What happens?

### Answer

link.txt becomes a dangling symbolic link.

---

## Scenario 4

You need a link to a directory.

Which link should you use?

### Answer

Use a symbolic link.

    ln -s directory link

---

## Scenario 5

You need a link across two filesystems.

Which type should you use?

### Answer

Use a symbolic link because hard links generally cannot cross filesystem boundaries.

---

## Scenario 6

You want to deploy multiple application versions and have one stable path point to the active version.

What would you use?

### Answer

A symbolic link.

Example:

    current -> releases/v3

When deploying v4:

    current -> releases/v4

This allows the application to use a stable path while changing the active version.

---

# 27. 🧪 Mini Practical Interview Task

Run the following commands:

    mkdir link-demo
    cd link-demo

Create a file:

    echo "Linux Quest" > original.txt

Create hard link:

    ln original.txt hardlink.txt

Create symbolic link:

    ln -s original.txt symlink.txt

Check:

    ls -li

Expected concept:

    original.txt  → Same inode
    hardlink.txt  → Same inode
    symlink.txt   → Different inode

Now delete original:

    rm original.txt

Check hard link:

    cat hardlink.txt

Expected:

    Linux Quest

Check symbolic link:

    cat symlink.txt

Expected:

    No such file or directory

Why?

    Hard Link
        ↓
    Same inode
        ↓
    Data still exists

    Symbolic Link
        ↓
    Target path deleted
        ↓
    Broken link

---

# 28. 🧠 Interview Cheat Sheet

    INODE
    ↓
    Stores file metadata
    ↓
    Does not normally store filename


    HARD LINK
    ↓
    Points to same inode
    ↓
    Same data
    ↓
    Same inode number
    ↓
    Usually same filesystem
    ↓
    Cannot normally point to directories
    ↓
    Survives deletion of another filename


    SYMBOLIC LINK
    ↓
    Stores target path
    ↓
    Different inode
    ↓
    Can point to files/directories
    ↓
    Can cross filesystems
    ↓
    Can become broken

---

# 29. ⭐ One-Line Answers for Rapid Revision

**What is an inode?**

> A filesystem structure containing file metadata and pointers to data blocks.

**What is a hard link?**

> Another filename pointing to the same inode.

**What is a symbolic link?**

> A special file storing the path of another file or directory.

**Hard link command?**

> ln source target

**Symbolic link command?**

> ln -s source target

**How to check inode?**

> ls -li

**How to check symbolic link?**

> ls -l

**Can hard links cross filesystems?**

> Generally no.

**Can symbolic links cross filesystems?**

> Yes.

**Can hard links point to directories?**

> Normally no for users.

**Can symbolic links point to directories?**

> Yes.

**What is a dangling symlink?**

> A symlink whose target no longer exists.

**What happens when a hard link is deleted?**

> The link count decreases; data remains if another hard link exists.

**What happens when a symlink target is deleted?**

> The symlink becomes broken.

---

# 30. 🎯 Interviewer Trap Questions

### Trap 1: Is a hard link a copy of a file?

❌ No.

A hard link is not a copy.

It is another directory entry pointing to the same inode.

### Trap 2: Does deleting the original filename always delete the file?

❌ No.

If hard links still exist, the file data remains accessible.

### Trap 3: Is a symbolic link the same as a shortcut in Windows?

Conceptually similar, but technically a Linux symbolic link is a filesystem object that stores a pathname.

### Trap 4: Do hard links have different inodes?

❌ No.

Hard links to the same file share the same inode.

### Trap 5: Does a symbolic link have an inode?

✅ Yes.

The symbolic link itself has its own inode, which is different from the target's inode.

### Trap 6: Can a symbolic link point to another symbolic link?

✅ Yes.

The system follows the chain until it reaches the final target or encounters an error.

---

# 31. 🏆 Final Interview Summary

                    LINUX FILE LINKS
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ▼                           ▼
        HARD LINK                  SYMBOLIC LINK
             │                           │
             ▼                           ▼
        SAME INODE                  OWN INODE
             │                           │
             ▼                           ▼
        SAME DATA                  STORES PATH
             │                           │
             ▼                           ▼
     Usually same FS              Can cross FS
             │                           │
             ▼                           ▼
    Survives other name          Can become broken
       being deleted             if target is deleted

---

# 🔥 Most Important Interview Points

1. Inode stores metadata, not normally the filename.
2. Hard links point to the same inode.
3. Symbolic links store a target path.
4. Hard links share the same inode number.
5. Symbolic links have their own inode.
6. Hard links generally cannot cross filesystems.
7. Symbolic links can cross filesystems.
8. Hard links normally cannot point to directories.
9. Symbolic links can point to directories.
10. Deleting one hard-link filename does not necessarily delete the data.
11. Deleting a symlink target makes the symlink dangling.
12. ln creates hard links by default.
13. ln -s creates symbolic links.
14. ls -li is useful for comparing inode numbers.
15. ls -l and readlink help inspect symbolic links.

---

# 🐧 Linux Quest — Lesson 09 Interview Prep

Topic: Linux File Links

Status:

🟢 Inodes — Complete
🟢 Hard Links — Complete
🟢 Symbolic Links — Complete
🟢 Link Count — Complete
🟢 Broken Symlinks — Complete
🟢 Filesystem Boundaries — Complete
🟢 Interview Questions — Complete
🟢 Scenario Questions — Complete
🟢 Practical Task — Complete
🟢 Rapid Revision — Complete

🚀 Lesson 09 Interview Preparation Complete!

# 💼 Linux File Permissions & Ownership — Interview Preparation

> Interview questions and answers covering Linux file permissions, ownership, chmod, chown, chgrp, umask, SUID, SGID, Sticky Bit, and Linux security.

---

# 1. What are Linux file permissions?

Linux file permissions control who can access a file or directory and what actions they can perform.

There are three main types of permissions:

    r → Read
    w → Write
    x → Execute

There are three main categories of users:

    User / Owner
    Group
    Others

Example:

    -rwxr-xr--

Meaning:

    Owner  → rwx
    Group  → r-x
    Others → r--

---

# 2. What do r, w, and x mean?

For files:

    r → Read file contents
    w → Modify file contents
    x → Execute the file

For directories:

    r → List directory contents
    w → Create, delete, or rename entries
    x → Enter or traverse the directory

Important:

Directory permissions behave differently from file permissions.

---

# 3. What are User, Group, and Others?

Linux permissions are divided into three categories:

    User (u)
        ↓
    File owner

    Group (g)
        ↓
    Users belonging to the file's group

    Others (o)
        ↓
    Everyone else

Example:

    -rwxr-xr--

    rwx → User
    r-x → Group
    r-- → Others

---

# 4. How do you check file permissions?

Use:

    ls -l

Example:

    ls -l file.txt

Output:

    -rw-r--r-- 1 rishika developers 100 file.txt

The first section represents permissions:

    -rw-r--r--

The next fields represent:

    Owner → rishika
    Group → developers

---

# 5. Explain the permission string -rwxr-xr--

Breakdown:

    - | rwx | r-x | r--
      |     |     |
      |     |     └── Others
      |     └──────── Group
      └────────────── Owner

Meaning:

    -    → Regular file
    rwx  → Owner has Read + Write + Execute
    r-x  → Group has Read + Execute
    r--  → Others have Read only

Numeric equivalent:

    rwx = 7
    r-x = 5
    r-- = 4

Therefore:

    754

---

# 6. What is chmod?

`chmod` stands for Change Mode.

It is used to change file and directory permissions.

Example:

    chmod 755 script.sh

This sets:

    Owner  → rwx
    Group  → r-x
    Others → r-x

Another example:

    chmod 600 secret.txt

This gives:

    Owner  → Read + Write
    Group  → No Access
    Others → No Access

---

# 7. What is the difference between symbolic and numeric chmod?

Numeric mode uses numbers:

    chmod 755 file.txt

Symbolic mode uses letters and operators:

    chmod u+x script.sh

Where:

    u → User
    g → Group
    o → Others
    a → All

Operators:

    + → Add permission
    - → Remove permission
    = → Set exact permission

Examples:

    chmod u+x script.sh
    chmod g-w file.txt
    chmod o+r file.txt
    chmod a+x script.sh

---

# 8. What do the numbers 4, 2, and 1 represent?

Linux uses numeric permission values:

    Read
      ↓
      4

    Write
      ↓
      2

    Execute
      ↓
      1

Permissions are added together.

Examples:

    rwx = 4 + 2 + 1 = 7

    rw- = 4 + 2 = 6

    r-x = 4 + 1 = 5

    r-- = 4

Therefore:

    755 = rwxr-xr-x

---

# 9. What does chmod 777 mean?

    chmod 777 file

Means:

    Owner  → rwx
    Group  → rwx
    Others → rwx

Everyone has full permissions.

This is generally considered insecure because any user can modify or execute the file.

Better practice:

Use the minimum permissions required.

This follows the:

    Principle of Least Privilege

---

# 10. What does chmod 755 mean?

    chmod 755 script.sh

Means:

    Owner  → rwx
    Group  → r-x
    Others → r-x

The owner can:

    Read
    Write
    Execute

Group and others can:

    Read
    Execute

This is commonly used for executable scripts and directories.

---

# 11. What does chmod 644 mean?

    chmod 644 file.txt

Means:

    Owner  → rw-
    Group  → r--
    Others → r--

The owner can read and modify the file.

Everyone else can only read it.

This is a common permission for regular files.

---

# 12. What does chmod 600 mean?

    chmod 600 secret.txt

Means:

    Owner  → rw-
    Group  → ---
    Others → ---

Only the owner can read and write the file.

It is commonly used for:

    Private files
    SSH keys
    Sensitive configuration files

---

# 13. What is the difference between file and directory permissions?

For a file:

    r → Read contents
    w → Modify contents
    x → Execute

For a directory:

    r → List contents
    w → Create/Delete/Rename entries
    x → Enter/Traverse directory

Example:

A directory with `r` but without `x` may allow listing names but not accessing the files inside.

A directory with `x` but without `r` may allow accessing known file names but not listing the directory contents.

---

# 14. What is file ownership in Linux?

Every file and directory has:

    Owner
    Group

Example:

    -rw-r--r-- 1 rishika developers file.txt

Here:

    Owner → rishika
    Group → developers

Permissions are then applied based on:

    Owner
    Group
    Others

---

# 15. What is chown?

`chown` stands for Change Owner.

It is used to change the ownership of a file or directory.

Example:

    sudo chown rishika file.txt

Change owner and group:

    sudo chown rishika:developers file.txt

Recursive:

    sudo chown -R rishika:developers project/

The `-R` option applies the change recursively.

---

# 16. What is chgrp?

`chgrp` stands for Change Group.

It changes the group ownership of a file or directory.

Example:

    sudo chgrp developers file.txt

This changes the group to:

    developers

---

# 17. What is the difference between chown and chgrp?

`chown`:

    Changes owner
    Can also change group

Example:

    chown user:group file

`chgrp`:

    Changes only group ownership

Example:

    chgrp group file

---

# 18. What is umask?

`umask` controls the default permissions assigned to newly created files and directories.

Check current umask:

    umask

Example:

    0022

Typical base permissions:

    Files       → 666
    Directories → 777

With umask `022`:

    New File:
    666 - 022 → 644

    New Directory:
    777 - 022 → 755

The exact calculation is permission-bit based rather than ordinary decimal subtraction, but this is a useful conceptual shortcut.

---

# 19. Why do newly created files usually not have execute permission?

Files typically start from a base permission of:

    666

This means:

    rw-rw-rw-

The execute bit is not included by default.

This is a security measure.

For example, a newly created text file should not automatically become executable.

Directories use a base of:

    777

Then `umask` removes permissions as configured.

---

# 20. What is SUID?

SUID stands for:

    Set User ID

When SUID is set on an executable file, the program runs with the privileges of the file owner rather than the privileges of the user who launched it.

Example permission:

    -rwsr-xr-x

The `s` in the owner's execute position represents SUID.

Set SUID:

    chmod u+s file

Numeric form:

    chmod 4755 file

Security note:

SUID executables should be carefully audited because vulnerabilities in privileged programs can create security risks.

---

# 21. What is SGID?

SGID stands for:

    Set Group ID

For executable files:

The program runs with the privileges of the file's group.

For directories:

New files and directories created inside inherit the directory's group ownership.

Set SGID:

    chmod g+s directory/

Numeric form:

    chmod 2775 directory/

Example:

    drwxrwsr-x

The `s` in the group execute position represents SGID.

---

# 22. What is Sticky Bit?

Sticky Bit is commonly used on shared directories.

It restricts users from deleting or renaming files owned by other users in the directory, even when the directory is writable by everyone.

Example:

    drwxrwxrwt

The final `t` represents Sticky Bit.

Set Sticky Bit:

    chmod +t shared/

Numeric form:

    chmod 1777 shared/

A common example is:

    /tmp

---

# 23. What are SUID, SGID, and Sticky Bit?

Linux has three major special permission bits:

    SUID
      ↓
    4
      ↓
    Execute with file owner's privileges

    SGID
      ↓
    2
      ↓
    Execute with group privileges
    or inherit group on directories

    Sticky Bit
      ↓
    1
      ↓
    Restrict deletion in shared directories

Numeric examples:

    4755 → SUID + 755
    2775 → SGID + 775
    1777 → Sticky Bit + 777

---

# 24. What is the difference between SUID and SGID?

SUID:

    Uses the file owner's privileges.

SGID:

    Uses the file group's privileges.

For directories:

    SGID causes new files and directories
    to inherit the directory's group.

---

# 25. Why is /tmp usually configured with Sticky Bit?

`/tmp` is a shared writable directory.

Many users and processes may create files there.

Without Sticky Bit:

One user could potentially delete or rename another user's files if directory write permissions allowed it.

With Sticky Bit:

Users generally can delete only:

    Their own files
    Or files they otherwise have authority to manage

Typical permission:

    drwxrwxrwt

---

# 26. What is the Principle of Least Privilege?

The Principle of Least Privilege means:

A user or process should receive only the minimum permissions required to perform its task.

Bad practice:

    chmod 777 file

Better:

    chmod 600 secret.txt

Or:

    chmod 755 script.sh

The goal is:

    Minimum Access
          ↓
    Lower Security Risk

---

# 27. What does Permission Denied mean?

A `Permission denied` error usually means the current user does not have the required permission.

Possible causes:

    Wrong owner
    Wrong group
    Missing read permission
    Missing write permission
    Missing execute permission
    Parent directory lacks execute permission
    Filesystem mounted read-only
    ACL restrictions
    SELinux/AppArmor restrictions

Useful commands:

    ls -l file
    ls -ld directory
    whoami
    id
    stat file
    namei -l /path/to/file

---

# 28. How do you troubleshoot Permission Denied?

Follow this process:

    Permission Denied
          │
          ▼
    Check current user
          │
          ▼
    whoami
          │
          ▼
    Check ownership
          │
          ▼
    ls -l
          │
          ▼
    Check group membership
          │
          ▼
    id
          │
          ▼
    Check permissions
          │
          ▼
    Check parent directory
          │
          ▼
    Check ACL / SELinux
          │
          ▼
    Fix only required permission

Do not immediately use:

    chmod 777

Always understand the actual cause first.

---

# 29. Can a user delete a file if they do not have write permission on the file?

Yes.

File deletion is controlled mainly by the permissions of the parent directory, not the file itself.

For example:

    Directory:
    rwx

A user may be able to delete a file even if the file itself is:

    r--

However, Sticky Bit can restrict deletion in shared directories.

---

# 30. Can you modify a file without having write permission on the file?

Normally, no.

To modify a file, the user generally needs write permission on the file.

However, other mechanisms such as:

    Root privileges
    ACLs
    Capabilities
    Application-specific behavior

may affect access.

---

# 31. Can you access a file inside a directory without execute permission on the directory?

Normally, no.

The directory's execute (`x`) permission is required to traverse the directory.

For example:

    /home/user/project/file.txt

You need execute permission on the relevant directories in the path to access the file.

Use:

    namei -l /home/user/project/file.txt

to inspect permissions along the path.

---

# 32. What is the difference between chmod 755 and chmod 775?

`755`:

    Owner  → rwx
    Group  → r-x
    Others → r-x

`775`:

    Owner  → rwx
    Group  → rwx
    Others → r-x

Difference:

    755 → Group cannot write

    775 → Group can write

`775` is useful for shared project directories where members of the same group need write access.

---

# 33. What is the difference between chmod 644 and chmod 600?

`644`:

    Owner  → rw-
    Group  → r--
    Others → r--

`600`:

    Owner  → rw-
    Group  → ---
    Others → ---

Therefore:

    644 → Everyone can read

    600 → Only owner can read/write

Use `600` for sensitive files.

---

# 34. What is the difference between chmod 700 and chmod 755?

`700`:

    Owner  → rwx
    Group  → ---
    Others → ---

`755`:

    Owner  → rwx
    Group  → r-x
    Others → r-x

Therefore:

    700 → Private

    755 → Publicly accessible for read/execute

---

# 35. What does chmod 000 do?

    chmod 000 file

Removes all permissions:

    Owner  → ---
    Group  → ---
    Others → ---

No normal user permission is granted.

Root or other privileged mechanisms may still access the file.

Restore permissions with:

    chmod 644 file

or the required permission mode.

---

# 36. How do you make a file executable?

Use:

    chmod +x script.sh

Or:

    chmod u+x script.sh

Then run:

    ./script.sh

Check:

    ls -l script.sh

Expected:

    -rwx...

---

# 37. How do you remove execute permission?

Use:

    chmod -x script.sh

Or:

    chmod u-x script.sh

This removes execute permission according to the symbolic target.

---

# 38. What is the difference between `ls -l` and `ls -ld`?

`ls -l`:

Displays information about files and lists directory contents.

Example:

    ls -l directory/

`ls -ld`:

Displays information about the directory itself.

Example:

    ls -ld directory/

This is useful when you want to inspect directory permissions instead of the files inside it.

---

# 39. What is stat?

`stat` provides detailed information about a file.

Use:

    stat file.txt

It can show:

    File type
    Size
    Permissions
    Owner
    Group
    Inode
    Access time
    Modification time
    Change time

---

# 40. What is an inode?

An inode is a data structure used by Linux filesystems to store metadata about a file.

It contains information such as:

    File type
    Permissions
    Owner
    Group
    File size
    Timestamps
    Link count
    Pointers to data blocks

The filename itself is stored in the directory entry, which maps the name to the inode.

---

# 41. What happens when you run chmod?

When you execute:

    chmod 755 file.txt

Linux changes the permission bits associated with the file's metadata.

It does not change:

    File contents
    File name
    File size

It changes access permissions.

---

# 42. Does chmod change file ownership?

No.

`chmod` changes:

    Permissions

`chown` changes:

    Owner

`chgrp` changes:

    Group

Remember:

    chmod
      ↓
    Permissions

    chown
      ↓
    Owner

    chgrp
      ↓
    Group

---

# 43. What is the security risk of chmod 777?

`chmod 777` gives everyone:

    Read
    Write
    Execute

This can allow unauthorized users to:

    Modify files
    Delete content
    Replace scripts
    Inject malicious code

It violates the Principle of Least Privilege.

Therefore:

Avoid using `777` unless there is a specific, well-understood reason.

---

# 44. What is a secure permission for a private file?

A common choice is:

    chmod 600 secret.txt

This gives:

    Owner → Read + Write
    Group → No Access
    Others → No Access

For a private directory:

    chmod 700 private/

---

# 45. What permissions are commonly used for SSH private keys?

SSH private keys are commonly protected with:

    chmod 600 ~/.ssh/id_rsa

or an equivalent restrictive permission.

The exact expected permissions can depend on the SSH implementation and key type, but private keys should not be broadly readable.

---

# 46. What is the difference between permissions and ownership?

Ownership answers:

    Who owns this file?

Permissions answer:

    What can the owner, group, and others do?

Example:

    Owner = rishika
    Group = developers

Permissions:

    Owner  → rwx
    Group  → r-x
    Others → r--

Both ownership and permissions work together to control access.

---

# 47. What is an ACL?

ACL stands for:

    Access Control List

ACLs provide more fine-grained permissions than traditional User / Group / Others permissions.

For example, you can give a specific user additional access without changing the main owner or group.

Useful commands:

    getfacl file.txt

    setfacl -m u:username:r file.txt

ACLs are useful when standard Linux permission bits are not sufficient.

---

# 48. What is the difference between traditional permissions and ACLs?

Traditional permissions provide access control for:

    Owner
    Group
    Others

ACLs allow more detailed rules for:

    Specific users
    Specific groups

Therefore:

Traditional permissions → Simple access control

ACLs → Fine-grained access control

---

# 49. What is a practical example of SGID?

Suppose a development team has:

    /project

The directory belongs to:

    developers

Set SGID:

    chmod 2775 /project

Now new files created inside the directory can inherit the `developers` group.

This helps teams collaborate without manually changing group ownership for every file.

---

# 50. Scenario-Based Interview Question

### Scenario:

You have a shared project directory:

    /project

Requirements:

    Owner → Full Access
    Group → Full Access
    Others → Read + Execute

What permission should you use?

Answer:

    chmod 775 /project

Permissions:

    Owner  → rwx
    Group  → rwx
    Others → r-x

---

# 51. Scenario-Based Interview Question

### Scenario:

You have a secret configuration file.

Only the owner should read and modify it.

What permission should you use?

Answer:

    chmod 600 config.txt

Permissions:

    Owner  → rw-
    Group  → ---
    Others → ---

---

# 52. Scenario-Based Interview Question

### Scenario:

A script should be executable by everyone, but only the owner should modify it.

What permission should you use?

Answer:

    chmod 755 script.sh

Permissions:

    Owner  → rwx
    Group  → r-x
    Others → r-x

---

# 53. Scenario-Based Interview Question

### Scenario:

Multiple users need to write to a shared directory, but users should not delete each other's files.

What should you use?

Answer:

    Sticky Bit

Example:

    chmod 1777 shared/

This creates:

    drwxrwxrwt

The Sticky Bit restricts deletion or renaming of files by users who do not own them.

---

# 54. Scenario-Based Interview Question

### Scenario:

All files created inside a shared project directory should automatically inherit the project's group.

What should you use?

Answer:

    SGID

Example:

    chmod g+s project/

Or:

    chmod 2775 project/

This helps maintain consistent group ownership.

---

# 55. Scenario-Based Interview Question

### Scenario:

A user gets Permission Denied while accessing:

    /home/user/project/file.txt

What would you check?

Answer:

Check:

    whoami

Then:

    id

Then:

    ls -l /home/user/project/file.txt

Check directory permissions:

    ls -ld /home/user
    ls -ld /home/user/project

Check every directory in the path:

    namei -l /home/user/project/file.txt

Also check:

    ACLs
    SELinux
    AppArmor
    Read-only filesystem

Do not immediately use `chmod 777`.

---

# 56. Quick Interview Revision

    r = Read = 4

    w = Write = 2

    x = Execute = 1

    chmod
        ↓
    Change Permissions

    chown
        ↓
    Change Owner

    chgrp
        ↓
    Change Group

    umask
        ↓
    Default Permissions

    SUID
        ↓
    File Owner Privileges

    SGID
        ↓
    Group Privileges / Group Inheritance

    Sticky Bit
        ↓
    Restrict Deletion in Shared Directories

---

# 57. 📊 Important Permission Values

| Permission | Numeric | Meaning |
|---|---:|---|
| `---` | 0 | No permission |
| `--x` | 1 | Execute |
| `-w-` | 2 | Write |
| `-wx` | 3 | Write + Execute |
| `r--` | 4 | Read |
| `r-x` | 5 | Read + Execute |
| `rw-` | 6 | Read + Write |
| `rwx` | 7 | Read + Write + Execute |

---

# 58. 📊 Important chmod Values

| Command | Meaning |
|---|---|
| `chmod 600 file` | Owner Read + Write only |
| `chmod 644 file` | Owner Read + Write, Others Read |
| `chmod 700 dir` | Owner Full Access only |
| `chmod 755 file` | Owner Full, Others Read + Execute |
| `chmod 775 dir` | Owner + Group Full, Others Read + Execute |
| `chmod 777 file` | Everyone Full Access |
| `chmod 4755 file` | SUID + 755 |
| `chmod 2775 dir` | SGID + 775 |
| `chmod 1777 dir` | Sticky Bit + 777 |

---

# 59. 🎯 Top 10 Interview Questions

1. What are Linux file permissions?

2. Explain User, Group, and Others.

3. What do Read, Write, and Execute permissions mean?

4. Explain `chmod 755`.

5. What is the difference between `chmod 644` and `chmod 600`?

6. What is the difference between `chmod`, `chown`, and `chgrp`?

7. What is SUID, SGID, and Sticky Bit?

8. What is `umask`?

9. How would you troubleshoot Permission Denied?

10. Why should you avoid `chmod 777`?

---

# 🏆 Interview Quick Answer Sheet

Question:
What is chmod?

Answer:
`chmod` changes file and directory permissions.

Question:
What is chown?

Answer:
`chown` changes file ownership.

Question:
What is chgrp?

Answer:
`chgrp` changes group ownership.

Question:
What is umask?

Answer:
`umask` controls default permissions for newly created files and directories.

Question:
What is SUID?

Answer:
SUID allows an executable to run with the privileges of its file owner.

Question:
What is SGID?

Answer:
SGID allows an executable to run with group privileges and causes new files in an SGID directory to inherit its group.

Question:
What is Sticky Bit?

Answer:
Sticky Bit restricts users from deleting or renaming files owned by other users in a shared writable directory.

Question:
What is 755?

Answer:

    Owner  → rwx
    Group  → r-x
    Others → r-x

Question:
What is 644?

Answer:

    Owner  → rw-
    Group  → r--
    Others → r--

Question:
What is 600?

Answer:

    Owner  → rw-
    Group  → ---
    Others → ---

---

# 🎯 Final Interview Mental Model

                         LINUX ACCESS CONTROL
                                  │
              ┌───────────────────┼───────────────────┐
              │                   │                   │
              ▼                   ▼                   ▼
          OWNERSHIP           PERMISSIONS        SPECIAL BITS
              │                   │                   │
        ┌─────┴─────┐        ┌────┼────┐        ┌────┼────┐
        │           │        │    │    │        │    │    │
        ▼           ▼        ▼    ▼    ▼        ▼    ▼    ▼
      OWNER       GROUP      r    w    x       SUID SGID Sticky
        │           │        │    │    │
        └─────┬─────┘        4    2    1
              │
              ▼
        ACCESS DECISION
              │
        ┌─────┴─────┐
        │           │
        ▼           ▼
      ALLOW        DENY
        │
        ▼
   Secure Access

---

# 🐧 Chapter 10 — Linux File Permissions & Ownership

## Interview Preparation Checklist

- [x] File Permissions
- [x] User / Group / Others
- [x] Read / Write / Execute
- [x] Permission Strings
- [x] Numeric Permissions
- [x] `chmod`
- [x] Symbolic Permissions
- [x] `chown`
- [x] `chgrp`
- [x] `umask`
- [x] SUID
- [x] SGID
- [x] Sticky Bit
- [x] File vs Directory Permissions
- [x] Permission Denied Troubleshooting
- [x] ACL Basics
- [x] Principle of Least Privilege
- [x] Scenario-Based Questions
- [x] Quick Revision

**Status: 🟢 Complete**

---

## 🔗 Related Resources

📖 [Lesson 10 — Linux File Permissions & Ownership](../levels/level-02-file-system/10-file-permissions-and-ownership.md)

🧪 [Linux File Permissions & Ownership Lab](../labs/10-linux-file-permissions-and-ownership-lab.md)

🏠 [Back to Linux Quest](../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 10**

> *Understand. Control. Secure.*