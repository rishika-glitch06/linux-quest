# 🐧 Linux Quest — Level 02
# 🧪 Lab 08: Linux File Links — Hard Links & Symbolic Links

> In this lab, you will learn and practice Inodes, Hard Links, Symbolic Links, Link Counts, Broken Symlinks, Relative Links, and Filesystem References.

---

# 🎯 Lab Objectives

By completing this lab, you will learn:

- What an inode is
- How to check inode numbers
- How to create hard links
- How to create symbolic links
- How hard links behave when the original filename is deleted
- How symbolic links behave when the target is deleted
- How to check link counts
- How to identify broken symbolic links
- How to compare hard links and symbolic links
- How to use `ls`, `ls -li`, `readlink`, `stat`, and `find`

---

# 🧰 Requirements

You need:

- Linux system
- Terminal
- Basic knowledge of Linux files and directories
- Level 02 Linux File System knowledge

You can perform this lab on:

- Ubuntu
- Debian
- Kali Linux
- Fedora
- Arch Linux
- WSL
- Linux Virtual Machine

---

# ⚠️ Safety Notice

This lab creates a temporary directory called:

    linux-links-lab

All commands in this lab should be executed inside this directory.

Do NOT run destructive commands outside the lab directory.

---

# 🏗️ PART 1 — Create the Lab Environment

Create the lab directory:

    mkdir -p ~/linux-links-lab

Enter the directory:

    cd ~/linux-links-lab

Check your current location:

    pwd

Expected output will look similar to:

    /home/yourusername/linux-links-lab

---

# 📄 PART 2 — Create the Original File

Create a file:

    echo "Linux Quest - Hard Link and Symbolic Link Lab" > original.txt

View the file:

    cat original.txt

Expected output:

    Linux Quest - Hard Link and Symbolic Link Lab

Check the file:

    ls -l original.txt

---

# 🔍 PART 3 — Check the Inode

Check the inode number:

    ls -li original.txt

Example:

    123456 -rw-r--r-- 1 user user 45 Jul 30 10:00 original.txt

Here:

    123456

is the inode number.

The number:

    1

represents the current hard link count.

---

# 🔗 PART 4 — Create a Hard Link

Create a hard link:

    ln original.txt hardlink.txt

List both files:

    ls -li original.txt hardlink.txt

You should notice:

    original.txt  → Same inode
    hardlink.txt  → Same inode

Example:

    123456 -rw-r--r-- 2 user user 45 Jul 30 10:00 original.txt
    123456 -rw-r--r-- 2 user user 45 Jul 30 10:00 hardlink.txt

Observe carefully:

    Same inode number
    Link count = 2

---

# 🧠 TASK 1

Answer the following:

1. Do `original.txt` and `hardlink.txt` have the same inode?
2. What is the current link count?
3. Are they two separate copies of the data?
4. What happens if you modify one of them?

Write your answers in your notes.

---

# ✏️ PART 5 — Modify the Hard Link

Append text using the original filename:

    echo "This line was added through original.txt" >> original.txt

Now check the hard link:

    cat hardlink.txt

Expected output:

    Linux Quest - Hard Link and Symbolic Link Lab
    This line was added through original.txt

Why?

Because both filenames point to the same inode and the same underlying data.

Check again:

    ls -li original.txt hardlink.txt

The inode numbers should still be identical.

---

# 🧠 TASK 2

Explain:

Why does modifying `original.txt` also modify what you see through `hardlink.txt`?

Expected concept:

    original.txt
          │
          ▼
      Same Inode
          ▲
          │
    hardlink.txt

Both filenames refer to the same underlying file.

---

# 🗑️ PART 6 — Delete the Original Filename

Delete the original filename:

    rm original.txt

List the directory:

    ls -li

You should still see:

    hardlink.txt

Now read the file:

    cat hardlink.txt

Expected output:

    Linux Quest - Hard Link and Symbolic Link Lab
    This line was added through original.txt

The file still exists.

Why?

Because `hardlink.txt` still points to the same inode.

---

# 🔬 PART 7 — Check the Inode After Deletion

Run:

    ls -li hardlink.txt

The inode still exists.

Conceptually:

    original.txt ❌

    hardlink.txt
          │
          ▼
       Inode
          │
          ▼
      File Data

The filename `original.txt` was deleted, but the underlying file data remained.

---

# 🧠 TASK 3

Answer:

What happened to the file after deleting `original.txt`?

