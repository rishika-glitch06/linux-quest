# 🐧 Linux Quest — Level 02
# Chapter 08: Linux File Permissions & Ownership — Hands-on Lab

---

## 🎯 Lab Objectives

In this lab, you will practice:

- Understanding Linux file permissions
- Reading `ls -l` output
- Understanding User, Group, and Others
- Understanding Read, Write, and Execute permissions
- Using numeric permissions
- Using symbolic permissions
- Using `chmod`
- Using `chown`
- Using `chgrp`
- Understanding `umask`
- Understanding SUID
- Understanding SGID
- Understanding Sticky Bit
- Troubleshooting Permission Denied
- Applying the Principle of Least Privilege

---

# 🧪 Task 01 — Create the Lab Directory

Create a new directory for this lab.

Command:

    mkdir -p ~/linux-permissions-lab
    cd ~/linux-permissions-lab

Verify your current location:

    pwd

Expected output should end with:

    linux-permissions-lab

---

# 🧪 Task 02 — Create Files and Directories

Create the following structure:

    linux-permissions-lab/
    ├── notes.txt
    ├── secret.txt
    ├── script.sh
    ├── public/
    ├── private/
    └── shared/

Commands:

    touch notes.txt
    touch secret.txt
    touch script.sh

    mkdir public
    mkdir private
    mkdir shared

Check the structure:

    ls -la

---

# 🧪 Task 03 — Inspect Default Permissions

Run:

    ls -l

Observe the permissions of:

- notes.txt
- secret.txt
- script.sh
- public
- private
- shared

Answer:

1. Who is the owner?
2. Which group owns the files?
3. What permissions does the owner have?
4. What permissions does the group have?
5. What permissions do others have?

---

# 🧪 Task 04 — Practice chmod 644

Set `notes.txt` permissions to `644`:

    chmod 644 notes.txt

Check:

    ls -l notes.txt

Expected permission:

    -rw-r--r--

Breakdown:

    User    → rw-
    Group   → r--
    Others  → r--

Question:

Why is `644` commonly used for normal readable files?

---

# 🧪 Task 05 — Practice chmod 600

Set `secret.txt` permissions to `600`:

    chmod 600 secret.txt

Check:

    ls -l secret.txt

Expected permission:

    -rw-------

Breakdown:

    User    → rw-
    Group   → ---
    Others  → ---

Question:

Why is `600` useful for private files?

---

# 🧪 Task 06 — Practice Symbolic Permissions

Remove write permission from the owner:

    chmod u-w notes.txt

Check:

    ls -l notes.txt

Add write permission again:

    chmod u+w notes.txt

Add execute permission to the owner:

    chmod u+x notes.txt

Remove execute permission:

    chmod u-x notes.txt

Check the final permission:

    ls -l notes.txt

---

# 🧪 Task 07 — Practice Group Permissions

Add write permission for the group:

    chmod g+w notes.txt

Check:

    ls -l notes.txt

Remove write permission from the group:

    chmod g-w notes.txt

Check again:

    ls -l notes.txt

---

# 🧪 Task 08 — Practice Other Permissions

Add read permission for others:

    chmod o+r notes.txt

Remove read permission from others:

    chmod o-r notes.txt

Check:

    ls -l notes.txt

---

# 🧪 Task 09 — Practice chmod 755

Create a simple script:

    echo '#!/bin/bash' > script.sh
    echo 'echo "Linux Permissions Lab"' >> script.sh

Check the script:

    cat script.sh

Try running the script:

    ./script.sh

You may receive:

    Permission denied

Now add execute permission:

    chmod 755 script.sh

Check:

    ls -l script.sh

Expected permission:

    -rwxr-xr-x

Run the script:

    ./script.sh

Expected output:

    Linux Permissions Lab

Question:

Why was the script not executable before using `chmod 755`?

---

# 🧪 Task 10 — Practice Private Directory

Set `private` directory permissions to `700`:

    chmod 700 private

Check:

    ls -ld private

Expected permission:

    drwx------

