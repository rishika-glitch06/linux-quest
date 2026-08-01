# 🧪 Linux File Permissions & Ownership — Hands-on Lab

> Practice Linux file permissions, ownership, chmod, chown, chgrp, umask, SUID, SGID, Sticky Bit, and permission troubleshooting.

---

# 🎯 Lab Objectives

By completing this lab, you will learn how to:

- Understand Linux file permissions
- Read permission strings
- Understand User / Group / Others
- Use numeric permissions
- Use symbolic permissions
- Change permissions using `chmod`
- Change ownership using `chown`
- Change group ownership using `chgrp`
- Understand `umask`
- Practice SUID
- Practice SGID
- Practice Sticky Bit
- Troubleshoot Permission Denied errors
- Understand the Principle of Least Privilege

---

# 🧰 Requirements

You need:

- Linux system
- Ubuntu / Debian / Kali / Fedora / WSL
- Terminal
- Basic Linux command knowledge

Check your current user:

    whoami

Check your user and group information:

    id

Check the current directory:

    pwd

---

# 📁 Lab Setup

Create a dedicated lab directory:

    mkdir -p ~/linux-quest/level-02/lesson-10-permissions-lab

Move into it:

    cd ~/linux-quest/level-02/lesson-10-permissions-lab

Verify:

    pwd

Expected output will look similar to:

    /home/username/linux-quest/level-02/lesson-10-permissions-lab

---

# 1. 📄 Create Test Files

Create a file:

    touch file1.txt

Create another file:

    touch secret.txt

Create a script:

    touch script.sh

Create a directory:

    mkdir private

Create another directory:

    mkdir shared

Check everything:

    ls -la

Expected structure:

    .
    ├── file1.txt
    ├── secret.txt
    ├── script.sh
    ├── private/
    └── shared/

---

# 2. 🔍 Inspect Default Permissions

Run:

    ls -l

Observe the permissions of:

    file1.txt
    secret.txt
    script.sh
    private/
    shared/

Example:

    -rw-r--r--  file1.txt
    drwxr-xr-x  private/

The exact permissions may vary depending on your system's `umask`.

---

# 3. 🧠 Understand Permission Structure

Take this example:

    -rwxr-xr--

Break it down:

    - | rwx | r-x | r--
      |     |     |
      |     |     └── Others
      |     └──────── Group
      └────────────── Owner

Identify:

    File Type  = -
    Owner      = rwx
    Group      = r-x
    Others     = r--

Convert to numbers:

    rwx = 7
    r-x = 5
    r-- = 4

Final:

    754

---

# 4. 🔢 Set Numeric Permissions

Set `file1.txt` to permission `644`:

    chmod 644 file1.txt

Check:

    ls -l file1.txt

Expected:

    -rw-r--r--

Set `secret.txt` to `600`:

    chmod 600 secret.txt

Check:

    ls -l secret.txt

Expected:

    -rw-------

Set `private` to `700`:

    chmod 700 private

Check:

    ls -ld private

Expected:

    drwx------

---

# 5. 🛠️ Practice Symbolic Permissions

Add execute permission to the script:

    chmod u+x script.sh

Check:

    ls -l script.sh

Remove execute permission:

    chmod u-x script.sh

Add group write permission:

    chmod g+w file1.txt

Remove group write permission:

    chmod g-w file1.txt

Add read permission for others:

    chmod o+r file1.txt

Remove read permission from others:

    chmod o-r file1.txt

Check the final result:

    ls -l file1.txt

---

# 6. 👥 Practice User / Group / Others

Set:

    Owner → Read + Write + Execute
    Group → Read + Execute
    Others → Read

Use:

    chmod 754 script.sh

Verify:

    ls -l script.sh

Expected:

    -rwxr-xr--

Breakdown:

    Owner  = rwx = 7
    Group  = r-x = 5
    Others = r-- = 4

---

# 7. 📁 File vs Directory Permissions

Create a file inside `private`:

    touch private/secret.txt

Set directory permissions:

    chmod 700 private

