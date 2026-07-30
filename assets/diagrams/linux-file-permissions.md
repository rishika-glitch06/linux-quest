# 🐧 Linux Quest — Level 02
# Chapter 08: Linux File Permissions & Ownership — Diagram

---

## 📌 Linux Permission Structure

    ┌──────────────────────────────────────────────────────────────┐
    │                    Linux File Permissions                    │
    └──────────────────────────────────────────────────────────────┘
                              │
                              ▼
    ┌──────────────────────────────────────────────────────────────┐
    │                     Permission Classes                       │
    └──────────────────────────────────────────────────────────────┘
              │                     │                     │
              ▼                     ▼                     ▼
        ┌──────────┐          ┌──────────┐          ┌──────────┐
        │   USER   │          │  GROUP   │          │  OTHERS  │
        │  Owner   │          │ Members  │          │ Everyone │
        └──────────┘          └──────────┘          └──────────┘
              │                     │                     │
              └─────────────────────┼─────────────────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    Permissions      │
                         └─────────────────────┘
                                    │
                         ┌──────────┼──────────┐
                         ▼          ▼          ▼
                     ┌──────┐  ┌──────┐  ┌──────┐
                     │  r   │  │  w   │  │  x   │
                     │ Read │  │Write │  │Exec  │
                     └──────┘  └──────┘  └──────┘
                        4          2          1


---

## 📌 Understanding ls -l Output

Example:

    -rwxr-xr--  1  rishika  developers  1200  Jul 30  script.sh

    ┌──┬─────────┬───┬─────────┬────────────┬──────┬────────────┐
    │  │         │   │         │            │      │            │
    │  │         │   │         │            │      │            └── File Name
    │  │         │   │         │            │      └── Modification Date
    │  │         │   │         │            └── File Size
    │  │         │   │         └── Group Owner
    │  │         │   └── File Owner
    │  │         └── Hard Link Count
    │  └── Permission Bits
    └── File Type

Permission Section:

    -rwxr-xr--

     │   │   │
     │   │   └──────── Others
     │   │
     │   └──────────── Group
     │
     └──────────────── User / Owner

    -  → Regular File
    d  → Directory
    l  → Symbolic Link


---

## 📌 Permission Breakdown

Example:

    -rwxr-xr--

            USER       GROUP      OTHERS
             │           │           │
             ▼           ▼           ▼
           ┌─────┐     ┌─────┐     ┌─────┐
           │ rwx │     │ r-x │     │ r-- │
           └─────┘     └─────┘     └─────┘
              │           │           │
              ▼           ▼           ▼
             7           5           4

    Numeric Permission = 754


---

## 📌 Permission Values

    ┌─────────────┬───────────┐
    │ Permission  │ Value     │
    ├─────────────┼───────────┤
    │ ---         │ 0         │
    │ --x         │ 1         │
    │ -w-         │ 2         │
    │ -wx         │ 3         │
    │ r--         │ 4         │
    │ r-x         │ 5         │
    │ rw-         │ 6         │
    │ rwx         │ 7         │
    └─────────────┴───────────┘

    Read      = 4
    Write     = 2
    Execute   = 1


---

## 📌 Numeric Permission Calculation

    rwx = 4 + 2 + 1 = 7

    rw- = 4 + 2 + 0 = 6

    r-x = 4 + 0 + 1 = 5

    r-- = 4 + 0 + 0 = 4

    -wx = 0 + 2 + 1 = 3

    -w- = 0 + 2 + 0 = 2

    --x = 0 + 0 + 1 = 1

    --- = 0 + 0 + 0 = 0


---

## 📌 Common Linux Permissions

    ┌──────────┬───────────────┬──────────────────────────────┐
    │ Numeric  │ Symbolic      │ Meaning                      │
    ├──────────┼───────────────┼──────────────────────────────┤
    │ 777      │ rwxrwxrwx     │ Everyone full access         │
    │ 755      │ rwxr-xr-x     │ Owner full, others read/run  │
    │ 750      │ rwxr-x---     │ Owner full, group read/run   │
    │ 700      │ rwx------     │ Owner full access only       │
    │ 644      │ rw-r--r--     │ Owner write, everyone read   │
    │ 600      │ rw-------     │ Owner read/write only        │
    │ 400      │ r--------     │ Owner read-only              │
    └──────────┴───────────────┴──────────────────────────────┘


