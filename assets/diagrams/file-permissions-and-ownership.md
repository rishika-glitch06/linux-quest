# 🔐 Linux File Permissions & Ownership

> A visual guide to understanding Linux permissions, users, groups, ownership, and access control.

---

# 1. 🧩 Linux Permission Structure

```text
                 Linux File Permissions
                          │
                          ▼
                  -rwxr-xr--
                          │
          ┌───────────────┼───────────────┐
          │               │               │
          ▼               ▼               ▼
        USER            GROUP           OTHERS
          │               │               │
          ▼               ▼               ▼
        rwx             r-x             r--
          │               │               │
          ▼               ▼               ▼
   Read + Write +    Read + Execute    Read Only
      Execute
```

---

# 2. 📊 Permission Breakdown

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
-    rwx    r-x    r--
│     │      │      │
│     │      │      └── Others
│     │      └───────── Group
│     └──────────────── User / Owner
└────────────────────── File Type
```

---

# 3. 📁 File Type

The first character represents the type of file.

```text
-  → Regular File

d  → Directory

l  → Symbolic Link
```

Example:

```text
-rwxr-xr--
│
└── Regular File
```

Directory example:

```text
drwxr-xr-x
│
└── Directory
```

---

# 4. 🔐 Permission Types

```text
              Permissions
                   │
        ┌──────────┼──────────┐
        │          │          │
        ▼          ▼          ▼
       r           w          x
     Read        Write      Execute
        │          │          │
        ▼          ▼          ▼
   View Data    Modify Data   Run File
```

---

# 5. 👤 Permission Categories

Linux permissions apply to three categories:

```text
                    Permission Categories
                            │
             ┌──────────────┼──────────────┐
             │              │              │
             ▼              ▼              ▼
           User           Group          Others
            (u)            (g)            (o)
             │              │              │
             ▼              ▼              ▼
         File Owner    Group Members    Everyone Else
```

---

# 6. 🔢 Permission Numeric Values

Each permission has a numeric value:

```text
              Permission Values
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
       r = 4        w = 2        x = 1
      Read         Write       Execute
```

Add the values to create permission numbers.

```text
r-- = 4

-w- = 2

--x = 1

rw- = 4 + 2 = 6

r-x = 4 + 1 = 5

-wx = 2 + 1 = 3

rwx = 4 + 2 + 1 = 7
```

---

# 7. 🔢 Numeric Permission Flow

```text
                    chmod 754
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
          7            5            4
          │            │            │
          ▼            ▼            ▼
         rwx          r-x          r--
          │            │            │
          ▼            ▼            ▼
         User         Group        Others
```

Result:

```text
rwxr-xr--
```

---

# 8. 🔧 chmod

`chmod` is used to change permissions.

```text
                 chmod
                   │
                   ▼
          Change File Permissions
                   │
          ┌────────┴────────┐
          │                 │
          ▼                 ▼
      Symbolic            Numeric
       Mode                Mode
          │                 │
          ▼                 ▼
     chmod u+x         chmod 755
```

---

# 9. 🧩 Symbolic chmod

Symbolic permissions use:

```text
u → User
g → Group
o → Others
a → All
```

Operators:

```text
+ → Add Permission

- → Remove Permission

= → Set Exact Permission
```

Example:

```bash
chmod u+x script.sh
```

Flow:

```text
script.sh
    │
    ▼
chmod u+x
    │
    ▼
Add Execute Permission
    │
    ▼
For User / Owner
```

---

# 10. ➕ Adding Permissions

```text
chmod u+x script.sh
       │
       ├── u → User
       ├── + → Add
       └── x → Execute
```

Result:

```text
User gets Execute Permission
```

---

# 11. ➖ Removing Permissions

Example:

```bash
chmod o-w notes.txt
```

Breakdown:

```text
o → Others

- → Remove

w → Write
```

Result:

```text
Others lose Write Permission
```

---

# 12. 👑 File Ownership

Every file has:

```text
                 File Ownership
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
           Owner               Group
             │                   │
             ▼                   ▼
         User who           Group assigned
         owns file           to the file
```

Example:

```text
-rw-r--r-- 1 rishika developers notes.txt
                 │          │
                 │          │
                 ▼          ▼
               Owner      Group
```

---

# 13. 🔄 chown

`chown` changes the owner of a file.

```text
                 chown
                   │
                   ▼
             Change Owner
                   │
                   ▼
          sudo chown alice file
                   │
                   ▼
          Owner becomes alice
```

To change owner and group:

```bash
sudo chown alice:developers notes.txt
```

Flow:

```text
notes.txt
    │
    ▼
chown alice:developers
    │
    ├── Owner → alice
    │
    └── Group → developers
```

---

# 14. 👥 chgrp

`chgrp` changes group ownership.

```text
                 chgrp
                   │
                   ▼
             Change Group
                   │
                   ▼
       sudo chgrp developers notes.txt
                   │
                   ▼
           Group becomes
             developers