Expected answer:

The directory entry for `original.txt` was removed, but the inode and data remained because `hardlink.txt` still referenced the inode.

---

# 🔗 PART 8 — Create a New Hard Link

Create another hard link:

    ln hardlink.txt backup.txt

Check:

    ls -li hardlink.txt backup.txt

Expected concept:

    hardlink.txt ───────┐
                        │
                        ▼
                    Same Inode
                        ▲
                        │
    backup.txt ─────────┘

Check the link count:

    ls -l hardlink.txt backup.txt

The link count should now be:

    2

---

# 🧠 TASK 4

How many filenames currently point to the same inode?

Answer:

    2

The filenames are:

    hardlink.txt
    backup.txt

---

# 🗑️ PART 9 — Delete One Hard Link

Delete:

    rm backup.txt

Check:

    ls -li hardlink.txt

The file still exists.

The link count should now be:

    1

Read the file:

    cat hardlink.txt

The data is still available.

---

# 🔗 PART 10 — Create a Symbolic Link

Create a new target file:

    echo "This is the target of a symbolic link" > target.txt

Create a symbolic link:

    ln -s target.txt symlink.txt

List files:

    ls -l

You should see something similar to:

    symlink.txt -> target.txt

---

# 🔍 PART 11 — Inspect the Symbolic Link

Run:

    ls -l symlink.txt

Example:

    lrwxrwxrwx 1 user user 10 Jul 30 10:00 symlink.txt -> target.txt

The first character is:

    l

This means:

    Symbolic Link

Check the target:

    readlink symlink.txt

Expected:

    target.txt

---

# 🔬 PART 12 — Compare Inodes

Run:

    ls -li target.txt symlink.txt

Observe:

    target.txt
        ↓
    One inode

    symlink.txt
        ↓
    Different inode

The symbolic link has its own inode.

It stores the path:

    target.txt

---

# 🧠 TASK 5

Answer:

1. Do `target.txt` and `symlink.txt` have the same inode?
2. What does the symbolic link store?
3. Can a symbolic link point to a directory?

Expected answers:

1. No.
2. The path of the target.
3. Yes.

---

# ✏️ PART 13 — Modify the Symbolic Link Target

Modify the target:

    echo "New data added to target" >> target.txt

Read through the symbolic link:

    cat symlink.txt

Expected output:

    This is the target of a symbolic link
    New data added to target

Why?

Because the symbolic link redirects access to the target file.

Conceptually:

    symlink.txt
          │
          ▼
      target.txt
          │
          ▼
       File Data

---

# 🗑️ PART 14 — Delete the Symbolic Link

Delete the symbolic link:

    rm symlink.txt

Check:

    ls -l

The target file should still exist:

    target.txt

Read it:

    cat target.txt

The data should still be present.

Important:

    rm symlink.txt

deletes only the symbolic link.

It does NOT delete the target.

---

# 🔗 PART 15 — Create the Symbolic Link Again

Create the link again:

    ln -s target.txt symlink.txt

Verify:

    ls -l symlink.txt

Expected:

    symlink.txt -> target.txt

---

# 🗑️ PART 16 — Delete the Symbolic Link Target

Now delete the target:

    rm target.txt

Check the symbolic link:

    ls -l symlink.txt

It may still appear as:

    symlink.txt -> target.txt

But the target no longer exists.

Try:

    cat symlink.txt

Expected:

    No such file or directory

The symlink is now broken.

---

# 💔 PART 17 — Find the Broken Symlink

Run:

    find . -xtype l

Expected output:

    ./symlink.txt

This confirms that `symlink.txt` is a dangling or broken symbolic link.

---

# 🧠 TASK 6

Answer:

What is the difference between:

    rm symlink.txt

and:

    rm target.txt

First case:

    rm symlink.txt

Result:

    Symlink deleted
    Target remains

Second case:

    rm target.txt

Result:

    Target deleted
    Symlink becomes broken

---

# 📁 PART 18 — Symbolic Link to a Directory

Create a directory:

    mkdir real-directory

Create a file inside:

    echo "File inside directory" > real-directory/file.txt

Create a symbolic link to the directory:

    ln -s real-directory directory-link

Check:

    ls -l directory-link

Expected:

    directory-link -> real-directory

Access through the symbolic link:

    ls directory-link

Expected:

    file.txt

Read the file through the symbolic link:

    cat directory-link/file.txt

Expected:

    File inside directory

