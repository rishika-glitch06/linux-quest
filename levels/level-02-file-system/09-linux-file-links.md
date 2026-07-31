# 🐧 Linux Quest — Level 02
# 📚 Chapter 09: Linux File Links

> Learn how Linux uses hard links and symbolic links to create multiple references to files and directories.

---

# 🎯 Learning Objectives

By the end of this lesson, you will understand:

- What links are in Linux
- What an inode is
- What a hard link is
- What a symbolic link is
- The difference between hard links and symbolic links
- How link counts work
- What happens when files are deleted
- What broken or dangling symbolic links are
- How links interact with filesystems
- How to create and inspect links
- When to use hard links and symbolic links

---

# 1. Introduction to Linux Links

In Linux, a filename is not the actual file.

A filename is an entry in a directory that points to an inode.

The inode contains information about the actual file and points to the data stored on disk.

The basic relationship is:

    Filename
        │
        ▼
    Directory Entry
        │
        ▼
    Inode
        │
        ▼
    File Data

Linux allows multiple filenames to refer to the same underlying file.

This is achieved using links.

There are two major types of links:

    1. Hard Links
    2. Symbolic Links

---

# 2. Understanding the Inode

An inode is a data structure used by a Linux filesystem to store information about a file.

An inode contains metadata such as:

- File type
- File permissions
- File owner
- Group owner
- File size
- Timestamps
- Number of hard links
- Pointers to data blocks

An inode does NOT normally store the filename.

The filename is stored separately in the directory structure.

The relationship looks like:

    Filename
        │
        ▼
    Directory Entry
        │
        ▼
    Inode
        │
        ├── Permissions
        ├── Owner
        ├── Group
        ├── File Size
        ├── Timestamps
        ├── Link Count
        │
        ▼
    Data Blocks

You can view an inode number using:

    ls -li filename

Example:

    ls -li file.txt

The first number in the output is the inode number.

---

# 3. Why Are Inodes Important for Links?

Hard links work because multiple directory entries can point to the same inode.

For example:

    file1.txt
        │
        ▼
    Inode 1234
        │
        ▼
    File Data

A hard link creates another directory entry:

    file1.txt ───────┐
                    │
                    ▼
                Inode 1234
                    │
                    ▼
                File Data
                    ▲
                    │
    file2.txt ───────┘

Both filenames refer to the same inode.

Therefore:

    file1.txt
    file2.txt

are two names for the same underlying file.

---

# 4. What is a Hard Link?

A hard link is another directory entry that points directly to the same inode as an existing file.

Create a hard link using:

    ln source.txt hardlink.txt

Example:

    echo "Linux Quest" > original.txt

    ln original.txt hardlink.txt

Now:

    original.txt ───────┐
                        │
                        ▼
                    Inode 1001
                        │
                        ▼
                    File Data
                        ▲
                        │
    hardlink.txt ───────┘

Both files have:

- Same inode
- Same data
- Same permissions
- Same metadata
- Same underlying file

Check inode numbers:

    ls -li original.txt hardlink.txt

The inode numbers will be the same.

---

# 5. Hard Link is Not a Copy

A common misunderstanding is that creating a hard link creates a copy.

That is incorrect.

Suppose:

    original.txt
         │
         ▼
       Inode
         │
         ▼
      Data

After creating a hard link:

    original.txt ───────┐
                        │
                        ▼
                      Inode
                        │
                        ▼
                      Data
                        ▲
                        │
    hardlink.txt ───────┘

There is still only one set of file data.

Both names access the same data.

If you modify one:

    echo "New Line" >> original.txt

The change will also be visible through:

    cat hardlink.txt

This happens because both filenames refer to the same inode.

---

# 6. Hard Link Count

Every inode keeps track of how many hard links point to it.

Suppose:

    original.txt

Initially:

    Link Count = 1

Create:

    ln original.txt hardlink.txt

