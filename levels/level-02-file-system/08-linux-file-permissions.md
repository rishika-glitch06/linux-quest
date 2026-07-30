# 🐧 Linux Quest — Level 02
# Chapter 08: Linux File Permissions & Ownership

> Learn how Linux controls access to files and directories using permissions, ownership, groups, and special permission bits.

---

## 🎯 Learning Objectives

By the end of this chapter, you will understand:

- Linux file permission model
- User, Group, and Others
- Read, Write, and Execute permissions
- How to read `ls -l` output
- Numeric and symbolic permission notation
- `chmod` command
- `chown` command
- `chgrp` command
- File and directory permissions
- `umask`
- SUID
- SGID
- Sticky Bit
- Permission troubleshooting
- Principle of Least Privilege

---

# 1. 🔐 What Are Linux File Permissions?

Linux is a multi-user operating system.

Multiple users can access the same system, so Linux needs a mechanism to control:

- Who can read a file
- Who can modify a file
- Who can execute a file
- Who can access a directory
- Who owns a file
- Which group has access to a file

Linux uses a permission system based on three permission classes:

    User
    Group
    Others

And three basic permissions:

    Read
    Write
    Execute

---

# 2. 👤 Permission Classes

Every file and directory has permissions for three categories of users.

## User (u)

The User is the owner of the file.

Example:

    rishika owns notes.txt

The permissions assigned to the owner are called User permissions.

---

## Group (g)

The Group represents users who belong to the file's associated group.

Example:

    developers

If a file belongs to the `developers` group, members of that group may receive specific permissions.

---

## Others (o)

Others means every user who is:

- Not the file owner
- Not a member of the associated group

---

## Permission Model

    ┌──────────────┐
    │     File     │
    └──────┬───────┘
           │
           ▼
    ┌─────────────────────────────┐
    │       Permission Classes    │
    └─────────────┬───────────────┘
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
     User       Group      Others

---

# 3. 📖 Basic Permissions

Linux has three basic permissions.

## Read (r)

Numeric value:

    4

For a file, Read permission allows a user to:

- View file contents
- Read the file

Example:

    cat file.txt

---

## Write (w)

Numeric value:

    2

For a file, Write permission allows a user to:

- Modify file contents
- Edit the file

Example:

    nano file.txt

---

## Execute (x)

Numeric value:

    1

For a file, Execute permission allows a user to:

- Run an executable file
- Execute a script

Example:

    ./script.sh

---

# 4. 📁 Directory Permissions

Permissions behave slightly differently for directories.

## Read Permission on Directory

Read permission allows a user to list directory contents.

Example:

    ls directory/

---

## Write Permission on Directory

Write permission allows a user to:

- Create files
- Delete files
- Rename files

Important:

The ability to delete a file is mainly controlled by permissions on the parent directory, not simply by the file's own write permission.

---

## Execute Permission on Directory

Execute permission allows a user to:

- Enter the directory
- Traverse the directory
- Access files inside the directory when other permissions allow

Example:

    cd directory/

---

## Directory Permission Summary

    ┌──────────┬──────────────────────────────┐
    │ Permission│ Directory Meaning           │
    ├──────────┼──────────────────────────────┤
    │ r        │ List contents                │
    │ w        │ Create/Delete/Rename entries │
    │ x        │ Enter/Traverse directory     │
    └──────────┴──────────────────────────────┘

---

# 5. 🔍 Understanding ls -l

The command:

    ls -l

shows detailed information about files.

Example:

    -rwxr-xr-- 1 rishika developers 1200 Jul 30 script.sh

Breakdown:

    -rwxr-xr--
    │
    ├── File Type
    │
    ├── User Permissions
    │
    ├── Group Permissions
    │
    └── Others Permissions

---

## File Type

The first character represents the file type.

    -    Regular File
    d    Directory
    l    Symbolic Link
    c    Character Device
    b    Block Device
    p    Named Pipe
    s    Socket

Example:

    -rw-r--r--

The first `-` means this is a regular file.

Example:

    drwxr-xr-x

The first `d` means this is a directory.

---

# 6. 🔢 Permission Structure

Consider:

    -rwxr-xr--

Ignore the first character for a moment.

The remaining nine characters are divided into three groups.

    rwx    r-x    r--
    │      │      │
    User   Group  Others

So:

    User   → rwx
    Group  → r-x
    Others → r--

---

# 7. 🧮 Numeric Permission System

Each permission has a numeric value.

    Read      = 4
    Write     = 2
    Execute   = 1

Add the values to calculate permissions.