---

# 🧠 TASK 7

Why is a symbolic link useful for directories?

Expected answer:

A symbolic link can provide an alternate path to a directory without copying the directory or its contents.

---

# 📊 PART 19 — Check File Metadata with stat

Create a file:

    echo "Metadata Lab" > metadata.txt

Run:

    stat metadata.txt

Observe:

- File size
- Inode
- Permissions
- Owner
- Group
- Access time
- Modify time
- Change time

The inode number displayed by `stat` should match:

    ls -li metadata.txt

---

# 🔢 PART 20 — Observe Link Count Using stat

Create a hard link:

    ln metadata.txt metadata-hard.txt

Check:

    stat metadata.txt

Then:

    stat metadata-hard.txt

Observe the inode numbers.

Both should have the same inode.

The link count should be:

    2

Concept:

    metadata.txt ───────┐
                        │
                        ▼
                    Same Inode
                        ▲
                        │
    metadata-hard.txt ──┘

---

# 🧪 PART 21 — Complete Hard Link Experiment

Run all commands:

    echo "Hard Link Experiment" > hard-original.txt

    ln hard-original.txt hard-copy.txt

    ls -li hard-original.txt hard-copy.txt

    echo "New line" >> hard-original.txt

    cat hard-copy.txt

    rm hard-original.txt

    cat hard-copy.txt

Expected result:

The file is still accessible through:

    hard-copy.txt

Reason:

Both names referenced the same inode.

---

# 🧪 PART 22 — Complete Symbolic Link Experiment

Run:

    echo "Symbolic Link Experiment" > soft-original.txt

    ln -s soft-original.txt soft-link.txt

    ls -li soft-original.txt soft-link.txt

    cat soft-link.txt

Now delete target:

    rm soft-original.txt

Try:

    cat soft-link.txt

Expected:

    No such file or directory

Find the broken link:

    find . -xtype l

Expected:

    ./soft-link.txt

---

# 🔍 PART 23 — Find All Symbolic Links

Run:

    find . -type l

This shows all symbolic links inside the current directory.

For more details:

    find . -type l -ls

---

# 💔 PART 24 — Find All Broken Symbolic Links

Run:

    find . -xtype l

This finds dangling symbolic links.

Difference:

    find . -type l
        ↓
    Finds symbolic links

    find . -xtype l
        ↓
    Finds broken symbolic links

---

# 🧠 PART 25 — Challenge: Identify the Link Type

Create:

    echo "Challenge" > challenge.txt

Create a hard link:

    ln challenge.txt challenge-hard.txt

Create a symbolic link:

    ln -s challenge.txt challenge-soft.txt

Now run:

    ls -li challenge.txt challenge-hard.txt challenge-soft.txt

Your task:

Identify:

    1. Which files have the same inode?
    2. Which file has a different inode?
    3. Which file stores a path?
    4. What is the link count?

Expected:

    challenge.txt
          │
          ├── Same inode as challenge-hard.txt
          │
          └── Different inode from challenge-soft.txt

---

# 🧠 PART 26 — Challenge: Predict the Output

Before running the commands, predict what will happen.

Commands:

    echo "Linux Quest" > test.txt

    ln test.txt hard.txt

    ln -s test.txt soft.txt

    rm test.txt

Now answer:

    cat hard.txt

Will it work?

Answer:

    Yes

Why?

    hard.txt → Same inode → Data still exists

Now:

    cat soft.txt

Will it work?

Answer:

    No

Why?

    soft.txt → Stores path test.txt
    test.txt → Deleted
    Therefore → Broken Symlink

---

# 🧪 PART 27 — Final Practical Challenge

Create a directory:

    mkdir final-challenge

Enter it:

    cd final-challenge

Create a file:

    echo "Linux Quest Final Challenge" > main.txt

Create:

1. One hard link
2. One symbolic link
3. One backup hard link

Commands:

    ln main.txt hard.txt

    ln -s main.txt soft.txt

    ln main.txt backup.txt

Check:

    ls -li

Now answer:

    1. How many unique inode numbers are there?
    2. Which files share the same inode?
    3. Which file has a different inode?
    4. What is the hard link count?
    5. What happens if main.txt is deleted?
    6. Which links continue to work?
    7. Which link becomes broken?

Expected concept:

    main.txt ────────┐
                     │
    hard.txt ────────┼────► Same Inode
                     │
    backup.txt ──────┘


    soft.txt
        │
        ▼
    "main.txt"
        │
        ▼
    Target Path

