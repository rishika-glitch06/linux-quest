# 🐧 Lesson 05 — File Permissions & Ownership

> Learn how Linux controls access to files and directories using permissions, users, groups, and ownership.

---

# 🎯 Learning Objectives

By the end of this lesson, you will understand:

- Linux file permissions
- Read, write, and execute permissions
- User, group, and others
- File ownership
- Directory permissions
- `chmod`
- `chown`
- `chgrp`
- Symbolic and numeric permission modes
- Permission notation
- Common permission patterns
- Basic Linux security concepts

---

# 1. 🔐 What Are File Permissions?

Linux uses permissions to control who can access a file or directory.

Every file and directory has three basic types of permissions:

```text
r → Read
w → Write
x → Execute
```

These permissions determine what users can do with a file.

---

# 2. 👥 Permission Categories

Linux permissions are divided into three categories:

```text
User (u)
Group (g)
Others (o)
```

### User

The owner of the file.

### Group

Users who belong to the file's assigned group.

### Others

Everyone else.

---

# 3. 📊 Permission Structure

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
-   rwx   r-x   r--
│    │     │     │
│    │     │     └── Others
│    │     └──────── Group
│    └────────────── User
└─────────────────── File type
```

The first character represents the file type.

```text
- → Regular file
d → Directory
l → Symbolic link
```

---

# 4. 📖 Read Permission

The `r` permission allows reading.

For a file:

```text
r → Read file contents
```

For a directory:

```text
r → List directory contents
```

---

# 5. ✏️ Write Permission

The `w` permission allows modification.

For a file:

```text
w → Modify file contents
```

For a directory:

```text
w → Create, delete, or rename entries
```

---

# 6. ⚙️ Execute Permission

The `x` permission allows execution.

For a file:

```text
x → Execute the file as a program
```

For a directory:

```text
x → Access or enter the directory
```

Example:

```bash
cd Projects
```

requires execute permission on the directory.

---

# 7. 👤 User, Group, and Others

Consider:

```text
-rwxr-xr--
```

The permissions are:

```text
User     → rwx
Group    → r-x
Others   → r--
```

Meaning:

```text
User:
Read + Write + Execute

Group:
Read + Execute

Others:
Read only
```

---

# 8. 🔍 Viewing Permissions

Use:

```bash
ls -l
```

Example output:

```text
-rw-r--r-- 1 rishika users 120 Jul 27 notes.txt
```

The first part:

```text
-rw-r--r--
```

represents permissions.

---

# 9. 🧩 Understanding `ls -l`

Example:

```text
-rw-r--r-- 1 rishika users 120 Jul 27 notes.txt
```

Breakdown:

```text
-rw-r--r--
│
├── File type and permissions
│
├── 1
│   └── Number of hard links
│
├── rishika
│   └── Owner
│
├── users
│   └── Group
│
├── 120
│   └── File size
│
├── Jul 27
│   └── Modification date
│
└── notes.txt
    └── File name
```

---

# 10. 🔧 Changing Permissions with `chmod`

The `chmod` command changes file permissions.

Example:

```bash
chmod u+x script.sh
```

This adds execute permission for the user.

---

# 11. 🧩 Symbolic Permission Mode

The symbolic method uses:

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

---

# 12. ➕ Adding Permissions

Add execute permission to the owner:

```bash
chmod u+x script.sh
```

Add write permission to the group:

```bash
chmod g+w notes.txt
```

Add read permission to others:

```bash
chmod o+r notes.txt
```

---

# 13. ➖ Removing Permissions

Remove write permission from others:

```bash
chmod o-w notes.txt
```

Remove execute permission from the group:

```bash
chmod g-x script.sh
```

---

# 14. 🌐 Changing Permissions for Everyone

Add execute permission for everyone:

```bash
chmod a+x script.sh
```

Remove write permission for everyone:

```bash
chmod a-w notes.txt
```

---

# 15. 🔢 Numeric Permissions

Linux permissions can also be represented using numbers.

```text
Read    = 4
Write   = 2
Execute = 1
```

Add the values together.

### Read + Write

```text
4 + 2 = 6
```

### Read + Execute

```text
4 + 1 = 5
```

### Write + Execute

```text
2 + 1 = 3
```

### Read + Write + Execute

```text
4 + 2 + 1 = 7
```

---

# 16. 📊 Numeric Permission Table

| Number | Permission |
|---|---|
| 0 | --- |
| 1 | --x |
| 2 | -w- |
| 3 | -wx |
| 4 | r-- |
| 5 | r-x |
| 6 | rw- |
| 7 | rwx |

---

# 17. 🔢 Common `chmod` Examples

Give owner full permissions and everyone else read-only:

```bash
chmod 744 script.sh
```

Meaning:

```text
User    → 7 → rwx
Group   → 4 → r--
Others  → 4 → r--
```

---

Give everyone read and execute permissions:

```bash
chmod 555 script.sh
```

Meaning:

```text
User    → 5 → r-x
Group   → 5 → r-x
Others  → 5 → r-x
```

---

Give everyone full permissions:

```bash
chmod 777 file.txt
```

Meaning:

```text
User    → 7 → rwx
Group   → 7 → rwx
Others  → 7 → rwx
```

⚠️ Avoid using `777` unnecessarily because it gives everyone full access.

---

# 18. 👑 File Ownership

Every file has an owner and a group.

Example:

```text
-rw-r--r-- 1 rishika users notes.txt
```

Here:

```text
Owner → rishika
Group → users
```

---

# 19. 🔄 Changing Ownership

The `chown` command changes the owner of a file.

Example:

```bash
sudo chown alice notes.txt
```

Change owner and group:

```bash
sudo chown alice:developers notes.txt
```

---

# 20. 👥 Changing Group Ownership

The `chgrp` command changes the group ownership.

Example:

```bash
sudo chgrp developers notes.txt
```

---

# 21. 📁 Directory Permissions

Directory permissions work differently from file permissions.

```text
r → List contents
w → Create/delete/rename entries
x → Enter/access directory
```

Example:

```bash
chmod 755 Projects
```

Common directory permission:

```text
rwxr-xr-x
```

---

# 22. 🛡️ Permission Example

Suppose we have:

```text
-rwxr-x---
```

Breakdown:

```text
User:
rwx → Read + Write + Execute

