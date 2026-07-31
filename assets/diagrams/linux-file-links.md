# 📊 Linux File Links — Hard Links & Symbolic Links

> A complete visual guide to Linux inodes, hard links, symbolic links, broken links, and filesystem boundaries.

---

# 1. 🧠 Linux File Structure — Name → Inode → Data

    ┌─────────────────┐
    │   File Name     │
    │   original.txt  │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────┐
    │ Directory Entry │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────┐
    │      Inode      │
    │                 │
    │ Permissions     │
    │ Owner           │
    │ Group           │
    │ File Size       │
    │ Timestamps      │
    │ Link Count      │
    └────────┬────────┘
             │
             ▼
    ┌─────────────────┐
    │   File Data     │
    │                 │
    │  Linux Quest    │
    └─────────────────┘

---

# 2. 🔗 Hard Link

A hard link is another directory entry that points to the same inode.

    ┌─────────────────┐
    │  original.txt   │
    └────────┬────────┘
             │
             ▼
       ┌───────────┐
       │   Inode   │
       │  #12345   │
       │ Link Count│
       │     2     │
       └─────┬─────┘
             │
             ▼
       ┌────────────┐
       │ File Data  │
       │            │
       │ Linux Quest│
       └────────────┘
             ▲
             │
             │
    ┌────────┴────────┐
    │  hardlink.txt   │
    └─────────────────┘

### Mental Model

    original.txt ────────┐
                         │
                         ▼
                     SAME INODE
                         │
                         ▼
                     SAME DATA
                         ▲
                         │
                         │
    hardlink.txt ────────┘

Create a hard link:

    ln original.txt hardlink.txt

Check inode numbers:

    ls -li original.txt hardlink.txt

Both files should show the same inode number.

---

# 3. 🔗 Symbolic Link

A symbolic link stores the path of another file or directory.

    ┌─────────────────┐
    │  symlink.txt    │
    │                 │
    │  Special File   │
    └────────┬────────┘
             │
             │ Stores Path
             ▼
    ┌─────────────────┐
    │ "original.txt"  │
    └────────┬────────┘
             │
             │ Follows Path
             ▼
    ┌─────────────────┐
    │  original.txt   │
    └────────┬────────┘
             │
             ▼
       ┌───────────┐
       │   Inode   │
       │  #12345   │
       └─────┬─────┘
             │
             ▼
       ┌────────────┐
       │ File Data  │
       │            │
       │ Linux Quest│
       └────────────┘

Create a symbolic link:

    ln -s original.txt symlink.txt

Check:

    ls -l symlink.txt

Example:

    symlink.txt -> original.txt

---

# 4. 🆚 Hard Link vs Symbolic Link

              HARD LINK
                  │
                  ▼
        ┌─────────────────┐
        │   File Name     │
        └────────┬────────┘
                 │
                 ▼
            SAME INODE
                 │
                 ▼
             FILE DATA


           SYMBOLIC LINK
                  │
                  ▼
        ┌─────────────────┐
        │     Symlink     │
        └────────┬────────┘
                 │
                 ▼
           TARGET PATH
                 │
                 ▼
        ┌─────────────────┐
        │   Target File   │
        └────────┬────────┘
                 │
                 ▼
               INODE
                 │
                 ▼
             FILE DATA

---

# 5. 📊 Complete Comparison

    ┌──────────────────────────────────────────────────────────┐
    │                    HARD LINK                             │
    ├──────────────────────────────────────────────────────────┤
    │                                                          │
    │  original.txt ──────┐                                    │
    │                     │                                    │
    │                     ▼                                    │
    │                 SAME INODE                               │
    │                     │                                    │
    │                     ▼                                    │
    │                 FILE DATA                                │
    │                     ▲                                    │
    │                     │                                    │
    │  hardlink.txt ──────┘                                    │
    │                                                          │
    └──────────────────────────────────────────────────────────┘


    ┌──────────────────────────────────────────────────────────┐
    │                  SYMBOLIC LINK                           │
    ├──────────────────────────────────────────────────────────┤
    │                                                          │
    │  symlink.txt                                             │
    │       │                                                  │
    │       ▼                                                  │
    │  "original.txt"                                          │
    │       │                                                  │
    │       ▼                                                  │
    │  original.txt                                            │
    │       │                                                  │
    │       ▼                                                  │
    │     INODE                                                │
    │       │                                                  │
    │       ▼                                                  │
    │   FILE DATA                                              │
    │                                                          │
    └──────────────────────────────────────────────────────────┘

