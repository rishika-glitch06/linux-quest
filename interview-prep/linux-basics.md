# 💼 Linux Basics - Interview Preparation

Welcome!

This file contains all the important interview questions covered in **Level 01: Linux Basics**.

As new lessons are added, this file will also grow.

---

# 📖 Lesson 01 - What is Linux?

## Q1. What is Linux?

**Answer:**

Linux is a free and open-source operating system kernel that manages computer hardware and software resources. Popular operating systems like Ubuntu, Fedora, and Debian are built using the Linux kernel.

---

## Q2. What is an Operating System?

**Answer:**

An Operating System (OS) is system software that acts as an interface between the user and the computer hardware. It manages memory, CPU, files, devices, and running applications.

---

## Q3. Is Linux an Operating System or a Kernel?

**Answer:**

Technically, Linux is a kernel. A complete operating system combines the Linux kernel with system utilities and applications.

---

## Q4. Why is Linux called Open Source?

**Answer:**

Linux is called open source because its source code is publicly available, allowing anyone to view, modify, and distribute it under its license.

---

# 📖 Lesson 02 - History of Linux

## Q1. Who created Linux?

**Answer:**

Linux was created by Linus Torvalds, a Finnish computer science student, in 1991.

---

## Q2. Why was Linux created?

**Answer:**

Linux was created because Linus Torvalds wanted a free and flexible operating system for learning and experimentation.

---

## Q3. Which operating systems inspired Linux?

**Answer:**

Linux was inspired by UNIX and developed while Linus Torvalds was using MINIX.

---

## Q4. What is Tux?

**Answer:**

Tux is the official penguin mascot of Linux.

---

# 📖 Lesson 03 - Why Linux?

## Q1. Why is Linux popular?

**Answer:**

Linux is free, open source, secure, stable, customizable, and supported by a large developer community.

---

## Q2. Why do companies prefer Linux servers?

**Answer:**

Linux servers provide excellent performance, security, stability, and cost efficiency.

---

## Q3. Why is Linux important for DevOps?

**Answer:**

Most DevOps tools such as Docker, Kubernetes, Jenkins, and Ansible are designed to work efficiently on Linux.

---

## Q4. Name some careers where Linux is an important skill.

**Answer:**

- DevOps Engineer
- Cloud Engineer
- AI / Machine Learning Engineer
- Cybersecurity Analyst
- Site Reliability Engineer (SRE)
- Data Engineer

---

# ⭐ Quick Revision

Remember these keywords:

- Open Source
- Kernel
- Operating System
- Linus Torvalds
- UNIX
- MINIX
- Tux
- Security
- Stability
- Performance
- Cloud Computing
- DevOps
- AI
- Docker
- Kubernetes

---

# 📖 Lesson 04 - Linux Kernel

## Q1. What is the Linux Kernel?

**Answer:**

The Linux Kernel is the core component of the Linux operating system. It acts as a bridge between software and hardware by managing system resources and hardware communication.

---

## Q2. What are the main responsibilities of the Kernel?

**Answer:**

- Process Management
- Memory Management
- Device Management
- File System Management
- Security and Permissions

---

## Q3. Why can't applications communicate directly with hardware?

**Answer:**

Applications communicate with the Kernel, and the Kernel safely interacts with the hardware using device drivers.

---

## Q4. Which type of Kernel does Linux use?

**Answer:**

Linux uses a **Monolithic Kernel**, where most operating system services run inside the Kernel space.

---

## Q5. What is the difference between User Space and Kernel Space?

**Answer:**

User Space is where applications run with limited permissions.

Kernel Space is where the Kernel runs with full access to system hardware and resources.
---

# 📖 Lesson 05 - Linux Distributions

## Q1. What is a Linux Distribution?

**Answer:**

A Linux Distribution (or Linux Distro) is a complete operating system built using the Linux Kernel along with system utilities, software packages, package managers, and other tools.

---

## Q2. What is the difference between the Linux Kernel and a Linux Distribution?

**Answer:**

The Linux Kernel is the core component that manages hardware and system resources.

A Linux Distribution is a complete operating system that includes the Linux Kernel along with applications, utilities, package managers, and other software.

---

## Q3. Name some popular Linux distributions.

**Answer:**