Group:
r-x → Read + Execute

Others:
--- → No permissions
```

This means only the owner and group can access the file.

---

# 23. 🧠 Permission Calculation

Suppose we want:

```text
User:
Read + Write + Execute

Group:
Read + Execute

Others:
Read only
```

Calculate:

```text
User:
4 + 2 + 1 = 7

Group:
4 + 1 = 5

Others:
4 = 4
```

Therefore:

```bash
chmod 754 filename
```

Result:

```text
-rwxr-xr--
```

---

# 24. 🔒 Why Permissions Matter

Linux permissions help protect:

- Personal files
- System files
- Configuration files
- Application data
- Scripts
- Sensitive information

They prevent unauthorized users from modifying or accessing files.

---

# 25. ⚠️ Important Security Practice

Avoid using:

```bash
chmod 777
```

unless you completely understand why it is required.

Better:

```bash
chmod 755 script.sh
```

or:

```bash
chmod 644 notes.txt
```

Use the minimum permissions required.

This is called the:

> Principle of Least Privilege

---

# 26. 📊 Common Permission Modes

| Permission | Meaning |
|---|---|
| `600` | Owner read/write |
| `644` | Owner read/write, others read |
| `700` | Owner full access |
| `755` | Owner full access, others read/execute |
| `777` | Everyone full access |

---

# 27. 🧪 Practice

Create a file:

```bash
touch notes.txt
```

Check permissions:

```bash
ls -l notes.txt
```

Add execute permission:

```bash
chmod u+x notes.txt
```

Check again:

```bash
ls -l notes.txt
```

Set permissions to:

```text
rw-r--r--
```

Use:

```bash
chmod 644 notes.txt
```

Check:

```bash
ls -l notes.txt
```

---

# 🎯 Key Takeaways

- Linux uses permissions to control access.
- Permissions are divided among User, Group, and Others.
- `r` means read.
- `w` means write.
- `x` means execute.
- `ls -l` displays permissions.
- `chmod` changes permissions.
- `chown` changes ownership.
- `chgrp` changes group ownership.
- Numeric permissions use values 4, 2, and 1.
- `755` is a common permission for executable scripts and directories.
- `644` is a common permission for regular files.
- Avoid unnecessary `777` permissions.
- Use the Principle of Least Privilege.

---

# 🏆 Lesson Complete

You now understand the basics of Linux file permissions and ownership.

You can now:

```text
Read permissions
      ↓
Understand User / Group / Others
      ↓
Change permissions
      ↓
Change ownership
      ↓
Manage access securely
```

> 🐧 **Linux Quest — Level 02, Lesson 05 Complete**

> *Understand permissions. Control access. Secure the system.*

---

## 🔗 Navigation

⬅️ [Previous Lesson — File & Directory Management](./04-file-and-directory-management.md)

➡️ [Next Lesson — Coming Soon](#)

🖼️ [File Permissions & Ownership Diagram](../../assets/diagrams/file-permissions-and-ownership.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [File Permissions & Ownership Lab](../../labs/05-file-permissions-and-ownership-lab.md)

🏠 [Back to Linux Quest](../../README.md)