Breakdown:

    User    → rwx
    Group   → ---
    Others  → ---

Question:

Why does a directory need execute permission to be accessed or traversed?

---

# 🧪 Task 11 — Practice Public Directory

Set `public` directory permissions to `755`:

    chmod 755 public

Check:

    ls -ld public

Expected permission:

    drwxr-xr-x

Breakdown:

    User    → rwx
    Group   → r-x
    Others  → r-x

Question:

What can users do with this directory based on these permissions?

---

# 🧪 Task 12 — Check Current User

Run:

    whoami

Then:

    id

Then:

    groups

Record:

    Username:
    UID:
    Primary GID:
    Groups:

---

# 🧪 Task 13 — Check File Ownership

Run:

    ls -l notes.txt

Identify:

    Owner:
    Group:
    Permissions:

---

# 🧪 Task 14 — Practice chown

Check your current user:

    whoami

Change the owner of the file to your current user:

    sudo chown $USER notes.txt

Verify:

    ls -l notes.txt

Question:

What changed after using `chown`?

---

# 🧪 Task 15 — Practice chgrp

Check your groups:

    groups

Choose a group you belong to.

Change the group ownership:

    sudo chgrp GROUP_NAME notes.txt

Replace `GROUP_NAME` with an actual group from your system.

Verify:

    ls -l notes.txt

Question:

What changed after using `chgrp`?

---

# 🧪 Task 16 — Practice umask

Check your current umask:

    umask

Create a new file:

    touch umask-file.txt

Create a new directory:

    mkdir umask-directory

Check the permissions:

    ls -l umask-file.txt
    ls -ld umask-directory

Observe the default permissions.

Questions:

1. What is the current umask?
2. What permissions were assigned to the new file?
3. What permissions were assigned to the new directory?
4. How does umask affect newly created files and directories?

---

# 🧪 Task 17 — Permission Denied Challenge

Create a file:

    touch restricted.txt

Remove all permissions:

    chmod 000 restricted.txt

Check:

    ls -l restricted.txt

Try reading the file:

    cat restricted.txt

You may receive:

    Permission denied

Restore permissions:

    chmod 644 restricted.txt

Verify:

    ls -l restricted.txt

Question:

Why did `cat restricted.txt` fail when the file had `000` permissions?

---

# 🧪 Task 18 — Practice SUID

Create a test file:

    touch suid-test

Set SUID:

    chmod 4755 suid-test

Check:

    ls -l suid-test

Observe the `s` in the owner permission position.

Remove SUID:

    chmod u-s suid-test

Verify:

    ls -l suid-test

Note:

SUID is meaningful primarily on executable files. This task is only for observing the permission bit.

Question:

What is the numeric value of SUID?

Answer:

    4000

---

# 🧪 Task 19 — Practice SGID

Create a directory:

    mkdir sgid-test

Set SGID:

    chmod 2755 sgid-test

Check:

    ls -ld sgid-test

Observe the `s` in the group permission position.

Remove SGID:

    chmod g-s sgid-test

Verify:

    ls -ld sgid-test

Question:

What is the numeric value of SGID?

Answer:

    2000

---

# 🧪 Task 20 — Practice Sticky Bit

Create a shared directory:

    mkdir shared-test

Set Sticky Bit:

    chmod 1777 shared-test

Check:

    ls -ld shared-test

Expected permission pattern:

    drwxrwxrwt

Observe the `t` at the end of the permissions.

Remove Sticky Bit:

    chmod 0777 shared-test

Verify:

    ls -ld shared-test

Question:

What is the numeric value of Sticky Bit?

Answer:

    1000

---

# 🧪 Task 21 — Permission Calculation Challenge

Calculate the numeric permission for:

    rwxr-xr--

Calculate:

    User:
    rwx = ?

    Group:
    r-x = ?

    Others:
    r-- = ?

Answer:

    User    → 7
    Group   → 5
    Others  → 4

Therefore:

    754

Apply it:

    chmod 754 notes.txt

Verify:

    ls -l notes.txt

Question:

What does `754` allow the User, Group, and Others to do?

---

# 🧪 Task 22 — Symbolic Permission Challenge

Starting permission:

    -rw-r--r--

Perform the following:

1. Give owner execute permission.
2. Give group write permission.
3. Remove read permission from others.
4. Remove execute permission from owner.

Commands:

    chmod u+x notes.txt
    chmod g+w notes.txt
    chmod o-r notes.txt
    chmod u-x notes.txt

Check:

    ls -l notes.txt

Question:

What is the final permission of `notes.txt`?

---

# 🏆 FINAL CHALLENGE — Build a Secure Project

Create the following structure:

    permissions-project/
    ├── public/
    │   └── readme.txt
    ├── private/
    │   └── secret.txt
    ├── scripts/
    │   └── backup.sh
    └── shared/

Create directories:

    mkdir -p permissions-project/public
    mkdir -p permissions-project/private
    mkdir -p permissions-project/scripts
    mkdir -p permissions-project/shared

Create files:

    touch permissions-project/public/readme.txt
    touch permissions-project/private/secret.txt
    touch permissions-project/scripts/backup.sh

Set permissions for the public file:

    chmod 644 permissions-project/public/readme.txt

Set permissions for the private file:

    chmod 600 permissions-project/private/secret.txt

Set executable permissions for the script:

    chmod 755 permissions-project/scripts/backup.sh

Set Sticky Bit for the shared directory:

    chmod 1777 permissions-project/shared

Verify everything:

    ls -la permissions-project/public
    ls -la permissions-project/private
    ls -la permissions-project/scripts
    ls -ld permissions-project/shared

Expected configuration:

    public/readme.txt
    → 644

    private/secret.txt
    → 600

    scripts/backup.sh
    → 755

    shared/
    → 1777

---

# 🧠 FINAL LAB QUESTIONS

Answer these questions after completing the lab:

1. What is the difference between Read, Write, and Execute permissions?

2. What does `755` mean?

3. What does `644` mean?

4. What does `600` mean?

5. What does `700` mean?

6. What is the difference between `chmod` and `chown`?

7. What does `chgrp` do?

8. What is `umask`?

9. What is SUID?

10. What is SGID?

11. What is Sticky Bit?

12. Why should `chmod 777` generally be avoided?

13. What permission is required to enter or traverse a directory?

14. What permission is required to list directory contents?

15. How would you troubleshoot `Permission denied`?

16. What is the Principle of Least Privilege?

17. What is the difference between numeric and symbolic permissions?

18. What is the difference between SUID, SGID, and Sticky Bit?

---

# 📸 EVIDENCE CHECKLIST

Record terminal output or screenshots for:

- [ ] `ls -l`
- [ ] `chmod 644`
- [ ] `chmod 600`
- [ ] Symbolic chmod
- [ ] Executable script
- [ ] `chmod 755`
- [ ] Private directory
- [ ] `chmod 700`
- [ ] `whoami`
- [ ] `id`
- [ ] `groups`
- [ ] `chown`
- [ ] `chgrp`
- [ ] `umask`
- [ ] Permission Denied challenge
- [ ] SUID
- [ ] SGID
- [ ] Sticky Bit
- [ ] Permission calculation
- [ ] Symbolic permission challenge
- [ ] Final secure project

---

# 📝 LAB NOTES

## What I Learned

- 
- 
- 
- 

## Commands I Practiced

- `ls -l`
- `ls -ld`
- `chmod`
- `chown`
- `chgrp`
- `umask`
- `whoami`
- `id`
- `groups`

## Challenges Faced

- 

## How I Solved Them

- 

---

# 🏁 CHAPTER 08 STATUS

Linux File Permissions & Ownership

Theory              → ⬜
Diagram             → ⬜
Interview Prep      → 🟢 Complete
Hands-on Lab        → 🟢 Complete
README              → ⬜
Git Commits         → ⬜

Status: 🟡 In Progress

---

# 🐧 Linux Quest

> Understand permissions.
> Control access.
> Follow least privilege.
> Secure Linux.