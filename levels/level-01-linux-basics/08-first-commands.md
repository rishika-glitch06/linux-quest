# 💻 08 - First Linux Commands

## 📍 Where Are We?

**Linux Quest → Level 01: Linux Basics**

```text
✅ 01 - What is Linux?
✅ 02 - History of Linux
✅ 03 - Why Linux?
✅ 04 - Linux Kernel
✅ 05 - Linux Distributions
✅ 06 - GUI vs CLI
✅ 07 - Terminal Basics
🟢 08 - First Linux Commands (Current Lesson)
⬜ 09 - Linux File System Navigation
⬜ 10 - Working with Files & Directories
```

---

# 📚 In This Lesson You'll Learn

By the end of this lesson, you'll be able to:

- List files and folders
- Navigate between directories
- Create folders
- Create files
- Remove empty directories
- Understand absolute and relative paths
- Build confidence using the Linux terminal

---

# 👋 Let's Start

Now that you've learned how to use the Terminal, it's time to actually work with the Linux file system.

These commands are the building blocks of almost everything you'll do in Linux.

Whether you're a software developer, DevOps engineer, cybersecurity analyst, or cloud engineer—you'll use these commands almost every day.

Let's begin with the commands every Linux user should know.
---

# 📖 Understanding File Navigation

Every file and folder in Linux lives inside a directory.

Before creating or editing files, you should know:

- Where you are
- What files are present
- How to move between folders

These three commands make that possible:

- `pwd`
- `ls`
- `cd`

---

# 📌 Command

```bash
pwd
```

## 📖 What is it?

Prints your current working directory.

## ⚙️ Syntax

```bash
pwd
```

## 💻 Example

```bash
pwd
```

## 📤 Sample Output

```text
/home/rishika
```

## 🌍 Real World Use

Know your current location before creating or deleting files.

## ⚠️ Common Mistake

Thinking it changes directories—it only displays your current location.

## 💡 Pro Tip

If you're ever confused where you are, type `pwd`.

## 🧪 Try It Yourself

```bash
pwd
```

---

# 📌 Command

```bash
ls
```

## 📖 What is it?

Lists files and folders in the current directory.

## ⚙️ Syntax

```bash
ls
```

## 💻 Example

```bash
ls
```

## 📤 Sample Output

```text
Desktop
Documents
Downloads
Music
Pictures
Videos
```

## 🌍 Real World Use

Check what files and folders exist before opening, copying, or deleting them.

## ⚠️ Common Mistake

Expecting hidden files to appear. Use:

```bash
ls -a
```

to view hidden files.

## 💡 Pro Tip

Use:

```bash
ls -l
```

for detailed information.

## 🧪 Try It Yourself

```bash
ls
ls -a
ls -l
```

---

# 📌 Command

```bash
cd
```

## 📖 What is it?

Changes the current directory.

## ⚙️ Syntax

```bash
cd directory_name
```

## 💻 Example

```bash
cd Documents
```

## 📤 Example

```bash
pwd
/home/rishika

cd Documents

pwd
/home/rishika/Documents
```

## 🌍 Real World Use

Navigate through folders while working on projects.

## ⚠️ Common Mistake

Trying to enter a folder that doesn't exist.

## 💡 Pro Tip

Use:

```bash
cd ..
```

to move one directory back.

Use:

```bash
cd ~
```

to return to your Home directory.

## 🧪 Try It Yourself

```bash
pwd
ls
cd Documents
pwd
cd ..
pwd
```

---

# 🧩 Fun Fact

Every Linux user—from beginners to Linux kernel developers—uses `ls`, `pwd`, and `cd` almost every day.
---

# 📌 Command

```bash
mkdir
```

## 📖 What is it?

Creates a new directory (folder).

## ⚙️ Syntax

```bash
mkdir directory_name
```

## 💻 Example

```bash
mkdir LinuxQuest
```

## 📤 Sample Output

A new folder named `LinuxQuest` is created.

## 🌍 Real World Use

Used to organize projects and create new working directories.

## ⚠️ Common Mistake

Trying to create a folder that already exists.

## 💡 Pro Tip

Create multiple folders at once:

```bash
mkdir project docs images
```

## 🧪 Try It Yourself

```bash
mkdir practice
ls
```

---

# 📌 Command

```bash
touch
```

## 📖 What is it?

Creates a new empty file.

## ⚙️ Syntax

```bash
touch filename
```

## 💻 Example

```bash
touch notes.txt
```

## 📤 Sample Output

Creates an empty file named `notes.txt`.

## 🌍 Real World Use

Useful for creating configuration files, scripts, and notes.

## ⚠️ Common Mistake

Forgetting the file extension when it's needed.

## 🧪 Try It Yourself

```bash
touch file1.txt
ls
```

---

# 📌 Command

```bash
rmdir
```

## 📖 What is it?

Deletes an empty directory.

## ⚙️ Syntax

```bash
rmdir directory_name
```

## 💻 Example

```bash
rmdir practice
```

## 🌍 Real World Use

Used to remove directories that no longer contain files.

## ⚠️ Common Mistake

`rmdir` works **only** on empty directories.

---

# 🧩 Real World Scenario

Imagine you're starting a new project.

```bash
mkdir LinuxProject
cd LinuxProject
touch README.md
ls
```

You've just created a project folder and your first file inside it.