---

# 6. 🔢 Inode Comparison

    ┌─────────────────┐
    │  original.txt   │
    │                 │
    │  Inode: 12345   │
    └────────┬────────┘
             │
             │ SAME INODE
             ▼
    ┌─────────────────┐
    │  hardlink.txt   │
    │                 │
    │  Inode: 12345   │
    └─────────────────┘


    ┌─────────────────┐
    │  symlink.txt    │
    │                 │
    │  Inode: 67890   │
    └────────┬────────┘
             │
             │ Stores Target Path
             ▼
       original.txt
             │
             ▼
       Inode: 12345

Commands:

    ls -i original.txt
    ls -i hardlink.txt
    ls -i symlink.txt

Expected:

    original.txt  → 12345
    hardlink.txt  → 12345
    symlink.txt   → 67890

---

# 7. 🧪 Creating Both Types of Links

Create original file:

    touch original.txt

Create hard link:

    ln original.txt hardlink.txt

Create symbolic link:

    ln -s original.txt symlink.txt

Visual:

                         original.txt
                              │
                              ▼
                         Inode #1234
                              │
                              ▼
                         File Data
                              ▲
                              │
                 ┌────────────┴────────────┐
                 │                         │
                 │                         │
                 ▼                         ▼
          hardlink.txt                symlink.txt
                 │                         │
                 │                         │
                 ▼                         ▼
           SAME INODE                TARGET PATH
                                           │
                                           ▼
                                      original.txt

---

# 8. 📝 Modifying a Hard Link

    original.txt
          │
          ▼
      Inode #1234
          ▲
          │
          │
    hardlink.txt

Run:

    echo "Linux Quest" > original.txt

Then:

    echo "Modified through hard link" >> hardlink.txt

Now:

    cat original.txt

Output:

    Linux Quest
    Modified through hard link

Why?

    original.txt
          │
          └──────► SAME INODE
                        ▲
                        │
    hardlink.txt ───────┘

                  ↓

             SAME FILE DATA

---

# 9. 📝 Modifying a Symbolic Link

    symlink.txt
          │
          ▼
    original.txt
          │
          ▼
      Inode #1234
          │
          ▼
      File Data

Run:

    echo "Modified through symlink" >> symlink.txt

The data of `original.txt` is modified because the symbolic link redirects the operation to its target.

    symlink.txt
          │
          ▼
    original.txt
          │
          ▼
      SAME FILE DATA

---

# 10. 🗑️ Delete Original — Hard Link

Before deletion:

    original.txt ───────┐
                         │
                         ▼
                     Inode #1234
                         ▲
                         │
    hardlink.txt ────────┘

Delete:

    rm original.txt

After deletion:

    original.txt ❌

                     ┌──────────────┐
                     │ Inode #1234  │
                     └──────┬───────┘
                            ▲
                            │
                    hardlink.txt
                            │
                            ▼
                        File Data

Result:

    hardlink.txt
         │
         ▼
    Still Works ✅

The data remains because another hard link still references the inode.

---

# 11. 🗑️ Delete Target — Symbolic Link

Before deletion:

    symlink.txt
         │
         ▼
    original.txt
         │
         ▼
    File Data

Delete target:

    rm original.txt

After deletion:

    symlink.txt
         │
         ▼
    original.txt ❌
         │
         X
    Target Missing

Result:

    symlink.txt
         │
         ▼
    Broken Symbolic Link 💔

---

# 12. 💔 Broken Symbolic Link

A broken symbolic link points to a path that no longer exists.

    ┌─────────────────┐
    │   symlink.txt   │
    └────────┬────────┘
             │
             │ points to
             ▼
    ┌─────────────────┐
    │  original.txt   │
    │                 │
    │  ❌ NOT FOUND   │
    └─────────────────┘
             │
             ▼
       BROKEN SYMLINK

Find broken links:

    find . -xtype l

---

# 13. 📁 Symbolic Link to Directory

Symbolic links can point to directories.

    ┌──────────────────────┐
    │   project-link/      │
    │                      │
    │   Symbolic Link      │
    └──────────┬───────────┘
               │
               │ points to
               ▼
    ┌──────────────────────┐
    │      project/        │
    │                      │
    │  ├── src/            │
    │  ├── docs/           │
    │  └── README.md       │
    └──────────────────────┘