If `main.txt` is deleted:

    hard.txt       → Works ✅
    backup.txt     → Works ✅
    soft.txt       → Broken ❌

---

# 🧹 PART 28 — Clean Up the Lab

Return to the lab root:

    cd ~/linux-links-lab

Remove the lab directory:

    rm -rf final-challenge

Remove remaining test files:

    rm -f *.txt

Remove directories:

    rm -rf real-directory
    rm -f directory-link

Check:

    ls -la

The directory should be empty except for:

    .
    ..

You can remove the entire lab:

    cd ~

    rm -rf ~/linux-links-lab

---

# 📝 LAB QUESTIONS

Answer these questions after completing the lab.

## Q1. What is an inode?

Answer:

    ________________________________________

## Q2. Do hard links have the same inode?

Answer:

    ________________________________________

## Q3. Do symbolic links have the same inode as their target?

Answer:

    ________________________________________

## Q4. What command creates a hard link?

Answer:

    ________________________________________

## Q5. What command creates a symbolic link?

Answer:

    ________________________________________

## Q6. What happens when the original filename of a hard link is deleted?

Answer:

    ________________________________________

## Q7. What happens when the target of a symbolic link is deleted?

Answer:

    ________________________________________

## Q8. How do you find broken symbolic links?

Answer:

    ________________________________________

## Q9. Can symbolic links point to directories?

Answer:

    ________________________________________

## Q10. Can hard links generally cross filesystems?

Answer:

    ________________________________________

---

# 🎯 INTERVIEW TASK

Explain the following diagram:

                    ORIGINAL FILE
                         │
                         ▼
                      INODE
                         │
                  ┌──────┴──────┐
                  │             │
                  ▼             ▼
              HARD LINK     FILE DATA
                  │
                  │
                  └──── Same Inode


                    SYMBOLIC LINK
                         │
                         ▼
                    TARGET PATH
                         │
                         ▼
                    ORIGINAL FILE
                         │
                         ▼
                       INODE
                         │
                         ▼
                     FILE DATA

Your explanation should include:

- What an inode is
- How hard links work
- How symbolic links work
- What happens when a hard-linked filename is deleted
- What happens when a symbolic link target is deleted

---

# 🧠 LAB SUMMARY

## Hard Link

    ln source target

    source
       │
       ▼
    Inode
       ▲
       │
    target

Both names point to the same inode.

---

## Symbolic Link

    ln -s source target

    target
       │
       ▼
    Stores Path
       │
       ▼
    source
       │
       ▼
    Inode
       │
       ▼
    Data

The symbolic link has a different inode.

---

# ⭐ Key Commands Learned

    ln source target

Creates a hard link.

    ln -s source target

Creates a symbolic link.

    ls -li

Shows inode numbers.

    ls -l

Shows symbolic link targets.

    readlink link

Shows the target path of a symbolic link.

    readlink -f link

Resolves the complete path.

    stat file

Shows detailed file metadata.

    find . -type l

Finds symbolic links.

    find . -xtype l

Finds broken symbolic links.

---

# 🏆 LAB COMPLETION CHECKLIST

- [ ] Created lab environment
- [ ] Created original file
- [ ] Checked inode number
- [ ] Created hard link
- [ ] Compared inode numbers
- [ ] Checked link count
- [ ] Modified hard-linked file
- [ ] Deleted original filename
- [ ] Verified hard link still works
- [ ] Created symbolic link
- [ ] Checked symbolic link target
- [ ] Compared symbolic link inode
- [ ] Modified symbolic link target
- [ ] Deleted symbolic link
- [ ] Verified target still exists
- [ ] Deleted symbolic link target
- [ ] Created broken symbolic link
- [ ] Found broken symbolic link
- [ ] Created symbolic link to directory
- [ ] Used stat command
- [ ] Practiced hard link experiment
- [ ] Practiced symbolic link experiment
- [ ] Completed final challenge
- [ ] Answered lab questions

---

# 🚀 Linux Quest Progress

Level 02 — Linux File System

Lesson 09 — Linux File Links

🟢 Theory — Complete
🟢 Interview Preparation — Complete
🟢 Practical Lab — Complete

Status:

    🏆 LESSON 09 COMPLETE

Next:

    Level 02 → Lesson 10

Keep exploring. Keep breaking things safely. Keep learning Linux. 🐧🔥