- Ubuntu
- Debian
- Fedora
- Arch Linux
- Linux Mint
- Kali Linux
- Red Hat Enterprise Linux (RHEL)

---

## Q4. Which Linux distribution is best for beginners?

**Answer:**

Ubuntu and Linux Mint are considered the best choices for beginners because they are user-friendly, stable, and have strong community support.

---

## Q5. Why are there so many Linux distributions?

**Answer:**

Different distributions are created to meet different user needs such as desktop usage, software development, cloud computing, cybersecurity, enterprise environments, and education.

---

## Q6. Which Linux distribution is widely used in cloud and DevOps?

**Answer:**

Ubuntu and Debian are among the most commonly used distributions in cloud computing and DevOps environments because of their stability and extensive package support.

---

# 📖 Lesson 06 - GUI vs CLI

## Q1. What is GUI?

**Answer:**

GUI (Graphical User Interface) is a way of interacting with a computer using graphical elements like windows, icons, buttons, and menus instead of typing commands.

---

## Q2. What is CLI?

**Answer:**

CLI (Command Line Interface) is a text-based interface where users interact with the operating system by typing commands in a terminal.

---

## Q3. What are the advantages of CLI over GUI?

**Answer:**

- Faster for experienced users
- Uses fewer system resources
- Easy to automate tasks
- Ideal for remote server management
- Preferred in DevOps and System Administration

---

## Q4. What are the advantages of GUI?

**Answer:**

- Easy to learn
- User-friendly
- Visual interaction
- Suitable for beginners
- Great for everyday desktop use

---

## Q5. Which interface is commonly used on Linux servers?

**Answer:**

CLI is commonly used because it is lightweight, efficient, and allows remote management through SSH.

---

## Q6. Should a Linux professional know both GUI and CLI?

**Answer:**

Yes. A Linux professional should be comfortable with both. GUI is useful for everyday tasks, while CLI is essential for administration, automation, troubleshooting, and server management.
---

# 📖 Lesson 07 - Terminal Basics

## Q1. What is a Terminal?

**Answer:**

A Terminal is an application that allows users to interact with the Linux operating system by typing commands. It provides a text-based interface to communicate with the system.

---

## Q2. What is the difference between a Terminal and a Shell?

**Answer:**

A Terminal is the application where users type commands.

A Shell is the program that interprets and executes those commands.

---

## Q3. Name some popular Linux shells.

**Answer:**

- Bash
- Zsh
- Fish
- Ksh
- Tcsh

---

## Q4. What does the `$` symbol in the terminal prompt indicate?

**Answer:**

The `$` symbol indicates that the current user is a normal (non-root) user.

The `#` symbol usually indicates the root user.

---

## Q5. Which shell is the default on most Linux distributions?

**Answer:**

Bash (Bourne Again Shell) is the default shell on many Linux distributions.

---

## Q6. Why do Linux professionals prefer using the terminal?

**Answer:**

The terminal is faster, consumes fewer system resources, allows automation through scripting, and is ideal for managing remote servers and performing administrative tasks.

---

## Q7. What is a terminal prompt?

**Answer:**

The terminal prompt is the text displayed before the cursor (for example, `rishika@ubuntu:~$`). It typically shows the current user, hostname, current directory, and user privilege level.
---

# 📖 Lesson 08 - First Linux Commands

## Q1. What does the `ls` command do?

**Answer:**

The `ls` command lists all files and directories in the current working directory.

---

## Q2. What is the purpose of the `pwd` command?

**Answer:**

It displays the absolute path of the current working directory.

---

## Q3. What is the difference between `cd` and `pwd`?

**Answer:**

- `cd` changes the current directory.
- `pwd` displays the current directory.

---

## Q4. What does the `mkdir` command do?

**Answer:**

It creates a new directory (folder).

---

## Q5. What does the `touch` command do?

**Answer:**

It creates a new empty file. If the file already exists, it updates its timestamp.

---

## Q6. When should you use `rmdir` instead of `rm -r`?

**Answer:**

Use `rmdir` only for empty directories. Use `rm -r` when the directory contains files or subdirectories.

---

## Q7. Which Linux commands are used daily by almost every Linux user?

**Answer:**

`pwd`, `ls`, `cd`, `mkdir`, `touch`, `rm`, `rmdir`