Command:

    ln -s project project-link

Now:

    cd project-link

takes you to:

    project/

---

# 14. 🚫 Hard Links to Directories

Normal users generally cannot create hard links to directories.

        HARD LINK
            │
            ▼
      Regular File
            │
            ▼
        Allowed ✅


        HARD LINK
            │
            ▼
        Directory
            │
            ▼
     Normally Not Allowed ❌

Example:

    ln directory hardlink

Normally fails.

The special directory entries:

    .
    ..

are managed internally by the filesystem and are not ordinary user-created hard links.

---

# 15. 💾 Filesystem Boundary

## Hard Link

    FILESYSTEM A

    ┌─────────────────────────┐
    │                         │
    │  original.txt           │
    │       │                 │
    │       ▼                 │
    │    Inode 1234           │
    │       ▲                 │
    │       │                 │
    │  hardlink.txt           │
    │                         │
    └─────────────────────────┘

              ❌

    FILESYSTEM B

    ┌─────────────────────────┐
    │                         │
    │ Different inode space   │
    │                         │
    └─────────────────────────┘

Hard links generally cannot cross filesystem boundaries.

---

## Symbolic Link

    FILESYSTEM A                    FILESYSTEM B

    ┌─────────────────┐             ┌─────────────────┐
    │ symlink.txt     │             │ original.txt    │
    │                 │             │                 │
    │ /path/to/file ──┼────────────►│ File Data       │
    └─────────────────┘             └─────────────────┘

Symbolic links can cross filesystem boundaries because they store a path.

---

# 16. 🌍 Real-World Symbolic Link Example

Application deployment:

    application/
    │
    ├── releases/
    │   │
    │   ├── v1/
    │   │
    │   ├── v2/
    │   │
    │   └── v3/
    │
    └── current
           │
           ▼
          v3

The application uses:

    application/current

When a new version is deployed:

    current
       │
       ▼
      v4

The application continues using:

    application/current

No application configuration change is required.

---

# 17. 🛠️ Important Commands

Create hard link:

    ln source target

Create symbolic link:

    ln -s source target

View links:

    ls -l

View inode numbers:

    ls -li

Show symbolic link target:

    readlink symlink.txt

Show resolved path:

    readlink -f symlink.txt

Find symbolic links:

    find . -type l

Find broken symbolic links:

    find . -xtype l

View detailed metadata:

    stat file.txt

---

# 18. 📊 Quick Comparison Table

| Feature | Hard Link | Symbolic Link |
|---|---|---|
| Points to | Same inode | Target path |
| Own inode | No, shares inode | Yes |
| Same file data | Yes | Accesses target data |
| Survives target filename deletion | Yes, if another hard link exists | No |
| Can become broken | No, under normal link semantics | Yes |
| Cross filesystem | Generally no | Yes |
| Can point to directory | Normally no for users | Yes |
| Command | `ln` | `ln -s` |
| Check | `ls -li` | `ls -l` / `readlink` |

---

# 19. 🧠 Final Mental Model

                    LINUX FILE LINKS
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ▼                           ▼
        HARD LINK                  SYMBOLIC LINK
             │                           │
             ▼                           ▼
        SAME INODE                  STORES PATH
             │                           │
             ▼                           ▼
        SAME DATA                   TARGET FILE
             │                           │
             │                           ▼
             │                         INODE
             │                           │
             ▼                           ▼
      Another hard link            Actual Data
      can keep data alive
      after one name is deleted
             │
             ▼
      Usually same filesystem

---

# 20. 🏆 Quick Revision

    HARD LINK
        ↓
    Same inode
        ↓
    Same data
        ↓
    Usually same filesystem
        ↓
    Another hard link can preserve data
        ↓
    Cannot normally link directories


    SYMBOLIC LINK
        ↓
    Stores target path
        ↓
    Different inode
        ↓
    Can cross filesystems
        ↓
    Can point to directories
        ↓
    Can become broken

---

# 🐧 Linux Quest — Chapter 09

## Linux File Links

    Inodes              → 🟢 Complete
    Hard Links          → 🟢 Complete
    Symbolic Links      → 🟢 Complete
    Link Creation       → 🟢 Complete
    Link Deletion       → 🟢 Complete
    Broken Symlinks     → 🟢 Complete
    Filesystem Limits   → 🟢 Complete
    Visual Diagram      → 🟢 Complete

Status:

    🟢 Diagram Complete