Now:

    original.txt ───────┐
                        │
                        ▼
                    Inode
                Link Count = 2
                        ▲
                        │
    hardlink.txt ───────┘

Create another:

    ln original.txt backup.txt

Now:

    original.txt ───────┐
                        │
    hardlink.txt ───────┼──► Inode
                        │    Link Count = 3
    backup.txt ─────────┘

The link count can be viewed using:

    ls -l

or:

    stat filename

---

# 7. What Happens When a Hard Link is Deleted?

Suppose:

    original.txt ───────┐
                        │
                        ▼
                    Inode
                Link Count = 2
                        ▲
                        │
    hardlink.txt ───────┘

Run:

    rm original.txt

Now:

    original.txt ❌

    hardlink.txt
          │
          ▼
        Inode
    Link Count = 1
          │
          ▼
      File Data

The actual file data is NOT deleted.

The inode still exists because another hard link points to it.

The file data is removed only when:

- Link count becomes zero
- No process has the file open

This is an important Linux concept.

---

# 8. What is a Symbolic Link?

A symbolic link is also called:

- Symlink
- Soft link

Unlike a hard link, a symbolic link does not directly point to the target's inode.

Instead, it stores the path of the target.

Create a symbolic link:

    ln -s original.txt symlink.txt

Relationship:

    symlink.txt
          │
          ▼
    Stores Path
          │
          ▼
    original.txt
          │
          ▼
        Inode
          │
          ▼
      File Data

The symbolic link has its own inode.

The target file has a different inode.

---

# 9. Example of a Symbolic Link

Create a file:

    echo "Linux Quest" > original.txt

Create a symbolic link:

    ln -s original.txt symlink.txt

Check:

    ls -l

Output may look like:

    symlink.txt -> original.txt

This means:

    symlink.txt
         │
         ▼
    original.txt

Check the link target:

    readlink symlink.txt

Output:

    original.txt

---

# 10. Hard Link vs Symbolic Link

The most important difference:

    HARD LINK
        │
        ▼
    Points to Inode

    SYMBOLIC LINK
        │
        ▼
    Stores Path

Visual comparison:

    HARD LINK

    file1.txt ───────┐
                     │
                     ▼
                   Inode
                     │
                     ▼
                 File Data
                     ▲
                     │
    file2.txt ───────┘


    SYMBOLIC LINK

    symlink.txt
         │
         ▼
    "file1.txt"
         │
         ▼
    file1.txt
         │
         ▼
       Inode
         │
         ▼
     File Data

---

# 11. Hard Link and Symbolic Link Comparison

| Feature | Hard Link | Symbolic Link |
|---|---|---|
| Points to | Inode | Path |
| Inode | Same as target | Different inode |
| Data | Same underlying data | Accesses target data |
| Can point to directory | Normally no | Yes |
| Cross filesystem | Generally no | Yes |
| Broken link possible | No | Yes |
| Target deleted | Link still works if another hard link exists | Link becomes broken |
| Command | ln | ln -s |
| Inode number | Same | Different |

---

# 12. What Happens When the Original File is Deleted?

Consider:

    original.txt ───────┐
                        │
                        ▼
                    Inode 1234
                        ▲
                        │
    hardlink.txt ───────┘

Delete:

    rm original.txt

Result:

    original.txt ❌

    hardlink.txt
          │
          ▼
      Inode 1234
          │
          ▼
       Data

The hard link still works.

Now consider a symbolic link:

    symlink.txt
          │
          ▼
    original.txt
          │
          ▼
       Inode 1234

Delete:

    rm original.txt

Result:

    original.txt ❌

    symlink.txt
          │
          ▼
    Missing Target ❌

The symbolic link becomes broken.

---

# 13. Broken or Dangling Symbolic Links

A symbolic link whose target no longer exists is called:

- Broken symlink
- Dangling symlink

Example:

    symlink.txt
          │
          ▼
    original.txt
          │
          X
    Target Deleted

The symbolic link still exists, but the target path is invalid.