---

## Permission Examples

    rwx = 4 + 2 + 1 = 7

    rw- = 4 + 2 + 0 = 6

    r-x = 4 + 0 + 1 = 5

    r-- = 4 + 0 + 0 = 4

    -wx = 0 + 2 + 1 = 3

    -w- = 0 + 2 + 0 = 2

    --x = 0 + 0 + 1 = 1

    --- = 0 + 0 + 0 = 0

---

# 8. 📊 Common Permission Values

    0 = ---
    1 = --x
    2 = -w-
    3 = -wx
    4 = r--
    5 = r-x
    6 = rw-
    7 = rwx

---

# 9. 📌 Common Permission Modes

## 777

    rwxrwxrwx

Meaning:

    User   → rwx
    Group  → rwx
    Others → rwx

Everyone has full permissions.

This is generally unsafe and should be avoided unless there is a specific reason.

---

## 755

    rwxr-xr-x

Meaning:

    User   → rwx
    Group  → r-x
    Others → r-x

Commonly used for:

- Executable scripts
- Programs
- Directories

---

## 750

    rwxr-x---

Meaning:

    User   → rwx
    Group  → r-x
    Others → ---

Useful when only the owner and group should access something.

---

## 700

    rwx------

Meaning:

    User   → rwx
    Group  → ---
    Others → ---

Useful for private directories.

---

## 644

    rw-r--r--

Meaning:

    User   → rw-
    Group  → r--
    Others → r--

Commonly used for normal files.

---

## 600

    rw-------

Meaning:

    User   → rw-
    Group  → ---
    Others → ---

Useful for private files.

---

## 400

    r--------

Meaning:

    User   → r--
    Group  → ---
    Others → ---

Owner can only read the file.

---

# 10. 🛠️ chmod Command

`chmod` means:

    Change Mode

It is used to modify file and directory permissions.

Syntax:

    chmod PERMISSION FILE

Example:

    chmod 755 script.sh

This gives:

    User   → rwx
    Group  → r-x
    Others → r-x

---

# 11. 🔢 Numeric chmod

Example:

    chmod 644 file.txt

Breakdown:

    6 = rw-
    4 = r--
    4 = r--

Therefore:

    User   → rw-
    Group  → r--
    Others → r--

---

## More Examples

    chmod 600 secret.txt

    chmod 700 private/

    chmod 755 script.sh

    chmod 644 notes.txt

---

# 12. ✏️ Symbolic chmod

Permissions can also be changed using symbolic notation.

Permission classes:

    u = User
    g = Group
    o = Others
    a = All

Operators:

    + = Add permission
    - = Remove permission
    = = Set exact permission

---

## Examples

Add execute permission to User:

    chmod u+x script.sh

Remove write permission from User:

    chmod u-w file.txt

Add write permission to Group:

    chmod g+w file.txt

Remove read permission from Others:

    chmod o-r file.txt

Give execute permission to everyone:

    chmod a+x script.sh

Set exact permissions:

    chmod u=rwx,g=rx,o=r file.txt

---

# 13. 👑 chown Command

`chown` means:

    Change Owner

It changes the ownership of a file or directory.

Syntax:

    chown USER FILE

Example:

    sudo chown rishika file.txt

Change owner and group:

    sudo chown rishika:developers file.txt

Change ownership recursively:

    sudo chown -R rishika:developers project/

The `-R` option applies the change recursively to all files and directories inside.

---

# 14. 👥 chgrp Command

`chgrp` means:

    Change Group

It changes the group ownership of a file or directory.

Syntax:

    chgrp GROUP FILE

Example:

    sudo chgrp developers project.txt

Verify:

    ls -l project.txt

---

# 15. 🔄 chmod vs chown vs chgrp

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

    Changes permissions.

    chown rishika script.sh

    Changes owner.

    chgrp developers script.sh

    Changes group.

---

# 16. 🎭 File Ownership

Every file has:

    Owner
    Group

Example:

    -rw-r--r-- 1 rishika developers file.txt

Here:

    Owner = rishika
    Group = developers

The permissions are evaluated based on:

1. Is the user the owner?
2. If not, is the user a member of the file's group?
3. If neither, the Others permissions apply.

---

# 17. 🧠 Permission Evaluation

Suppose:

    -rw-r-----x

For a user accessing this file:

    Step 1
    Is the user the owner?

    YES
    → Use User permissions.

    NO
    ↓

    Step 2
    Is the user a member of the file's group?

    YES
    → Use Group permissions.

    NO
    ↓

    Step 3
    Use Others permissions.

