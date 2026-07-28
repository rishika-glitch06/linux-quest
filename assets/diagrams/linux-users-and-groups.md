# 🐧 Linux Users & Groups — Visual Guide

> A visual guide to understanding Linux users, groups, UID, GID, root, system identity files, and user management.

---

# 1. 👤 Linux Users

```text
                    LINUX SYSTEM
                         │
                         ▼
                      USERS
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
        Alice            Bob          Charlie
          │              │              │
          ▼              ▼              ▼
        UID 1001       UID 1002       UID 1003
```

Every Linux user has a unique **UID (User ID)**.

---

# 2. 👥 Linux Groups

```text
                     GROUP
                       │
                       ▼
                 developers
                       │
            ┌──────────┼──────────┐
            │          │          │
            ▼          ▼          ▼
          Alice       Bob       Charlie
```

Groups allow administrators to manage permissions for multiple users together.

---

# 3. 🆔 UID and GID

```text
                 LINUX IDENTITY
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
            UID                 GID
             │                   │
             ▼                   ▼
        User Identity       Group Identity
             │                   │
             ▼                   ▼
        Identifies User     Identifies Group
```

Example:

```text
uid=1000(rishika)
gid=1000(rishika)
```

---

# 4. 👤 User Identity

```text
                    USER
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
      Name           UID          Home
        │            │            │
        ▼            ▼            ▼
     rishika        1000      /home/rishika
```

---

# 5. 👥 User and Group Relationship

```text
                       USER
                        │
                        ▼
                     Alice
                        │
             ┌──────────┴──────────┐
             │                     │
             ▼                     ▼
       Primary Group       Secondary Groups
             │                     │
             ▼              ┌──────┴──────┐
        developers           │             │
                             ▼             ▼
                           docker         sudo
```

A user can have:

```text
1 Primary Group
+
Multiple Secondary Groups
```

---

# 6. ⭐ Primary Group

```text
                     Alice
                       │
                       ▼
               Primary Group
                       │
                       ▼
                  developers
```

Every user has a primary group.

Check with:

```bash
id alice
```

---

# 7. ➕ Secondary Groups

```text
                     Alice
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
      developers      docker       sudo
       Secondary      Secondary    Secondary
        Group          Group        Group
```

Check group membership:

```bash
groups alice
```

---

# 8. 👑 Root User

```text
                    ROOT
                     │
                     ▼
                   UID 0
                     │
          ┌──────────┼──────────┐
          │          │          │
          ▼          ▼          ▼
       System      Users      Files
      Management  Management  Management
          │          │          │
          └──────────┼──────────┘
                     │
                     ▼
              High Privileges
```

Root is the superuser.

```text
root → UID 0
```

---

# 9. 🛡️ Normal User vs Root

```text
                 USER TYPES
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
       Normal User            Root
             │                 │
             ▼                 ▼
       Limited Access      High Privileges
             │                 │
             ▼                 ▼
       Uses sudo when      Direct system
       authorized          administration
```

---

# 10. 📄 `/etc/passwd`

The `/etc/passwd` file stores basic user account information.

```text
                 /etc/passwd
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
       Username       UID          GID
          │            │            │
          ▼            ▼            ▼
      User Name    User ID      Primary Group
                       │
                       ▼
                Home Directory
                       │
                       ▼
                 Login Shell
```

Example:

```text
rishika:x:1000:1000:Rishika:/home/rishika:/bin/bash
```

Structure:

```text
username
   :
password placeholder
   :
UID
   :
GID
   :
user information
   :
home directory
   :
login shell
```

---

# 11. 🔐 `/etc/shadow`

```text
                 /etc/shadow
                       │
                       ▼
             Password Information
                       │
                       ▼
              Authentication Data
                       │
                       ▼
               Restricted Access
```

Conceptual relationship:

```text
/etc/passwd
     │
     └── Basic User Information


/etc/shadow
     │
     └── Password-related Information
```

`/etc/shadow` contains sensitive authentication information and should be protected.

---

# 12. 👥 `/etc/group`

```text
                  /etc/group
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
      Group Name      GID        Members
          │            │            │
          ▼            ▼            ▼
     developers      1001      alice,bob
```

Example:

```text
developers:x:1001:alice,bob
```

---

# 13. 🧩 Linux Identity Files

```text
                    USER & GROUP DATA
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
       /etc/passwd    /etc/shadow    /etc/group
             │             │             │
             ▼             ▼             ▼
        User Details   Password Data   Group Details
```

