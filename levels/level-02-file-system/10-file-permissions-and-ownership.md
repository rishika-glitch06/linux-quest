# 🔐 Linux File Permissions & Ownership

> Learn how Linux controls access to files and directories using permissions, ownership, groups, chmod, chown, special permissions, and security principles.

---

# 🎯 Learning Objectives

By completing this lesson, you will understand:

- Linux file permissions
- User, Group, and Others
- Read, Write, and Execute permissions
- Permission strings
- Numeric permission system
- Symbolic permission system
- `chmod`
- `chown`
- `chgrp`
- File ownership
- Directory permissions
- `umask`
- SUID
- SGID
- Sticky Bit
- Permission troubleshooting
- ACL basics
- Principle of Least Privilege

---

# 1. 🔐 What Are Linux File Permissions?

Linux uses a permission system to control access to files and directories.

Every file and directory has:

    Owner
    Group
    Permissions

Permissions determine what users can do with a file or directory.

The three basic permissions are:

    r → Read
    w → Write
    x → Execute

The three permission categories are:

    User / Owner
    Group
    Others

---

# 2. 👤 User, Group, and Others

Linux permissions are divided into three categories.

## User / Owner

The user who owns the file.

Represented by:

    u

---

## Group

Users belonging to the file's group.

Represented by:

    g

---

## Others

All other users.

Represented by:

    o

---

## Example

Consider:

    -rwxr-xr--

Breakdown:

    - | rwx | r-x | r--
      |     |     |
      |     |     └── Others
      |     └──────── Group
      └────────────── Owner

Therefore:

    Owner  → rwx
    Group  → r-x
    Others → r--

---

# 3. 📖 Read Permission

Read permission is represented by:

    r

Numeric value:

    4

For files:

    Read → View file contents

Example:

    cat file.txt

For directories:

    Read → List directory contents

Example:

    ls directory/

---

# 4. ✏️ Write Permission

Write permission is represented by:

    w

Numeric value:

    2

For files:

    Write → Modify file contents

For directories:

    Write → Create, delete, or rename entries

Important:

Directory write permission does not automatically mean you can access the contents.

You generally also need execute permission on the directory.

---

# 5. ⚙️ Execute Permission

Execute permission is represented by:

    x

Numeric value:

    1

For files:

    Execute → Run the file as a program

For directories:

    Execute → Enter or traverse the directory

Example:

    cd directory/

---

# 6. 📊 Permission Values

Linux uses numeric values for permissions.

| Permission | Value |
|---|---:|
| `---` | 0 |
| `--x` | 1 |
| `-w-` | 2 |
| `-wx` | 3 |
| `r--` | 4 |
| `r-x` | 5 |
| `rw-` | 6 |
| `rwx` | 7 |

The values are:

    Read    = 4
    Write   = 2
    Execute = 1

---

# 7. 🧮 Understanding Numeric Permissions

Permissions are calculated by adding values.

Example:

    rwx

    r = 4
    w = 2
    x = 1

    4 + 2 + 1 = 7

Therefore:

    rwx = 7

---

Example:

    r-x

    r = 4
    x = 1

    4 + 1 = 5

Therefore:

    r-x = 5

---

Example:

    rw-

    r = 4
    w = 2

    4 + 2 = 6

Therefore:

    rw- = 6

---

# 8. 🔍 Understanding Permission Strings

Example:

    -rwxr-xr--

Break it down:

    -     → File Type
    rwx   → Owner
    r-x   → Group
    r--   → Others

The permission value is:

    rwx = 7
    r-x = 5
    r-- = 4

Therefore:

    754

---

# 9. 📁 File Type Indicator

The first character of the permission string represents the file type.

Examples:

    -  → Regular file
    d  → Directory
    l  → Symbolic link
    c  → Character device
    b  → Block device
    s  → Socket
    p  → Named pipe

Example:

    -rw-r--r--

The first character:

    -

means it is a regular file.

Example:

    drwxr-xr-x

The first character:

    d

means it is a directory.

---

# 10. 🔎 Checking Permissions

Use:

    ls -l

Example:

    ls -l file.txt

Output:

    -rw-r--r-- 1 rishika developers 100 file.txt

This shows:

    Permissions → -rw-r--r--
    Owner       → rishika
    Group       → developers
    File        → file.txt

For a directory itself:

    ls -ld directory/

---

# 11. 🛠️ chmod

`chmod` means:

    Change Mode

It is used to change file and directory permissions.

Syntax:

    chmod [permissions] [file]

Example:

    chmod 755 script.sh

---

# 12. 🔢 Numeric chmod

Numeric permissions use values from 0 to 7.