---

## 📌 chmod — Change File Permissions

    chmod
      │
      ├─────────────── Numeric Mode
      │
      │       chmod 755 script.sh
      │
      │       User    → rwx → 7
      │       Group   → r-x → 5
      │       Others  → r-x → 5
      │
      └─────────────── Symbolic Mode

              chmod u+x script.sh
                    │
                    └── Add Execute Permission to User

    Symbolic Classes:

    u → User
    g → Group
    o → Others
    a → All

    Operators:

    + → Add
    - → Remove
    = → Set Exact Permission


---

## 📌 chmod Symbolic Permission Flow

    ┌──────────────┐
    │ chmod u+x    │
    └──────┬───────┘
           │
           ▼
    ┌──────────────┐
    │     User     │
    └──────┬───────┘
           │
           ▼
    ┌──────────────┐
    │ Add Execute  │
    │   Permission │
    └──────────────┘


    Example:

    chmod g+w file.txt

    g → Group
    + → Add
    w → Write

    Result:

    Group gets Write Permission


---

## 📌 chown — Change Ownership

    ┌──────────────────────┐
    │       chown          │
    │    Change Owner      │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │       File           │
    │      file.txt        │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │       New Owner      │
    │       rishika        │
    └──────────────────────┘

    Command:

    sudo chown rishika file.txt

    Change Owner + Group:

    sudo chown rishika:developers file.txt


---

## 📌 chgrp — Change Group

    ┌──────────────────────┐
    │       chgrp          │
    │    Change Group      │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │       File           │
    │      file.txt        │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │      New Group       │
    │     developers       │
    └──────────────────────┘

    Command:

    sudo chgrp developers file.txt


---

## 📌 chmod vs chown vs chgrp

    ┌───────────────┬────────────────────────────────┐
    │ Command       │ Purpose                        │
    ├───────────────┼────────────────────────────────┤
    │ chmod         │ Change file permissions        │
    │ chown         │ Change file owner              │
    │ chgrp         │ Change group ownership         │
    └───────────────┴────────────────────────────────┘


---

## 📌 Directory Permissions

    Directory
       │
       ├──────── r → List contents
       │
       ├──────── w → Create/Delete/Rename entries
       │
       └──────── x → Enter/Traverse directory


    Important:

    r = Can see directory listing

    w = Can modify directory entries

    x = Can access/traverse directory


    Example:

    drwxr-xr-x

     │   │   │
     │   │   └── Others
     │   └────── Group
     └────────── User

    User    → rwx
    Group   → r-x
    Others  → r-x


---

## 📌 umask

    New File / Directory
             │
             ▼
        Default Mode
             │
             ▼
           umask
             │
             ▼
      Remove Permission Bits
             │
             ▼
      Final Permissions


    Typical Base Permissions:

    Files       → 666
    Directories → 777

    umask controls which permission bits are removed.


---

## 📌 SUID

    SUID
      │
      ▼
    Executable File
      │
      ▼
    Runs with File Owner's Privileges


    Numeric Value:

    4000


    Example:

    chmod 4755 program


    Permission Pattern:

    -rwsr-xr-x
      │
      └── s = SUID


    ⚠️ Security Note:

    SUID programs must be carefully managed because they run
    with the privileges of the file owner.


---

## 📌 SGID

    SGID
      │
      ├──────── Executable File
      │              │
      │              ▼
      │       Runs with Group Privileges
      │
      └──────── Directory
                     │
                     ▼
              New Files Inherit
              Directory Group


    Numeric Value:

    2000


    Example:

    chmod 2755 directory


    Permission Pattern:

    drwxr-sr-x
         │
         └── s = SGID


---

## 📌 Sticky Bit

    Sticky Bit
        │
        ▼
    Shared Directory
        │
        ▼
    Users Can Create Their Own Files
        │
        ▼
    Users Cannot Normally Delete
    Other Users' Files


    Numeric Value:

    1000


    Example:

    chmod 1777 shared


    Permission Pattern:

    drwxrwxrwt
           │
           └── t = Sticky Bit


    Common Example:

    /tmp