```

---

# 15. 🔐 chmod vs chown vs chgrp

```text
                   File Management
                         │
            ┌────────────┼────────────┐
            │            │            │
            ▼            ▼            ▼
          chmod         chown        chgrp
            │            │            │
            ▼            ▼            ▼
       Permissions      Owner        Group
            │            │            │
            ▼            ▼            ▼
        rwx access    User owns     Group owns
```

---

# 16. 📁 Directory Permissions

Directory permissions work differently.

```text
               Directory Permissions
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
         r             w            x
       Read          Write        Execute
          │            │            │
          ▼            ▼            ▼
    List contents   Create/Delete   Enter/
                   Rename entries   Access
```

---

# 17. 🧠 File vs Directory Permissions

```text
              Permission Meaning
                     │
             ┌───────┴───────┐
             │               │
             ▼               ▼
            File          Directory
             │               │
       ┌─────┼─────┐   ┌─────┼─────┐
       │     │     │   │     │     │
       ▼     ▼     ▼   ▼     ▼     ▼
       r     w     x   r     w     x
       │     │     │   │     │     │
       ▼     ▼     ▼   ▼     ▼     ▼
      Read  Edit  Run List  Modify Enter
```

---

# 18. 📊 Common Permission Modes

```text
600
│
└── rw-------
    Owner: Read + Write

644
│
└── rw-r--r--
    Owner: Read + Write
    Group: Read
    Others: Read

700
│
└── rwx------
    Owner: Full Access

755
│
└── rwxr-xr-x
    Owner: Full Access
    Group: Read + Execute
    Others: Read + Execute

777
│
└── rwxrwxrwx
    Everyone: Full Access
```

---

# 19. ⚠️ chmod 777 Warning

```text
                 chmod 777
                     │
                     ▼
              User → Full Access
                     │
                     ▼
             Group → Full Access
                     │
                     ▼
            Others → Full Access
                     │
                     ▼
                  ⚠️ Risk
```

Avoid using:

```bash
chmod 777
```

unless absolutely necessary.

Follow:

> Principle of Least Privilege

Give users only the permissions they actually need.

---

# 20. 🛡️ Principle of Least Privilege

```text
                  Least Privilege
                        │
                        ▼
             Give Minimum Required
                  Permissions
                        │
          ┌─────────────┼─────────────┐
          │             │             │
          ▼             ▼             ▼
         Read          Write        Execute
          │             │             │
          ▼             ▼             ▼
       If Needed      If Needed      If Needed
```

The goal is:

```text
Minimum Permissions
        │
        ▼
Reduced Risk
        │
        ▼
Better Security
```

---

# 21. 🔍 Complete Permission Workflow

```text
                 Create File
                      │
                      ▼
                 ls -l file
                      │
                      ▼
              Check Permissions
                      │
                      ▼
                Need Change?
                      │
              ┌───────┴───────┐
              │               │
             YES              NO
              │               │
              ▼               ▼
            chmod          Continue
              │
              ▼
       Check Permissions
              │
              ▼
           ls -l
```

---

# 22. 🧭 Complete Ownership Workflow

```text
                File / Directory
                       │
                       ▼
                  Check Owner
                       │
                       ▼
                   ls -l
                       │
                       ▼
             Need Owner Change?
                       │
                       ▼
                     chown
                       │
                       ▼
              Owner Updated
                       │
                       ▼
                  Verify
                       │
                       ▼
                    ls -l
```

---

# 23. 🏆 Quick Memory Map

```text
r → Read
w → Write
x → Execute

u → User
g → Group
o → Others
a → All

chmod → Change Permissions

chown → Change Owner

chgrp → Change Group

4 → Read
2 → Write
1 → Execute
```

---

# 24. 🎯 Final Permission Map

```text
                    LINUX ACCESS CONTROL
                            │
            ┌───────────────┴───────────────┐
            │                               │
            ▼                               ▼
       PERMISSIONS                       OWNERSHIP
            │                               │
     ┌──────┼──────┐                 ┌──────┴──────┐
     │      │      │                 │             │
     ▼      ▼      ▼                 ▼             ▼
     r      w      x               Owner         Group
     │      │      │                 │             │
     ▼      ▼      ▼                 ▼             ▼
   Read   Write  Execute           chown         chgrp
     │      │      │
     └──────┼──────┘
            │
            ▼
          chmod
```

---

# 🎯 Key Takeaway

```text
             Linux Permissions
                    │
       ┌────────────┼────────────┐
       │            │            │
       ▼            ▼            ▼
     User          Group        Others
       │            │            │
       └────────────┼────────────┘
                    │
                    ▼
               r / w / x
                    │
                    ▼
                 chmod
                    │
                    ▼
              Access Control
                    │
                    ▼
                Security
```

---

## 🔗 Related Resources

📖 [Lesson 05 — File Permissions & Ownership](../../levels/level-02-file-system/05-file-permissions-and-ownership.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [File Permissions & Ownership Lab](../../labs/05-file-permissions-and-ownership-lab.md)

🏠 [Back to Linux Quest](../../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 05**

> *Understand permissions. Control access. Secure the system.*