Example:

    chmod 755 script.sh

Means:

    7 → Owner
    5 → Group
    5 → Others

Therefore:

    Owner  → rwx
    Group  → r-x
    Others → r-x

Final:

    rwxr-xr-x

---

# 13. 📊 Common chmod Values

## chmod 600

    chmod 600 secret.txt

Permissions:

    Owner  → rw-
    Group  → ---
    Others → ---

Used for:

    Private files
    Sensitive information
    Private keys

---

## chmod 644

    chmod 644 file.txt

Permissions:

    Owner  → rw-
    Group  → r--
    Others → r--

Common for:

    Regular files
    Text files
    Web files

---

## chmod 700

    chmod 700 private/

Permissions:

    Owner  → rwx
    Group  → ---
    Others → ---

Used for:

    Private directories

---

## chmod 755

    chmod 755 script.sh

Permissions:

    Owner  → rwx
    Group  → r-x
    Others → r-x

Common for:

    Executable scripts
    Public directories

---

## chmod 775

    chmod 775 project/

Permissions:

    Owner  → rwx
    Group  → rwx
    Others → r-x

Useful for:

    Shared project directories

---

## chmod 777

    chmod 777 file

Permissions:

    Owner  → rwx
    Group  → rwx
    Others → rwx

Everyone has full access.

⚠️ This is generally insecure and should be avoided unless there is a specific reason.

---

# 14. ✏️ Symbolic chmod

Instead of numbers, permissions can be modified symbolically.

Users:

    u → User
    g → Group
    o → Others
    a → All

Operators:

    + → Add permission
    - → Remove permission
    = → Set permission

Examples:

    chmod u+x script.sh

Add execute permission to owner.

    chmod g+w file.txt

Add write permission to group.

    chmod o-r file.txt

Remove read permission from others.

    chmod a+x script.sh

Add execute permission for everyone.

---

# 15. 🧠 chmod Examples

Add execute:

    chmod +x script.sh

Remove execute:

    chmod -x script.sh

Give owner full access:

    chmod u+rwx file.txt

Remove group write:

    chmod g-w file.txt

Give others read:

    chmod o+r file.txt

Set exact permissions:

    chmod u=rw,g=r,o= file.txt

---

# 16. 👑 File Ownership

Every Linux file has:

    Owner
    Group

Example:

    -rw-r--r-- 1 rishika developers file.txt

Here:

    Owner = rishika
    Group = developers

Permissions are applied based on ownership.

---

# 17. 🔄 chown

`chown` means:

    Change Owner

Syntax:

    chown user file

Example:

    sudo chown rishika file.txt

Change owner and group:

    sudo chown rishika:developers file.txt

---

# 18. 👥 chgrp

`chgrp` means:

    Change Group

Example:

    sudo chgrp developers file.txt

This changes the group ownership.

---

# 19. 🔁 Recursive Ownership

The `-R` option applies changes recursively.

Example:

    sudo chown -R rishika:developers project/

This changes ownership of:

    project/
    All files
    All subdirectories

Use recursive commands carefully.

---

# 20. 📂 File vs Directory Permissions

Permissions behave differently for files and directories.

## File

    r → Read contents
    w → Modify contents
    x → Execute

## Directory

    r → List contents
    w → Create/Delete/Rename entries
    x → Enter/Traverse

---

# 21. 🚫 Permission Denied

You may see:

    Permission denied

This means the current user does not have sufficient access.

Possible causes:

    Missing read permission
    Missing write permission
    Missing execute permission
    Wrong ownership
    Wrong group
    Parent directory restrictions
    ACL restrictions
    SELinux/AppArmor restrictions
    Read-only filesystem

---

# 22. 🔎 Permission Troubleshooting

Check current user:

    whoami

Check user and groups:

    id

Check file:

    ls -l file.txt

Check directory:

    ls -ld directory/

Check detailed metadata:

    stat file.txt

Check permissions along path:

    namei -l /path/to/file

Always identify the actual problem before changing permissions.

Avoid blindly using:

    chmod 777

---

# 23. 🧮 umask

`umask` controls default permissions for newly created files and directories.

Check current umask:

    umask

Example:

    0022

Typical base permissions:

    Files       → 666
    Directories → 777

With a typical `022` umask:

    New File       → 644
    New Directory  → 755

The exact calculation is based on permission bits.

---

# 24. 📄 Why Files Do Not Get Execute Permission by Default

New files typically start from:

    666

This means:

    rw-rw-rw-

Execute permission is not included.

This prevents newly created files from automatically becoming executable.

Directories typically start from:

    777

The `umask` then removes permissions according to system configuration.

