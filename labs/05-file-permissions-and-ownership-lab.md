# 🧪 Linux Quest — Lesson 05 Lab

# 🔐 File Permissions & Ownership Lab

> A hands-on lab to practice Linux file permissions, ownership, `chmod`, `chown`, and `chgrp`.

---

## 🎯 Lab Objectives

By completing this lab, you will practice:

- Viewing file permissions
- Understanding `r`, `w`, and `x`
- Creating files and directories
- Changing permissions using `chmod`
- Using symbolic permission notation
- Using numeric permission notation
- Understanding file ownership
- Changing ownership using `chown`
- Changing group ownership using `chgrp`
- Understanding directory permissions
- Verifying permission changes

---

# 🧩 Task 1 — Create a Lab Workspace

Create a directory for this lab:

```bash
mkdir permissions-lab
```

Enter the directory:

```bash
cd permissions-lab
```

Verify your location:

```bash
pwd
```

Expected output should end with:

```text
permissions-lab
```

---

# 🧩 Task 2 — Create Practice Files

Create three files:

```bash
touch notes.txt script.sh secret.txt
```

Check the files:

```bash
ls
```

Expected:

```text
notes.txt
script.sh
secret.txt
```

---

# 🧩 Task 3 — View Default Permissions

Run:

```bash
ls -l
```

Observe the permissions of all three files.

Example:

```text
-rw-r--r-- 1 user user 0 notes.txt
-rw-r--r-- 1 user user 0 script.sh
-rw-r--r-- 1 user user 0 secret.txt
```

Your output may be different depending on your Linux system and `umask`.

---

# 🧩 Task 4 — Understand Permission Notation

Take this example:

```text
-rwxr-xr--
```

Identify:

```text
File Type:
User:
Group:
Others:
```

Expected:

```text
File Type: Regular File
User: rwx
Group: r-x
Others: r--
```

---

# 🧩 Task 5 — Add Execute Permission

Add execute permission to the owner of `script.sh`:

```bash
chmod u+x script.sh
```

Check:

```bash
ls -l script.sh
```

The owner should now have:

```text
rwx
```

---

# 🧩 Task 6 — Remove Execute Permission

Remove execute permission from the owner:

```bash
chmod u-x script.sh
```

Verify:

```bash
ls -l script.sh
```

---

# 🧩 Task 7 — Add Write Permission to Group

Run:

```bash
chmod g+w notes.txt
```

Verify:

```bash
ls -l notes.txt
```

The group should now have write permission.

---

# 🧩 Task 8 — Remove Write Permission from Others

Run:

```bash
chmod o-w notes.txt
```

Verify:

```bash
ls -l notes.txt
```

---

# 🧩 Task 9 — Set Numeric Permission 644

Set `notes.txt` to permission `644`:

```bash
chmod 644 notes.txt
```

Verify:

```bash
ls -l notes.txt
```

Expected permission:

```text
-rw-r--r--
```

Breakdown:

```text
User:
6 → rw-

Group:
4 → r--

Others:
4 → r--
```

---

# 🧩 Task 10 — Set Numeric Permission 755

Set `script.sh` to:

```bash
chmod 755 script.sh
```

Verify:

```bash
ls -l script.sh
```

Expected:

```text
-rwxr-xr-x
```

Breakdown:

```text
User:
7 → rwx

Group:
5 → r-x

Others:
5 → r-x
```

---

# 🧩 Task 11 — Set Permission 600

Set `secret.txt` to:

```bash
chmod 600 secret.txt
```

Verify:

```bash
ls -l secret.txt
```

Expected:

```text
-rw-------
```

Meaning:

```text
User:
Read + Write

Group:
No permissions

Others:
No permissions
```

---

# 🧩 Task 12 — Create a Directory

Create a directory:

```bash
mkdir private
```

Check:

```bash
ls -ld private
```

The `-d` option displays information about the directory itself.

---

# 🧩 Task 13 — Set Directory Permissions

Set the directory permission to `700`:

```bash
chmod 700 private
```

Verify:

```bash
ls -ld private
```

Expected:

```text
drwx------
```

Meaning:

```text
Owner:
Read + Write + Execute

Group:
No permissions

Others:
No permissions
```

---

# 🧩 Task 14 — Create a File Inside the Directory

Enter the directory:

```bash
cd private
```

Create a file:

```bash
touch private.txt
```

Check:

```bash
ls -l
```

Return to the parent directory:

```bash
cd ..
```

---

# 🧩 Task 15 — Change Group Permission

Add read and execute permission to the group for `script.sh`:

```bash
chmod g+rx script.sh
```

Verify:

```bash
ls -l script.sh
```

---

# 🧩 Task 16 — Change Permissions for Others

Add read permission for others:

```bash
chmod o+r notes.txt
```

Verify:

```bash
ls -l notes.txt
```

---

# 🧩 Task 17 — Remove All Permissions from Others

Run:

```bash
chmod o-rwx secret.txt
```

Verify:

```bash
ls -l secret.txt
```

Others should have:

```text
---
```

---

# 🧩 Task 18 — Practice `chown`

Check current ownership:

```bash
ls -l notes.txt
```

You will see the current owner and group.

Example:

```text
-rw-r--r-- 1 rishika users 0 notes.txt
```

The owner is:

```text
rishika
```

The group is:

```text
users
```

> ⚠️ Changing ownership usually requires administrator privileges.

Example:

```bash
sudo chown username notes.txt
```

Replace `username` with an actual user available on your system.

Verify:

```bash
ls -l notes.txt
```

---

# 🧩 Task 19 — Practice `chgrp`

Change the group ownership:

```bash
sudo chgrp groupname notes.txt
```

Replace `groupname` with a valid group on your system.

Verify:

```bash
ls -l notes.txt
```

---

# 🧩 Task 20 — Change Owner and Group Together

Use:

```bash
sudo chown username:groupname notes.txt
```

Verify:

```bash
ls -l notes.txt
```

Expected structure:

```text
Owner → username
Group → groupname
```

> ⚠️ Use actual users and groups available on your Linux system.

---

# 🧩 Task 21 — Permission Calculation Challenge

Calculate the numeric permission for:

```text
rwxr-x---
```

Break it down:

```text
User:
rwx = ?

Group:
r-x = ?

Others:
--- = ?
```

### Answer

```text
User:
4 + 2 + 1 = 7

Group:
4 + 1 = 5

Others:
0 = 0
```

Therefore:

```bash
chmod 750 filename
```

---

# 🧩 Task 22 — Permission Challenge

Set `notes.txt` to:

```text
rw-r-----
```

Calculate:

```text
User:
rw- = ?

Group:
r-- = ?

Others:
--- = ?
```

### Answer

```text
6
4
0
```

Run:

```bash
chmod 640 notes.txt
```

Verify:

```bash
ls -l notes.txt
```

---

# 🧩 Task 23 — Permission Challenge

Set `script.sh` to:

```text
rwxr-xr-x
```

Use:

```bash
chmod 755 script.sh
```

Verify:

```bash
ls -l script.sh
```

---

# 🧩 Task 24 — Security Challenge

Check the permissions:

```bash
ls -l
```

If you see:

```text
-rwxrwxrwx
```

Ask yourself:

> Does this file really need `777` permissions?

The recommended approach is to give only the permissions required by the user or application.

---

# 🧩 Task 25 — Final Verification

Run:

```bash
ls -la
```

Check:

```text
File Name
Permissions
Owner
Group
```

Your final workspace should contain:

```text
permissions-lab/
│
├── notes.txt
├── script.sh
├── secret.txt
└── private/
    └── private.txt
```

---

# 🧠 Lab Questions

Answer these questions after completing the lab.

### Q1. What command displays file permissions?

```text
Answer:
```

### Q2. What does `r` mean?

```text
Answer:
```

### Q3. What does `w` mean?

```text
Answer:
```

### Q4. What does `x` mean?

```text
Answer:
```

### Q5. What does `chmod` do?

```text
Answer:
```

### Q6. What does `chown` do?

```text
Answer:
```

### Q7. What does `chgrp` do?

```text
Answer:
```

### Q8. What does `chmod 755` mean?

```text
Answer:
```

### Q9. What does `chmod 644` mean?

```text
Answer:
```

### Q10. Why should `chmod 777` be avoided when unnecessary?

```text
Answer:
```

---

# 🏆 Lab Completion Checklist

- [ ] Created `permissions-lab`
- [ ] Created practice files
- [ ] Used `ls -l`
- [ ] Understood `r`, `w`, and `x`
- [ ] Used symbolic `chmod`
- [ ] Used numeric `chmod`
- [ ] Practiced `644`
- [ ] Practiced `755`
- [ ] Practiced `600`
- [ ] Created a directory
- [ ] Changed directory permissions
- [ ] Practiced `chown`
- [ ] Practiced `chgrp`
- [ ] Calculated permission values
- [ ] Understood `777` security risks
- [ ] Completed final verification
- [ ] Answered lab questions

---

# 🎯 Final Challenge

Without looking at the previous commands, try to achieve:

```text
notes.txt
→ rw-r-----

script.sh
→ rwxr-xr-x

secret.txt
→ rw-------

private/
→ rwx------
```

Then verify everything using:

```bash
ls -l
ls -ld private
```

---

# 🐧 Linux Quest Progress

```text
Level 02
    │
    ▼
Lesson 05
    │
    ├── 📖 Lesson
    ├── 🖼️ Diagram
    ├── 💼 Interview Preparation
    └── 🧪 Hands-on Lab
             │
             ▼
          COMPLETE
```

> 🏆 **Linux Quest — Level 02, Lesson 05 Lab Complete**

> *Learn permissions. Practice access control. Build secure Linux skills.*

---

## 🔗 Related Resources

📖 [Lesson 05 — File Permissions & Ownership](../levels/level-02-file-system/05-file-permissions-and-ownership.md)

🖼️ [File Permissions & Ownership Diagram](../assets/diagrams/file-permissions-and-ownership.md)

💼 [Linux File System Interview Preparation](../interview-prep/linux-file-system.md)

🏠 [Back to Linux Quest](../README.md)