Find broken symbolic links using:

    find . -xtype l

---

# 14. Removing a Symbolic Link

To remove a symbolic link:

    rm symlink.txt

This removes only the link.

It does NOT remove the target.

Example:

    symlink.txt -> original.txt

Run:

    rm symlink.txt

Result:

    symlink.txt ❌
    original.txt ✅

The target remains untouched.

---

# 15. Symbolic Links to Directories

Symbolic links can point to directories.

Example:

    ln -s /var/log logs

Now:

    logs
      │
      ▼
    /var/log

You can use:

    cd logs

The system treats the symbolic link as another path to the directory.

This is very useful for:

- Application deployments
- Configuration directories
- Version management
- Shortening long paths

---

# 16. Hard Links to Directories

Hard links to directories are normally not allowed for regular users.

This restriction exists to prevent filesystem cycles and maintain directory structure consistency.

Therefore:

    Hard Link → Regular File ✅

    Hard Link → Directory ❌ Normally Not Allowed

Special directory entries:

    .
    ..

are filesystem-managed and are not normal user-created hard links.

---

# 17. Hard Links and Filesystems

Hard links generally cannot cross filesystem boundaries.

Why?

Because a hard link directly references an inode.

An inode belongs to a particular filesystem.

Example:

    Filesystem A
        │
        ▼
      Inode 1234
        ▲
        │
    Hard Link
        │
        X
    Filesystem B

Trying to create such a link may result in:

    Invalid cross-device link

---

# 18. Symbolic Links and Filesystems

Symbolic links can cross filesystem boundaries.

Why?

Because a symbolic link stores a path.

Example:

    Filesystem A

    symlink
        │
        ▼
    /mnt/data/file.txt
        │
        ▼

    Filesystem B

    file.txt

The symbolic link does not directly reference the target inode.

Therefore, it can point to a target located on another filesystem.

---

# 19. Absolute Symbolic Links

An absolute symbolic link contains the complete path.

Example:

    ln -s /home/user/project/file.txt link.txt

The link stores:

    /home/user/project/file.txt

Advantages:

- Clear target path
- Works regardless of current directory

Disadvantage:

- Can break if the directory structure changes

---

# 20. Relative Symbolic Links

A relative symbolic link contains a path relative to its location.

Example:

    ln -s ../project/file.txt link.txt

The link stores:

    ../project/file.txt

Relative links are useful when moving an entire directory structure.

They maintain relationships between files using relative paths.

---

# 21. Important Commands

## Create Hard Link

    ln source target

Example:

    ln file.txt hardlink.txt

---

## Create Symbolic Link

    ln -s source target

Example:

    ln -s file.txt symlink.txt

---

## Check Inode Number

    ls -li file.txt

---

## List Symbolic Link

    ls -l symlink.txt

---

## Show Symbolic Link Target

    readlink symlink.txt

---

## Resolve Full Symbolic Link Path

    readlink -f symlink.txt

---

## Show File Metadata

    stat file.txt

---

## Find Symbolic Links

    find . -type l

---

## Find Broken Symbolic Links

    find . -xtype l

---

# 22. Understanding ls -li

Run:

    ls -li

Example:

    12345 -rw-r--r-- 2 user user 100 file.txt

The fields represent:

    12345
       │
       └── Inode Number

    -rw-r--r--
       │
       └── Permissions

    2
       │
       └── Hard Link Count

    user
       │
       └── Owner

    user
       │
       └── Group

    100
       │
       └── File Size

    file.txt
       │
       └── Filename

---

# 23. Understanding Link Count

Suppose:

    file.txt

Link count:

    1

After:

    ln file.txt hard.txt

Link count:

    2

After:

    ln file.txt backup.txt

Link count:

    3

After:

    rm hard.txt

Link count:

    2

After:

    rm backup.txt

Link count:

    1

Finally:

    rm file.txt

Link count:

    0

If no process has the file open, the filesystem can reclaim the inode and data blocks.

---