---

# 14. 🔍 `whoami`

```text
                    whoami
                       │
                       ▼
              Current User Identity
                       │
                       ▼
                    rishika
```

Command:

```bash
whoami
```

---

# 15. 🆔 `id`

```text
                      id
                       │
                       ▼
                User Identity
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
            UID                 GID
             │                   │
             ▼                   ▼
        User Identity       Primary Group
             │                   │
             └─────────┬─────────┘
                       │
                       ▼
                 Group Membership
```

Command:

```bash
id
```

---

# 16. 👀 Logged-in Users

```text
              Logged-in Users
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
       who           w          users
        │            │            │
        ▼            ▼            ▼
     Basic        Detailed      Usernames
    Information   Information    Only
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

# 17. ➕ Creating a User

```text
                  CREATE USER
                       │
                       ▼
                  useradd
                       │
                       ▼
                New User Account
                       │
                       ▼
                Assign Identity
                       │
                       ▼
                   UID / GID
```

Example:

```bash
sudo useradd alice
```

---

# 18. 🏠 User with Home Directory

```text
                useradd -m alice
                       │
                       ▼
                 Create User
                       │
                       ▼
              Create Home Directory
                       │
                       ▼
                  /home/alice
```

Command:

```bash
sudo useradd -m alice
```

---

# 19. 🔑 Set User Password

```text
                  New User
                     │
                     ▼
                  passwd
                     │
                     ▼
              Set Password
                     │
                     ▼
              Authentication
```

Command:

```bash
sudo passwd alice
```

---

# 20. ✏️ Modify User

```text
                  Existing User
                        │
                        ▼
                     usermod
                        │
              ┌─────────┼─────────┐
              │         │         │
              ▼         ▼         ▼
           Groups      Shell     Other
```

Example:

```bash
sudo usermod -s /bin/bash alice
```

---

# 21. ➕ Add User to Group

```text
                     Alice
                       │
                       ▼
              usermod -aG developers
                       │
                       ▼
                  developers
                       │
                       ▼
                  Alice Member
```

Command:

```bash
sudo usermod -aG developers alice
```

Meaning:

```text
-a → Append
-G → Secondary Group
```

---

# 22. ➖ Remove User from Group

```text
                Alice
                  │
                  ▼
        Member of developers
                  │
                  ▼
        gpasswd -d alice developers
                  │
                  ▼
         Removed from Group
```

Command:

```bash
sudo gpasswd -d alice developers
```

---

# 23. ❌ Delete User

```text
                 Existing User
                       │
                       ▼
                    userdel
                       │
                       ▼
                User Account Removed
```

Command:

```bash
sudo userdel alice
```

To remove the home directory too:

```bash
sudo userdel -r alice
```

⚠️ Use carefully.

---

# 24. ➕ Create Group

```text
                  CREATE GROUP
                       │
                       ▼
                    groupadd
                       │
                       ▼
                 New Group
                       │
                       ▼
                  developers
```

Command:

```bash
sudo groupadd developers
```

---

# 25. ✏️ Modify Group

```text
                 Existing Group
                       │
                       ▼
                    groupmod
                       │
                       ▼
               Change Group Name
```

Example:

```bash
sudo groupmod -n programmers developers
```

Result:

```text
developers
      │
      ▼
programmers
```

---

# 26. ❌ Delete Group

```text
                 Existing Group
                       │
                       ▼
                    groupdel
                       │
                       ▼
                 Group Removed
```

Command:

```bash
sudo groupdel developers
```

---

# 27. 🛡️ sudo

```text
                    Normal User
                         │
                         ▼
                       sudo
                         │
                         ▼
              Temporary Elevated Access
                         │
                         ▼
               Execute Authorized Command
```

Example:

```bash
sudo apt update
```

---

# 28. 👑 Root vs sudo

```text
                    Privileged Access
                           │
                 ┌─────────┴─────────┐
                 │                   │
                 ▼                   ▼
                root                sudo
                 │                   │
                 ▼                   ▼
          Full privileges      Temporary elevated
                               privileges
                 │                   │
                 ▼                   ▼
         Direct administration   Authorized command