---

## 📌 SUID vs SGID vs Sticky Bit

    ┌──────────────┬──────────┬─────────────────────────────┐
    │ Feature      │ Value    │ Purpose                     │
    ├──────────────┼──────────┼─────────────────────────────┤
    │ SUID         │ 4000     │ Run as file owner           │
    │ SGID         │ 2000     │ Run as group / group inherit│
    │ Sticky Bit   │ 1000     │ Protect shared directory    │
    └──────────────┴──────────┴─────────────────────────────┘


---

## 📌 Permission Denied Troubleshooting Flow

    Permission Denied
          │
          ▼
    ┌─────────────────┐
    │ Check User      │
    │ whoami          │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────┐
    │ Check Groups    │
    │ id / groups     │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────┐
    │ Check File      │
    │ ls -l file      │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────┐
    │ Check Ownership │
    │ User / Group    │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────────┐
    │ Check Permissions   │
    │ r / w / x           │
    └──────────┬──────────┘
               │
               ▼
    ┌─────────────────────┐
    │ Check Parent Paths  │
    │ namei -l /path      │
    └──────────┬──────────┘
               │
               ▼
    ┌─────────────────────┐
    │ Fix Permissions or  │
    │ Ownership if Needed │
    └─────────────────────┘


---

## 📌 Principle of Least Privilege

    User / Process
          │
          ▼
    ┌──────────────────────┐
    │ Identify Required    │
    │ Access                │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │ Give Minimum         │
    │ Required Permissions │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │ Avoid Unnecessary    │
    │ Privileges           │
    └──────────────────────┘


    Avoid:

    chmod 777 file.txt

    Prefer:

    chmod 644 file.txt

    or:

    chmod 600 secret.txt


---

## 📌 Secure Project Permission Model

    permissions-project/
    │
    ├── public/
    │     └── readme.txt
    │           │
    │           └── 644
    │
    ├── private/
    │     └── secret.txt
    │           │
    │           └── 600
    │
    ├── scripts/
    │     └── backup.sh
    │           │
    │           └── 755
    │
    └── shared/
          │
          └── 1777
              │
              └── Sticky Bit


---

## 📌 Complete Linux Permission Hierarchy

                    Linux Permissions
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
        User             Group            Others
          │                │                │
          └────────────────┼────────────────┘
                           │
                           ▼
                   ┌───────────────┐
                   │  r  w  x      │
                   │  4  2  1      │
                   └───────┬───────┘
                           │
                           ▼
                   Numeric Permissions
                           │
              ┌────────────┼────────────┐
              ▼            ▼            ▼
             755          644          600
              │            │            │
              ▼            ▼            ▼
         Executable      Readable      Private
           Files          Files         Files


---

## 📌 Linux Permission Command Map

    ┌──────────────────────────────────────────────┐
    │              Linux Permission Tools          │
    └──────────────────────┬───────────────────────┘
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       chmod            chown            chgrp
          │                │                │
          ▼                ▼                ▼
    Permissions        Ownership          Group
          │
          ▼
       umask
          │
          ▼
    Default Permission
    Control


---

## 📌 Quick Revision Diagram

    r = Read      = 4
    w = Write     = 2
    x = Execute   = 1

    User   = Owner
    Group  = Group Members
    Others = Everyone Else

    chmod = Change Permissions
    chown = Change Owner
    chgrp = Change Group
    umask = Default Permission Mask

    SUID        = 4000
    SGID        = 2000
    Sticky Bit  = 1000

    755 = rwxr-xr-x
    644 = rw-r--r--
    600 = rw-------
    700 = rwx------
    777 = rwxrwxrwx

---

# 🏁 Chapter 08 Diagram Complete

Chapter: Linux File Permissions & Ownership

Theory         → ⬜
Interview Prep → 🟢 Complete
Hands-on Lab   → 🟢 Complete
Diagram        → 🟢 Complete
README         → ⬜
Git Commits    → ⬜

Status: 🟡 In Progress

---

# 🐧 Linux Quest

> Understand permissions.
> Control access.
> Follow least privilege.
> Secure Linux.