Important:

Linux does not combine permissions from User, Group, and Others.

It selects the applicable category.

---

# 18. 🛡️ Principle of Least Privilege

The Principle of Least Privilege means:

> Give users and processes only the permissions they actually need.

Avoid unnecessary permissions.

Bad example:

    chmod 777 secret.txt

Better:

    chmod 600 secret.txt

For a public readable file:

    chmod 644 file.txt

For an executable script:

    chmod 755 script.sh

The goal is to minimize security risks.

---

# 19. ⚙️ umask

`umask` controls default permissions for newly created files and directories.

Check the current umask:

    umask

Example:

    0022

Typical base permissions:

    Files       → 666
    Directories → 777

The umask removes permission bits from these base permissions.

---

## Example

Suppose:

    umask = 022

A new file may be created with:

    644

A new directory may be created with:

    755

This happens because the umask prevents certain write permissions from being granted by default.

---

# 20. 🔒 SUID

SUID means:

    Set User ID

Numeric value:

    4000

When SUID is set on an executable file, the program runs with the effective privileges of the file owner.

Example:

    chmod 4755 program

Permission may appear as:

    -rwsr-xr-x

The `s` appears in the User execute position.

SUID can be useful but can also create security risks if applied incorrectly.

Only trusted executables should have SUID.

---

# 21. 👥 SGID

SGID means:

    Set Group ID

Numeric value:

    2000

For an executable:

The program runs with the effective group privileges of the file's group.

For a directory:

New files and directories created inside may inherit the directory's group ownership.

Example:

    chmod 2755 shared/

Permission may appear as:

    drwxr-sr-x

The `s` appears in the Group execute position.

SGID is commonly useful for shared project directories.

---

# 22. 📌 Sticky Bit

Sticky Bit is commonly used on shared directories.

Numeric value:

    1000

Example:

    chmod 1777 shared/

Permission:

    drwxrwxrwt

The `t` appears at the end.

A common example is:

    /tmp

The Sticky Bit prevents users from deleting or renaming files belonging to other users in a shared directory, subject to the usual ownership and privilege rules.

---

# 23. 🆚 SUID vs SGID vs Sticky Bit

    SUID
    4000
    ↓
    Run executable with file owner's effective privileges.

    SGID
    2000
    ↓
    Run executable with group privileges.
    On directories, encourage group inheritance.

    Sticky Bit
    1000
    ↓
    Protect files in shared directories from deletion
    or renaming by other users.

---

# 24. 🚨 Permission Denied

When you see:

    Permission denied

Do not immediately use:

    chmod 777

Instead, investigate.

Check current user:

    whoami

Check user identity:

    id

Check groups:

    groups

Check file permissions:

    ls -l file.txt

Check directory permissions:

    ls -ld directory/

Check the complete path:

    namei -l /path/to/file

Then determine:

- Who owns the file?
- Which group owns it?
- Which permission category applies?
- Does the user have the required permission?
- Do parent directories allow traversal?

Fix only the required permission.

---

# 25. 🔍 Permission Troubleshooting Example

Suppose:

    cat secret.txt

Returns:

    Permission denied

Step 1:

    whoami

Step 2:

    ls -l secret.txt

Suppose output is:

    -rw------- 1 alice alice secret.txt

If the current user is:

    bob

Then:

    bob ≠ alice

Bob is not the owner.

If Bob is not in the applicable group, the Others permissions apply.

Others have:

    ---

Therefore:

    Permission denied

Possible solutions:

- Ask the owner for access.
- Change ownership if appropriate.
- Change group ownership.
- Modify permissions carefully.
- Use `sudo` only when administrative access is actually required.

---

# 26. 📁 File vs Directory Permissions

For files:

    r → Read contents
    w → Modify contents
    x → Execute

For directories:

    r → List contents
    w → Create/Delete/Rename entries
    x → Enter/Traverse

Important:

    File permissions
    ≠
    Directory permissions

A user may have permission to read a file but still be unable to access it if they cannot traverse the parent directory.

---

# 27. 🔐 Why chmod 777 Is Dangerous

`777` means:

    User   → rwx
    Group  → rwx
    Others → rwx

Every user can:

- Read
- Modify
- Execute

Depending on the context, this can allow unauthorized modification or execution.

Instead of:

    chmod 777 file.txt

Use the minimum required permissions.

Examples:

    chmod 644 file.txt

    chmod 600 secret.txt

    chmod 755 script.sh

    chmod 700 private/

Always follow:

    Principle of Least Privilege

---

# 28. 🧩 Real-World Permission Example

