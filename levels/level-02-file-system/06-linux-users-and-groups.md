# 🐧 Lesson 06 — Linux Users & Groups

> Learn how Linux manages users, groups, identities, and access control.

---

# 🎯 Learning Objectives

By the end of this lesson, you will understand:

- Linux users
- Linux groups
- User IDs (UID)
- Group IDs (GID)
- Root user
- `/etc/passwd`
- `/etc/group`
- `/etc/shadow`
- `whoami`
- `id`
- `who`
- `w`
- `users`
- `groups`
- `useradd`
- `adduser`
- `usermod`
- `userdel`
- `groupadd`
- `groupmod`
- `groupdel`
- Primary and secondary groups
- `sudo`
- User and group management

---

# 1. 👤 What Is a User?

A user in Linux represents an identity that can interact with the operating system.

A user can:

- Access files
- Run commands
- Own files
- Run processes
- Access specific resources

Each user has a unique identity.

---

# 2. 👥 What Is a Group?

A group is a collection of users.

Groups make permission management easier.

Instead of assigning permissions to individual users, administrators can assign permissions to a group.

Example:

```text
              Developers Group
                     │
          ┌──────────┼──────────┐
          │          │          │
          ▼          ▼          ▼
        Alice       Bob       Charlie
```

All members can receive permissions assigned to the `developers` group.

---

# 3. 🆔 UID — User ID

Every Linux user has a unique numeric identifier called a UID.

Check your UID:

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

The UID identifies a user internally.

---

# 4. 🆔 GID — Group ID

Every Linux group has a unique numeric identifier called a GID.

Check your group information:

```bash
id
```

Example:

```text
uid=1000(rishika) gid=1000(rishika) groups=1000(rishika)
```

Here:

```text
UID → 1000
GID → 1000
```

---

# 5. 👑 Root User

The root user is the superuser in Linux.

Root has extensive privileges and can:

- Modify system files
- Create users
- Delete users
- Change ownership
- Change permissions
- Install software
- Manage system services

Root's UID is:

```text
0
```

Check:

```bash
id root
```

---

# 6. 🔍 `whoami`

The `whoami` command displays the current user.

```bash
whoami
```

Example:

```text
rishika
```

---

# 7. 🆔 `id`

The `id` command displays user and group identity information.

Run:

```bash
id
```

Example:

```text
uid=1000(rishika) gid=1000(rishika) groups=1000(rishika)
```

You can also check another user:

```bash
id username
```

---

# 8. 👀 `who`

The `who` command shows users currently logged into the system.

```bash
who
```

---

# 9. 📊 `w`

The `w` command provides more detailed information about logged-in users.

```bash
w
```

It can display:

- Username
- Terminal
- Login time
- Idle time
- Current activity

---

# 10. 👥 `users`

The `users` command displays the usernames of currently logged-in users.

```bash
users
```

---

# 11. 👥 `groups`

The `groups` command shows the groups a user belongs to.

For the current user:

```bash
groups
```

For another user:

```bash
groups username
```

---

# 12. 📄 `/etc/passwd`

The `/etc/passwd` file stores basic information about Linux users.

View it:

```bash
cat /etc/passwd
```

A typical entry looks like:

```text
rishika:x:1000:1000:Rishika:/home/rishika:/bin/bash
```

The fields are separated by `:`.

Structure:

```text
username
   │
   ▼
password placeholder
   │
   ▼
UID
   │
   ▼
GID
   │
   ▼
User information
   │
   ▼
Home directory
   │
   ▼
Login shell
```

---

# 13. 🔐 `/etc/shadow`

The `/etc/shadow` file stores password-related information.

View it:

```bash
sudo cat /etc/shadow
```

It contains sensitive authentication information.

Therefore:

```text
/etc/passwd
    │
    └── General user information

/etc/shadow
    │
    └── Password-related information
```

Access to `/etc/shadow` is restricted.

---

# 14. 👥 `/etc/group`

The `/etc/group` file stores group information.

View it:

```bash
cat /etc/group
```

Example:

```text
developers:x:1001:alice,bob
```

This represents:

```text
Group:
developers

GID:
1001

Members:
alice
bob
```

---

# 15. 🔄 User and Group Relationship

```text
                    Linux System
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
            Users                 Groups
              │                     │
      ┌───────┼───────┐             │
      │       │       │             │
      ▼       ▼       ▼             ▼
    Alice    Bob    Charlie     Developers
                                  │
                         ┌────────┼────────┐
                         │        │        │
                         ▼        ▼        ▼
                       Alice     Bob    Charlie
```

---

# 16. ⭐ Primary Group

Every Linux user has a primary group.

Check using:

```bash
id username
```

Example:

```text
uid=1000(rishika) gid=1000(rishika)
```

The `gid` represents the primary group.

---

# 17. ➕ Secondary Groups

A user can belong to additional groups.

Example:

```text
User: rishika

Primary Group:
rishika

Secondary Groups:
developers
docker
sudo
```

Check:

```bash
groups
```

---

# 18. ➕ Creating a User

The `useradd` command creates a new user.

Example:

```bash
sudo useradd alice
```

Check:

```bash
id alice
```

---

# 19. 🏠 Creating a User with Home Directory