# 24. Why Do Hard Links Share the Same Inode?

A hard link is not a separate file.

It is another directory entry pointing to the same inode.

Therefore:

    file1.txt
         │
         ▼
    Directory Entry
         │
         ▼
       Inode
         │
         ▼
      File Data

and:

    file2.txt
         │
         ▼
    Directory Entry
         │
         ▼
       Same Inode
         │
         ▼
      Same Data

This is why:

    ls -li file1.txt file2.txt

shows the same inode number.

---

# 25. Why Symbolic Links Have Different Inodes

A symbolic link is itself a filesystem object.

Therefore:

    target.txt
         │
         ▼
      Inode A
         │
         ▼
      Data


    symlink.txt
         │
         ▼
      Inode B
         │
         ▼
    Stores Path
         │
         ▼
      target.txt

Therefore:

    Target Inode ≠ Symlink Inode

---

# 26. Important Difference in Deletion

## Hard Link

    original.txt ───────┐
                        ▼
                      Inode
                        ▲
                        │
    hardlink.txt ───────┘

Delete:

    rm original.txt

Result:

    hardlink.txt → Still Works ✅

---

## Symbolic Link

    symlink.txt
          │
          ▼
    original.txt
          │
          ▼
        Inode

Delete:

    rm original.txt

Result:

    symlink.txt → Broken ❌

---

# 27. Real-World Use Cases of Hard Links

Hard links can be useful when:

- Multiple filenames need to refer to the same file
- You want to avoid duplicate data
- You want a file to remain accessible through multiple names
- You need filesystem-level references to the same inode

However, hard links are less commonly used in everyday administration compared to symbolic links.

---

# 28. Real-World Use Cases of Symbolic Links

Symbolic links are widely used for:

### Application Deployments

Example:

    current -> releases/v3

When deploying a new version:

    current -> releases/v4

The application can continue using:

    /app/current

without changing its configuration.

---

### Configuration Files

A symbolic link can point to a configuration file stored elsewhere.

Example:

    /etc/app/config
          │
          ▼
    /opt/app/configs/production.conf

---

### Shortcuts to Long Paths

Instead of:

    cd /var/www/my-application/project

Create:

    ln -s /var/www/my-application/project ~/project

Now:

    cd ~/project

---

# 29. Common Mistakes

## Mistake 1: Thinking Hard Links Are Copies

Incorrect:

    Hard Link = Copy

Correct:

    Hard Link = Another Directory Entry to Same Inode

---

## Mistake 2: Thinking Symlinks Share the Same Inode

Incorrect:

    Symlink = Same Inode

Correct:

    Symlink = Different Inode + Target Path

---

## Mistake 3: Thinking Deleting Original Always Deletes Data

Incorrect:

    rm original.txt = Data Immediately Deleted

Correct:

    Data remains if another hard link exists.

---

## Mistake 4: Thinking Symlink Target Deletion Deletes Symlink

Incorrect:

    Delete Target = Symlink Automatically Removed

Correct:

    Delete Target = Symlink Becomes Broken

---

## Mistake 5: Confusing Link Count with File Copies

Link count does not represent the number of copies.

It represents the number of directory entries referencing the inode.

---

# 30. Practical Example

Create:

    echo "Linux Quest" > original.txt

Create hard link:

    ln original.txt hard.txt

Create symbolic link:

    ln -s original.txt soft.txt

Now:

    original.txt ───────┐
                        │
                        ▼
                      Inode
                        │
                        ▼
                      Data
                        ▲
                        │
    hard.txt ───────────┘


    soft.txt
        │
        ▼
    "original.txt"
        │
        ▼
    original.txt

Check:

    ls -li original.txt hard.txt soft.txt

Expected:

    original.txt → Same inode as hard.txt
    hard.txt     → Same inode as original.txt
    soft.txt     → Different inode

---

# 31. Important Interview Concepts

### Question: What is an inode?

Answer:

> An inode is a filesystem data structure that stores metadata about a file and pointers to its data blocks. It does not normally store the filename.

---

### Question: What is a hard link?

Answer:

> A hard link is another directory entry pointing to the same inode as an existing file.

---

### Question: What is a symbolic link?

Answer:

> A symbolic link is a special file that stores the pathname of another file or directory.

---

### Question: What happens when a hard-linked file is deleted?

Answer:

> Only the directory entry is removed. The data remains accessible through other hard links.

---

### Question: What happens when a symlink target is deleted?

Answer:

> The symbolic link becomes dangling or broken.

---

### Question: Can hard links cross filesystems?

Answer:

> Generally no, because hard links directly reference inodes belonging to a specific filesystem.

---

### Question: Can symbolic links cross filesystems?

Answer:

> Yes, because they store pathnames instead of directly referencing inodes.

---

### Question: Can hard links point to directories?

Answer:

> Normally no for regular users.

---

### Question: Can symbolic links point to directories?

Answer:

> Yes.

---

# 32. Quick Revision

    INODE
    ↓
    Stores file metadata
    ↓
    Does not normally store filename


    HARD LINK
    ↓
    Same inode
    ↓
    Same data
    ↓
    Same filesystem generally
    ↓
    Cannot normally point to directories


    SYMBOLIC LINK
    ↓
    Stores target path
    ↓
    Different inode
    ↓
    Can point to files/directories
    ↓
    Can cross filesystems
    ↓
    Can become broken

---

# 33. Hard Link vs Symbolic Link — Memory Trick

Remember:

    HARD LINK
        ↓
    H = Hard → Holds the inode directly

    SYMBOLIC LINK
        ↓
    S = Symbolic → Stores the path symbolically

Or simply:

    HARD LINK
    "Same Inode"

    SOFT LINK
    "Stores Path"

---

# 34. Key Takeaways

1. A filename is a directory entry pointing to an inode.
2. An inode stores metadata and pointers to file data.
3. Hard links point directly to the same inode.
4. Hard links are not copies.
5. Multiple hard links share the same data.
6. Hard links have the same inode number.
7. The link count represents the number of hard-link references.
8. Deleting one hard link does not necessarily delete the file data.
9. Symbolic links store the path of their target.
10. Symbolic links have their own inode.
11. Symbolic links can point to files and directories.
12. Symbolic links can cross filesystem boundaries.
13. A deleted symlink target creates a dangling symlink.
14. Hard links generally cannot cross filesystem boundaries.
15. Hard links normally cannot point to directories.
16. `ln` creates hard links.
17. `ln -s` creates symbolic links.
18. `ls -li` shows inode numbers.
19. `readlink` shows a symbolic link's target.
20. `find . -xtype l` can find broken symbolic links.

---

# 35. 🏆 Chapter Summary

                    LINUX FILE LINKS
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ▼                           ▼
        HARD LINK                  SYMBOLIC LINK
             │                           │
             ▼                           ▼
        Same Inode                  Own Inode
             │                           │
             ▼                           ▼
        Same Data                  Stores Path
             │                           │
             ▼                           ▼
    Usually Same FS              Can Cross FS
             │                           │
             ▼                           ▼
    Cannot Normally Point        Can Point to
       to Directories             Directories
             │                           │
             ▼                           ▼
    Survives Other Name          Can Become Broken
       Being Deleted             If Target Deleted

---

# 🐧 Linux Quest Progress

Level 02 — Linux File System

Chapter 09 — Linux File Links

🟢 Inodes — Complete
🟢 Hard Links — Complete
🟢 Symbolic Links — Complete
🟢 Link Count — Complete
🟢 Broken Symlinks — Complete
🟢 Filesystem Boundaries — Complete
🟢 Absolute & Relative Symlinks — Complete
🟢 Real-World Use Cases — Complete

Next:

➡️ Chapter 10 — File Permissions and Ownership

Keep learning. Keep experimenting. Keep mastering Linux. 🐧🔥