Imagine a web application.

Project:

    /var/www/myapp/

Possible structure:

    myapp/
    ├── public/
    ├── config/
    ├── logs/
    └── scripts/

Possible security approach:

    public/
    → Readable by web server

    config/
    → Restricted access

    logs/
    → Writable by application service

    scripts/
    → Executable only by authorized users

The exact permissions depend on the application and deployment architecture.

The goal is to give each service only the permissions it needs.

---

# 29. 🧪 Important Commands

Check permissions:

    ls -l

Check directory permissions:

    ls -ld directory/

Change permissions:

    chmod

Change owner:

    chown

Change group:

    chgrp

Check current user:

    whoami

Check UID and groups:

    id

Check group membership:

    groups

Check umask:

    umask

Inspect path permissions:

    namei -l /path/to/file

---

# 30. 📋 Quick Command Reference

    ls -l file.txt

    chmod 644 file.txt

    chmod 755 script.sh

    chmod 600 secret.txt

    chmod 700 private/

    chmod u+x script.sh

    chmod g+w file.txt

    chmod o-r file.txt

    sudo chown user file.txt

    sudo chown user:group file.txt

    sudo chgrp group file.txt

    umask

    whoami

    id

    groups

---

# 31. 🧠 Key Takeaways

1. Linux uses permissions to control access to files and directories.

2. Permissions are divided into:
   - User
   - Group
   - Others

3. Basic permissions are:
   - Read
   - Write
   - Execute

4. Read = 4.

5. Write = 2.

6. Execute = 1.

7. `chmod` changes permissions.

8. `chown` changes ownership.

9. `chgrp` changes group ownership.

10. `umask` controls default permissions for newly created files and directories.

11. SUID has a value of `4000`.

12. SGID has a value of `2000`.

13. Sticky Bit has a value of `1000`.

14. Directory permissions behave differently from file permissions.

15. `chmod 777` should generally be avoided.

16. Use the Principle of Least Privilege.

17. When troubleshooting `Permission denied`, inspect ownership, permissions, groups, and parent directory traversal.

---

# 🧠 Interview Quick Revision

Question:

What are the three Linux permission classes?

Answer:

    User
    Group
    Others

Question:

What are the three basic permissions?

Answer:

    Read
    Write
    Execute

Question:

What does `chmod` do?

Answer:

It changes file or directory permissions.

Question:

What does `chown` do?

Answer:

It changes the owner of a file or directory.

Question:

What does `chgrp` do?

Answer:

It changes the group ownership of a file or directory.

Question:

What does `755` mean?

Answer:

    User   → rwx
    Group  → r-x
    Others → r-x

Question:

What does `644` mean?

Answer:

    User   → rw-
    Group  → r--
    Others → r--

Question:

What does `600` mean?

Answer:

    User   → rw-
    Group  → ---
    Others → ---

Question:

What is SUID?

Answer:

SUID allows an executable to run with the effective privileges of its file owner.

Question:

What is SGID?

Answer:

SGID allows an executable to run with group privileges and can cause group inheritance in directories.

Question:

What is Sticky Bit?

Answer:

Sticky Bit protects files in shared directories from being deleted or renamed by other users.

Question:

What is the Principle of Least Privilege?

Answer:

Giving users and processes only the minimum permissions required to perform their tasks.

---

# 🏁 Chapter 08 Completion Checklist

- [ ] Understand User, Group, and Others
- [ ] Understand Read, Write, and Execute
- [ ] Understand file permissions
- [ ] Understand directory permissions
- [ ] Read `ls -l` output
- [ ] Understand numeric permissions
- [ ] Understand symbolic permissions
- [ ] Practice `chmod`
- [ ] Practice `chown`
- [ ] Practice `chgrp`
- [ ] Understand `umask`
- [ ] Understand SUID
- [ ] Understand SGID
- [ ] Understand Sticky Bit
- [ ] Complete Permission Denied troubleshooting
- [ ] Complete Hands-on Lab
- [ ] Complete Interview Preparation
- [ ] Complete Diagram

---

# 🐧 Linux Quest — Level 02

## Chapter 08: Linux File Permissions & Ownership

    Theory              → 🟢 Complete
    Diagram             → 🟢 Complete
    Interview Prep      → 🟢 Complete
    Hands-on Lab        → 🟢 Complete
    README              → ⬜ Pending
    Git Commits         → ⬜ Pending

Status:

    🟡 Chapter Content Complete

---

> Understand permissions.
> Control access.
> Follow least privilege.
> Secure Linux.