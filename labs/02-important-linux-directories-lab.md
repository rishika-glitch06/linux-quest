# 🧪 Lab 02 — Explore Important Linux Directories

> Learn the purpose of important Linux directories by exploring them directly from the terminal.

---

## 🎯 Lab Objectives

By completing this lab, you will learn how to:

- Explore important Linux directories
- Understand `/etc`
- Understand `/home`
- Understand `/root`
- Understand `/boot`
- Understand `/dev`
- Understand `/proc`
- Understand `/sys`
- Understand `/tmp`
- Understand `/usr`
- Understand `/var`
- Inspect system information

---

# 🧰 Commands Used

```bash
pwd
ls
ls -l
cd
cat
head
```

---

# 🧩 Task 01 — Explore `/etc`

Run:

```bash
ls /etc
```

Now inspect some configuration files:

```bash
cat /etc/hostname
```

You can also check:

```bash
cat /etc/hosts
```

### 🧠 Observation

The `/etc` directory contains system-wide configuration files.

---

# 🧩 Task 02 — Explore `/home`

Run:

```bash
ls /home
```

If a user directory exists, explore it:

```bash
ls /home/<username>
```

Replace `<username>` with the actual username on your system.

### 🧠 Observation

`/home` stores personal directories of normal users.

---

# 🧩 Task 03 — Explore `/root`

Run:

```bash
ls /root
```

If you receive a permission error, that is expected when you are not logged in as the root user.

### 🧠 Observation

`/root` is the home directory of the root user.

---

# 🧩 Task 04 — Explore `/boot`

Run:

```bash
ls /boot
```

Look for files related to the Linux kernel and boot process.

### 🧠 Observation

`/boot` contains important files required during system startup.

---

# 🧩 Task 05 — Explore `/dev`

Run:

```bash
ls /dev
```

You can inspect specific device interfaces:

```bash
ls /dev/null
```

Try:

```bash
ls -l /dev/null
```

### 🧠 Observation

`/dev` contains special files representing devices and device interfaces.

---

# 🧩 Task 06 — Explore `/proc`

Run:

```bash
ls /proc
```

Check CPU information:

```bash
cat /proc/cpuinfo
```

Check memory information:

```bash
cat /proc/meminfo
```

Check information about the running kernel:

```bash
cat /proc/version
```

### 🧠 Observation

`/proc` is a virtual file system that provides dynamic information about processes and the Linux kernel.

---

# 🧩 Task 07 — Explore `/sys`

Run:

```bash
ls /sys
```

Explore the devices directory:

```bash
ls /sys/devices
```

### 🧠 Observation

`/sys` provides information about hardware, devices, drivers, and the Linux kernel.

---

# 🧩 Task 08 — Explore `/tmp`

Run:

```bash
ls /tmp
```

Create a temporary test file:

```bash
touch /tmp/linux-quest-test
```

Verify:

```bash
ls /tmp
```

Remove the test file:

```bash
rm /tmp/linux-quest-test
```

### 🧠 Observation

`/tmp` is commonly used for temporary files.

---

# 🧩 Task 09 — Explore `/usr`

Run:

```bash
ls /usr
```

Explore:

```bash
ls /usr/bin
```

You can also check:

```bash
ls /usr/share
```

### 🧠 Observation

`/usr` contains many user-space applications, libraries, and shared resources.

---

# 🧩 Task 10 — Explore `/var`

Run:

```bash
ls /var
```

Explore log files:

```bash
ls /var/log
```

Explore cache:

```bash
ls /var/cache
```

### 🧠 Observation

`/var` contains variable data that changes during normal system operation.

---

# 🧩 Task 11 — Explore `/media`

Run:

```bash
ls /media
```

If removable devices are connected and mounted, you may see them here.

### 🧠 Observation

`/media` is commonly used for removable storage devices.

---

# 🧩 Task 12 — Explore `/mnt`

Run:

```bash
ls /mnt
```

### 🧠 Observation

`/mnt` is traditionally used as a temporary mount point.

---

# 🧩 Task 13 — Explore `/opt`

Run:

```bash
ls /opt
```