Check:

    ls -ld private

Try accessing it:

    cd private

If access is allowed, return:

    cd ..

Now remove execute permission:

    chmod u-x private

Try:

    cd private

Observe the result.

You may receive:

    Permission denied

Restore permission:

    chmod 700 private

---

# 8. 📂 Directory Write Permission

Create a directory:

    mkdir testdir

Set permissions:

    chmod 500 testdir

Try creating a file:

    touch testdir/test.txt

Observe the result.

Now restore write permission:

    chmod 700 testdir

Try again:

    touch testdir/test.txt

Check:

    ls -la testdir

---

# 9. 🔐 Secure a Secret File

Create a secret file:

    echo "This is confidential information" > secret.txt

Set secure permissions:

    chmod 600 secret.txt

Check:

    ls -l secret.txt

Expected:

    -rw-------

Meaning:

    Owner  → Read + Write
    Group  → No Access
    Others → No Access

View the content:

    cat secret.txt

---

# 10. 🧑‍💻 Create an Executable Script

Create script content:

    echo '#!/bin/bash' > script.sh

    echo 'echo "Linux Permissions Lab"' >> script.sh

View the script:

    cat script.sh

Try executing:

    ./script.sh

You may receive:

    Permission denied

Add execute permission:

    chmod u+x script.sh

Run again:

    ./script.sh

Expected:

    Linux Permissions Lab

Check permissions:

    ls -l script.sh

---

# 11. 👑 Change File Ownership

Check current ownership:

    ls -l file1.txt

Check current user:

    whoami

Change owner to the current user:

    sudo chown $(whoami) file1.txt

Check:

    ls -l file1.txt

The owner should now be your current username.

Note:

Changing ownership usually requires administrative privileges.

---

# 12. 👥 Change Group Ownership

Check available groups:

    groups

Create a test group if needed:

    sudo groupadd linuxlab

Change group ownership:

    sudo chgrp linuxlab file1.txt

Check:

    ls -l file1.txt

Expected format:

    -rw-r--r-- username linuxlab file1.txt

---

# 13. 🔄 Change Owner and Group Together

Use:

    sudo chown $(whoami):linuxlab file1.txt

Check:

    ls -l file1.txt

Expected:

    Owner → Your username
    Group → linuxlab

---

# 14. 📂 Recursive Ownership

Create a project directory:

    mkdir -p project/data/logs

Create files:

    touch project/app.py
    touch project/data/data.txt
    touch project/data/logs/app.log

Check:

    ls -lR project

Change ownership recursively:

    sudo chown -R $(whoami):linuxlab project

Verify:

    ls -lR project

The owner and group should be applied recursively.

---

# 15. 🎭 Check umask

Check current umask:

    umask

Example:

    0022

Create a new file:

    touch umask-test.txt

Create a new directory:

    mkdir umask-dir

Check:

    ls -ld umask-dir
    ls -l umask-test.txt

Observe the default permissions.

---

# 16. 🧮 Understand umask Calculation

Typical base permissions:

    Files       → 666
    Directories → 777

For:

    umask = 022

New file:

    666
     │
     ▼
    022
     │
     ▼
    644

New directory:

    777
     │
     ▼
    022
     │
     ▼
    755

Verify:

    umask

Then create:

    touch test-umask.txt
    mkdir test-umask-dir

Check:

    ls -l test-umask.txt
    ls -ld test-umask-dir

---

# 17. 🔴 SUID Practice

Create a test file:

    touch suid-test

Set SUID:

    chmod u+s suid-test

Check:

    ls -l suid-test

You may see:

    -rwSr--r--

The `S` indicates SUID is set without execute permission.

Now add execute permission:

    chmod u+x suid-test

Check:

    ls -l suid-test

You may see:

    -rwsr--r--

The `s` represents SUID.

Remove SUID:

    chmod u-s suid-test

Check:

    ls -l suid-test

---

# 18. 🟡 SGID Practice

Create a shared directory:

    mkdir sgid-dir