```

---

# 29. 🔄 Complete User Management Workflow

```text
                  USER MANAGEMENT
                        │
                        ▼
                  Create User
                        │
                        ▼
                useradd / adduser
                        │
                        ▼
                 Set Password
                        │
                        ▼
                     passwd
                        │
                        ▼
                 Create Group
                        │
                        ▼
                   groupadd
                        │
                        ▼
              Add User to Group
                        │
                        ▼
                    usermod
                        │
                        ▼
                   Verify
                        │
                        ▼
                  id / groups
```

---

# 30. 🧠 User and Group Management Map

```text
                         LINUX
                           │
              ┌────────────┴────────────┐
              │                         │
              ▼                         ▼
            USERS                     GROUPS
              │                         │
      ┌───────┼───────┐         ┌───────┼───────┐
      │       │       │         │       │       │
      ▼       ▼       ▼         ▼       ▼       ▼
   useradd usermod userdel   groupadd groupmod groupdel
      │       │       │         │       │       │
      └───────┴───────┘         └───────┴───────┘
              │                         │
              └────────────┬────────────┘
                           │
                           ▼
                     ACCESS CONTROL
```

---

# 31. 🔗 User → Group → Permissions

```text
                       USER
                         │
                         ▼
                       GROUP
                         │
                         ▼
                  File Ownership
                         │
                         ▼
                    Permissions
                         │
                 ┌───────┼───────┐
                 │       │       │
                 ▼       ▼       ▼
                 r       w       x
                 │       │       │
                 ▼       ▼       ▼
               Read    Write   Execute
```

This connects:

```text
User
  ↓
Group
  ↓
Ownership
  ↓
Permissions
  ↓
Access
```

---

# 32. 🔐 Identity and Access Control

```text
                 WHO ARE YOU?
                      │
                      ▼
                    UID
                      │
                      ▼
                WHAT GROUPS?
                      │
                      ▼
                    GID
                      │
                      ▼
              WHAT CAN YOU DO?
                      │
                      ▼
                 Permissions
                      │
                      ▼
                 File Access
```

---

# 33. 🏆 Complete Linux Identity Map

```text
                         LINUX IDENTITY
                               │
             ┌─────────────────┼─────────────────┐
             │                 │                 │
             ▼                 ▼                 ▼
           USER              GROUP             ROOT
             │                 │                 │
             ▼                 ▼                 ▼
            UID               GID              UID 0
             │                 │                 │
             └─────────────────┼─────────────────┘
                               │
                               ▼
                        ACCESS CONTROL
                               │
                               ▼
                          PERMISSIONS
                               │
                               ▼
                         SYSTEM SECURITY
```

---

# 34. 🎯 Quick Memory Map

```text
whoami
  ↓
Current User

id
  ↓
UID + GID + Groups

who
  ↓
Logged-in Users

w
  ↓
Detailed Login Information

groups
  ↓
Group Membership

useradd
  ↓
Create User

usermod
  ↓
Modify User

userdel
  ↓
Delete User

groupadd
  ↓
Create Group

groupmod
  ↓
Modify Group

groupdel
  ↓
Delete Group

passwd
  ↓
Set Password

sudo
  ↓
Elevated Privileges
```

---

# 35. 🧭 Final Visual Summary

```text
                    LINUX USERS & GROUPS
                              │
             ┌────────────────┼────────────────┐
             │                │                │
             ▼                ▼                ▼
           USERS            GROUPS            ROOT
             │                │                │
             ▼                ▼                ▼
            UID              GID              UID 0
             │                │                │
             └────────────────┼────────────────┘
                              │
                              ▼
                    /etc/passwd
                    /etc/shadow
                    /etc/group
                              │
                              ▼
                       ACCESS CONTROL
                              │
                              ▼
                       FILE PERMISSIONS
                              │
                              ▼
                          SECURITY
```

---

# 🎯 Key Takeaway

```text
             USER
               │
               ▼
              UID
               │
               ▼
             GROUP
               │
               ▼
              GID
               │
               ▼
          OWNERSHIP
               │
               ▼
         PERMISSIONS
               │
               ▼
            ACCESS
               │
               ▼
           SECURITY
```

> 🐧 **Linux Quest — Level 02, Lesson 06**

> *Understand identities. Manage users. Control access. Secure the system.*

---

## 🔗 Related Resources

📖 [Lesson 06 — Linux Users & Groups](../../levels/level-02-file-system/06-linux-users-and-groups.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [Linux Users & Groups Lab](../../labs/06-linux-users-and-groups-lab.md)

🏠 [Back to Linux Quest](../../README.md)