### 🧠 Observation

`/opt` is commonly used for optional or third-party software.

---

# 🧩 Task 14 — Explore `/run`

Run:

```bash
ls /run
```

### 🧠 Observation

`/run` contains temporary runtime information created while the system is running.

---

# 🧩 Task 15 — Explore `/srv`

Run:

```bash
ls /srv
```

### 🧠 Observation

`/srv` is used for data related to services provided by the system.

---

# 🧠 Challenge — Directory Identification

Identify the correct directory for each situation.

### Challenge 01

System configuration files:

```text
Answer: __________
```

### Challenge 02

Normal user home directories:

```text
Answer: __________
```

### Challenge 03

System boot files:

```text
Answer: __________
```

### Challenge 04

Process and kernel information:

```text
Answer: __________
```

### Challenge 05

Hardware and device information:

```text
Answer: __________
```

### Challenge 06

System and application logs:

```text
Answer: __________
```

### Challenge 07

Temporary files:

```text
Answer: __________
```

### Challenge 08

Optional third-party software:

```text
Answer: __________
```

---

# 🧩 Scenario Challenge

Imagine you are debugging a Linux server.

### Scenario 01

The system configuration needs to be inspected.

Where would you look?

```text
Answer: __________
```

---

### Scenario 02

You want to investigate why a service stopped working.

Where would you look for logs?

```text
Answer: __________
```

---

### Scenario 03

You want to inspect CPU and memory information.

Which directory would you check?

```text
Answer: __________
```

---

### Scenario 04

You want to inspect hardware information exposed by the kernel.

Which directory would you check?

```text
Answer: __________
```

---

### Scenario 05

You need a temporary location to store a test file.

Which directory could you use?

```text
Answer: __________
```

---

# 📝 Lab Questions

### Q1. What is the purpose of `/etc`?

**Your Answer:**

---

### Q2. What is the difference between `/home` and `/root`?

**Your Answer:**

---

### Q3. What is the purpose of `/proc`?

**Your Answer:**

---

### Q4. What is the purpose of `/sys`?

**Your Answer:**

---

### Q5. What is the difference between `/dev` and `/sys`?

**Your Answer:**

---

### Q6. What is stored in `/var/log`?

**Your Answer:**

---

### Q7. What is the difference between `/media` and `/mnt`?

**Your Answer:**

---

### Q8. What is the purpose of `/opt`?

**Your Answer:**

---

# 📊 Directory Investigation Table

Complete this table after performing the lab.

| Directory | What did you find? | Purpose |
|---|---|---|
| `/etc` | | |
| `/home` | | |
| `/root` | | |
| `/boot` | | |
| `/dev` | | |
| `/proc` | | |
| `/sys` | | |
| `/tmp` | | |
| `/usr` | | |
| `/var` | | |
| `/media` | | |
| `/mnt` | | |
| `/opt` | | |
| `/run` | | |
| `/srv` | | |

---

# ✅ Lab Completion Checklist

- [ ] Explored `/etc`
- [ ] Explored `/home`
- [ ] Explored `/root`
- [ ] Explored `/boot`
- [ ] Explored `/dev`
- [ ] Explored `/proc`
- [ ] Explored `/sys`
- [ ] Explored `/tmp`
- [ ] Explored `/usr`
- [ ] Explored `/var`
- [ ] Explored `/media`
- [ ] Explored `/mnt`
- [ ] Explored `/opt`
- [ ] Explored `/run`
- [ ] Explored `/srv`
- [ ] Completed directory identification challenge
- [ ] Completed scenario challenge
- [ ] Completed investigation table

---

# 🏆 Quest Complete

You have successfully completed:

> 🐧 **Level 02 — Lab 02: Explore Important Linux Directories**

You now understand the purpose of the major directories in the Linux File System Hierarchy and have practiced exploring them directly from the terminal.

---

## 🔗 Navigation

📖 [Level 02 — Linux File System](../../levels/level-02-file-system/README.md)

🖼️ [Important Linux Directories Diagram](../../assets/diagrams/important-linux-directories.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🏠 [Back to Linux Quest](../../README.md)