Use:

```bash
sudo useradd -m alice
```

The `-m` option creates a home directory.

Example:

```text
/home/alice
```

---

# 20. 🔑 Setting a Password

Use:

```bash
sudo passwd alice
```

You will be asked to enter a password.

---

# 21. 👤 `adduser`

On many Debian-based systems, `adduser` provides a more interactive way to create users.

Example:

```bash
sudo adduser alice
```

It may ask for:

- Password
- Full name
- User information

---

# 22. ✏️ Modifying a User

The `usermod` command modifies an existing user.

Example:

```bash
sudo usermod -s /bin/bash alice
```

This changes the user's login shell.

---

# 23. 👥 Adding a User to a Group

Use:

```bash
sudo usermod -aG developers alice
```

Meaning:

```text
-a → Append
-G → Secondary group
```

Verify:

```bash
groups alice
```

⚠️ The `-a` option is important because without it, existing supplementary groups may be replaced.

---

# 24. ➖ Removing a User from a Group

On many Linux systems:

```bash
sudo gpasswd -d alice developers
```

Verify:

```bash
groups alice
```

---

# 25. ❌ Deleting a User

Use:

```bash
sudo userdel alice
```

This removes the user account.

To also remove the user's home directory:

```bash
sudo userdel -r alice
```

⚠️ Use carefully because deleting the home directory can permanently remove user data.

---

# 26. ➕ Creating a Group

Use:

```bash
sudo groupadd developers
```

Verify:

```bash
getent group developers
```

---

# 27. ✏️ Modifying a Group

Use:

```bash
sudo groupmod -n programmers developers
```

This renames:

```text
developers
```

to:

```text
programmers
```

---

# 28. ❌ Deleting a Group

Use:

```bash
sudo groupdel developers
```

⚠️ Make sure the group is no longer required before deleting it.

---

# 29. 🛡️ `sudo`

`sudo` allows authorized users to execute commands with elevated privileges.

Example:

```bash
sudo apt update
```

The user does not necessarily become root permanently.

Instead, `sudo` provides temporary elevated privileges for the command.

---

# 30. 🔐 Root vs Sudo

```text
Root
 │
 └── Full administrative privileges

Sudo
 │
 └── Temporary elevated privileges
     for authorized commands
```

Using `sudo` is generally safer than operating as root all the time.

---

# 31. 🧠 Important User Management Commands

| Command | Purpose |
|---|---|
| `whoami` | Show current user |
| `id` | Show UID and GID information |
| `who` | Show logged-in users |
| `w` | Detailed logged-in user information |
| `users` | Show logged-in usernames |
| `groups` | Show group membership |
| `useradd` | Create user |
| `adduser` | Interactive user creation |
| `usermod` | Modify user |
| `userdel` | Delete user |
| `groupadd` | Create group |
| `groupmod` | Modify group |
| `groupdel` | Delete group |
| `passwd` | Change user password |
| `chage` | Manage password aging |
| `sudo` | Execute command with elevated privileges |

---

# 32. 🔄 User Management Workflow

```text
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
Create / Assign Groups
    │
    ▼
usermod
    │
    ▼
Verify Identity
    │
    ▼
id / groups
```

---

# 33. 🔐 Linux Identity Files

```text
                    Linux Identity
                          │
          ┌───────────────┼───────────────┐
          │               │               │
          ▼               ▼               ▼
     /etc/passwd     /etc/shadow      /etc/group
          │               │               │
          ▼               ▼               ▼
     User Details     Password Data    Group Details
```

---

# 34. 🧠 Security Best Practices

Follow these practices:

- Use strong passwords.
- Avoid unnecessary root access.
- Use `sudo` carefully.
- Give users only required permissions.
- Remove unused accounts.
- Review group memberships.
- Protect `/etc/shadow`.
- Avoid sharing user accounts.
- Regularly review privileged users.

---

# 35. 🎯 Key Takeaways

- Linux identifies users using UIDs.
- Linux identifies groups using GIDs.
- Root has UID `0`.
- `/etc/passwd` stores basic user information.
- `/etc/shadow` stores password-related information.
- `/etc/group` stores group information.
- Users can have primary and secondary groups.
- `useradd` creates users.
- `usermod` modifies users.
- `userdel` removes users.
- `groupadd` creates groups.
- `groupmod` modifies groups.
- `groupdel` removes groups.
- `sudo` provides controlled elevated privileges.

---

# 🏆 Lesson Complete

You now understand how Linux manages:

```text
Users
  ↓
Groups
  ↓
UID / GID
  ↓
Ownership
  ↓
Access Control
  ↓
System Security
```

> 🐧 **Linux Quest — Level 02, Lesson 06 Complete**

> *Understand identities. Manage users. Secure the system.*

---

## 🔗 Navigation

⬅️ [Previous Lesson — File Permissions & Ownership](./05-file-permissions-and-ownership.md)

➡️ [Next Lesson — Coming Soon](#)

🖼️ [Linux Users & Groups Diagram](../../assets/diagrams/linux-users-and-groups.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [Linux Users & Groups Lab](../../labs/06-linux-users-and-groups-lab.md)

🏠 [Back to Linux Quest](../../README.md)