Set permissions:

    chmod 2775 sgid-dir

Check:

    ls -ld sgid-dir

You should see an `s` in the group execute position.

Example:

    drwxrwsr-x

Create a file inside:

    touch sgid-dir/test.txt

Check:

    ls -l sgid-dir/test.txt

Check the group ownership:

    ls -l sgid-dir

Remove SGID:

    chmod g-s sgid-dir

---

# 19. 🟢 Sticky Bit Practice

Create a shared directory:

    mkdir sticky-dir

Set permissions:

    chmod 1777 sticky-dir

Check:

    ls -ld sticky-dir

Expected:

    drwxrwxrwt

The final `t` represents Sticky Bit.

Create test files:

    touch sticky-dir/file1.txt
    touch sticky-dir/file2.txt

Check:

    ls -la sticky-dir

Remove Sticky Bit:

    chmod -t sticky-dir

Restore it:

    chmod +t sticky-dir

---

# 20. 🧪 Permission Denied Challenge

Create:

    mkdir restricted

Create a file:

    touch restricted/file.txt

Set restrictive permissions:

    chmod 000 restricted

Try:

    ls restricted

Observe:

    Permission denied

Restore permissions:

    chmod 700 restricted

Try again:

    ls restricted

You should now be able to access the directory.

---

# 21. 🔎 Permission Troubleshooting

Use:

    ls -l restricted

Check directory permissions:

    ls -ld restricted

Check your identity:

    whoami

Check your groups:

    id

Check detailed file information:

    stat restricted

Check path permissions:

    namei -l restricted/file.txt

Ask yourself:

    1. Who is the owner?
    2. What is the group?
    3. Is my user the owner?
    4. Am I part of the group?
    5. What permissions does the owner have?
    6. What permissions does the group have?
    7. What permissions do others have?
    8. Does the parent directory have execute permission?

---

# 22. 🧠 Permission Calculation Challenge

Convert the following permissions to numeric values:

### Challenge 1

    rwxr-xr-x

Answer:

    755

### Challenge 2

    rw-r--r--

Answer:

    644

### Challenge 3

    rw-------

Answer:

    600

### Challenge 4

    rwxrwxr-x

Answer:

    775

### Challenge 5

    r-xr-----

Answer:

    540

---

# 23. 🧩 chmod Challenge

Set the following permissions:

### Challenge 1

Owner → Full Access
Group → Read
Others → No Access

Use:

    chmod 740 file1.txt

---

### Challenge 2

Owner → Read + Write
Group → Read
Others → Read

Use:

    chmod 644 file1.txt

---

### Challenge 3

Owner → Full Access
Group → Full Access
Others → Read + Execute

Use:

    chmod 775 project

---

### Challenge 4

Owner → Full Access
Group → No Access
Others → No Access

Use:

    chmod 700 private

---

# 24. 🧪 Mini Project — Secure Project Directory

Create:

    mkdir -p secure-project/data
    mkdir -p secure-project/scripts
    mkdir -p secure-project/logs

Create files:

    touch secure-project/data/database.txt
    touch secure-project/scripts/run.sh
    touch secure-project/logs/app.log

Set permissions:

    chmod 700 secure-project

    chmod 700 secure-project/data

    chmod 700 secure-project/scripts

    chmod 755 secure-project/logs

Secure database file:

    chmod 600 secure-project/data/database.txt

Make script executable:

    chmod 700 secure-project/scripts/run.sh

Set log permissions:

    chmod 644 secure-project/logs/app.log

Check everything:

    ls -lR secure-project

Expected security model:

    secure-project/
    │
    ├── data/
    │     └── database.txt
    │          └── 600
    │
    ├── scripts/
    │     └── run.sh
    │          └── 700
    │
    └── logs/
          └── app.log
               └── 644

---

# 25. 🎯 Final Permission Challenge

Create:

    mkdir final-challenge

Inside it create:

    touch final-challenge/public.txt
    touch final-challenge/private.txt
    touch final-challenge/run.sh

Set permissions according to the requirements:

public.txt:

    Owner → Read + Write
    Group → Read
    Others → Read

Expected:

    644

private.txt:

    Owner → Read + Write
    Group → No Access
    Others → No Access

Expected:

    600

run.sh:

    Owner → Full Access
    Group → Read + Execute
    Others → Read + Execute

Expected:

    755

Set the permissions:

    chmod 644 final-challenge/public.txt
    chmod 600 final-challenge/private.txt
    chmod 755 final-challenge/run.sh

Verify:

    ls -l final-challenge

---

# 26. 🏆 Final Practical Task

Complete the following without looking at previous commands.

Create a directory:

    permissions-final

Inside it create:

    confidential.txt
    public.txt
    script.sh
    shared/

Requirements:

    confidential.txt
    → Permission 600

    public.txt
    → Permission 644

    script.sh
    → Permission 755

    shared/
    → Permission 1777

    script.sh
    → Must be executable

    confidential.txt
    → Must not be accessible by Group or Others

    shared/
    → Must have Sticky Bit

Commands:

    mkdir permissions-final

    touch permissions-final/confidential.txt
    touch permissions-final/public.txt
    touch permissions-final/script.sh

    mkdir permissions-final/shared

    chmod 600 permissions-final/confidential.txt
    chmod 644 permissions-final/public.txt
    chmod 755 permissions-final/script.sh
    chmod 1777 permissions-final/shared

Verify:

    ls -l permissions-final

    ls -ld permissions-final/shared

Expected:

    confidential.txt → -rw-------
    public.txt       → -rw-r--r--
    script.sh        → -rwxr-xr-x
    shared/          → drwxrwxrwt

---

# 27. 🧹 Lab Cleanup

After completing the lab, remove the test environment:

    cd ~

Remove the lab directory:

    rm -rf ~/linux-quest/level-02/lesson-10-permissions-lab

⚠️ Always verify the path before using `rm -rf`.

---

# 🧠 Lab Summary

During this lab, you practiced:

    ls -l
        ↓
    View Permissions

    chmod
        ↓
    Change Permissions

    chown
        ↓
    Change Owner

    chgrp
        ↓
    Change Group

    umask
        ↓
    Default Permissions

    SUID
        ↓
    Run with Owner Privileges

    SGID
        ↓
    Group Inheritance

    Sticky Bit
        ↓
    Protect Shared Directory Files

    stat
        ↓
    Detailed File Information

    namei -l
        ↓
    Inspect Path Permissions

---

# 📊 Command Summary

| Command | Purpose |
|---|---|
| `ls -l` | View file permissions and ownership |
| `ls -ld` | View directory permissions |
| `chmod` | Change permissions |
| `chown` | Change owner |
| `chgrp` | Change group |
| `umask` | View or set default permissions |
| `stat` | View detailed file information |
| `whoami` | Show current user |
| `id` | Show user and group information |
| `namei -l` | Inspect permissions along a path |
| `sudo` | Execute commands with elevated privileges |

---

# ✅ Lab Completion Checklist

- [ ] Created lab environment
- [ ] Inspected file permissions
- [ ] Understood `rwx`
- [ ] Converted permissions to numeric values
- [ ] Used `chmod` numeric mode
- [ ] Used `chmod` symbolic mode
- [ ] Practiced file permissions
- [ ] Practiced directory permissions
- [ ] Changed file ownership
- [ ] Changed group ownership
- [ ] Used recursive ownership
- [ ] Checked `umask`
- [ ] Practiced SUID
- [ ] Practiced SGID
- [ ] Practiced Sticky Bit
- [ ] Troubleshot Permission Denied
- [ ] Completed Permission Calculation Challenge
- [ ] Completed chmod Challenge
- [ ] Completed Mini Project
- [ ] Completed Final Permission Challenge

---

# 🎉 Lab Status

    🟢 COMPLETED

You now understand the fundamentals of Linux File Permissions & Ownership.

> 🐧 Linux Quest — Level 02, Lesson 10

> *Understand. Control. Secure.*