---

# 25. 🔴 SUID

SUID means:

    Set User ID

When applied to an executable file, the program runs with the privileges of the file owner.

Example:

    -rwsr-xr-x

The `s` appears in the owner's execute position.

Set SUID:

    chmod u+s file

Numeric form:

    chmod 4755 file

SUID programs should be carefully managed because vulnerabilities in privileged programs can create security risks.

---

# 26. 🟡 SGID

SGID means:

    Set Group ID

For executable files:

The program runs with the privileges of the file's group.

For directories:

New files and directories inherit the directory's group ownership.

Set SGID:

    chmod g+s directory/

Numeric form:

    chmod 2775 directory/

Example:

    drwxrwsr-x

The `s` in the group execute position represents SGID.

---

# 27. 🟢 Sticky Bit

Sticky Bit is commonly used on shared writable directories.

It prevents users from deleting or renaming files owned by other users in the directory, subject to the usual ownership and privilege rules.

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

# 28. 📊 Special Permissions

Linux has three major special permission bits.

| Permission | Numeric Value | Purpose |
|---|---:|---|
| SUID | 4 | Run executable with owner's privileges |
| SGID | 2 | Run with group privileges / inherit group |
| Sticky Bit | 1 | Restrict deletion in shared directories |

Examples:

    4755 → SUID + 755

    2775 → SGID + 775

    1777 → Sticky Bit + 777

---

# 29. 🧠 SUID vs SGID vs Sticky Bit

    SUID
      │
      ▼
    Owner Privileges

    SGID
      │
      ▼
    Group Privileges
    or Group Inheritance

    Sticky Bit
      │
      ▼
    Restrict File Deletion

---

# 30. 🛡️ Principle of Least Privilege

The Principle of Least Privilege means:

A user or process should have only the permissions required to perform its task.

Example:

Instead of:

    chmod 777 secret.txt

Use:

    chmod 600 secret.txt

Instead of giving everyone write access:

    Give only required users or groups access.

Security principle:

    Minimum Access
          ↓
    Lower Risk
          ↓
    Better Security

---

# 31. 🔐 Secure Permission Examples

Private file:

    chmod 600 secret.txt

Private directory:

    chmod 700 private/

Public readable file:

    chmod 644 file.txt

Executable script:

    chmod 755 script.sh

Shared project:

    chmod 775 project/

Shared temporary directory:

    chmod 1777 shared/

---

# 32. 📋 chmod vs chown vs chgrp

    chmod
       ↓
    Changes Permissions

    chown
       ↓
    Changes Owner

    chgrp
       ↓
    Changes Group

Example:

    chmod 755 script.sh

    sudo chown rishika script.sh

    sudo chgrp developers script.sh

---

# 33. 🧩 ACL — Access Control List

ACL stands for:

    Access Control List

Traditional Linux permissions provide access control for:

    Owner
    Group
    Others

ACLs provide more detailed access control.

For example, you can give a specific user access without changing the main owner.

View ACL:

    getfacl file.txt

Set ACL:

    setfacl -m u:username:r file.txt

ACLs are useful for complex access requirements.

---

# 34. 📊 Traditional Permissions vs ACL

Traditional permissions:

    Owner
    Group
    Others

ACL:

    Specific Users
    Specific Groups
    Additional Permissions

Therefore:

    Traditional Permissions
            ↓
       Simple Access

    ACL
            ↓
       Fine-Grained Access

---

# 35. 📁 Shared Directory Example

Suppose a development team uses:

    /project

The directory belongs to:

    developers

Set group ownership:

    sudo chown :developers /project

Give owner and group full access:

    chmod 2775 /project

The `2` enables SGID.

Now:

    New files inherit the developers group.

This makes collaborative project management easier.

---

# 36. 🗑️ Sticky Bit Example

Suppose multiple users share:

    /shared

Set:

    chmod 1777 /shared

Permissions:

    Owner  → rwx
    Group  → rwx
    Others → rwx

Sticky Bit:

    Enabled

Result:

Users can create files, but generally cannot delete or rename files owned by other users.

---

# 37. 🧠 Permission Decision Flow

```text
                User Requests Access
                        │
                        ▼
                 Identify User
                        │
                        ▼
                Check File Owner
                        │
             ┌──────────┴──────────┐
             │                     │
          Owner?                Not Owner
             │                     │
             ▼                     ▼
        Use Owner             Check Group
        Permissions                │
                              ┌────┴────┐
                              │         │
                           Member?   Not Member
                              │         │
                              ▼         ▼
                         Group Perms  Others
                                        │
                                        ▼
                                  Others Perms