# ⌨️ 07 - Terminal Basics

## 📍 Where Are We?

**Linux Quest → Level 01: Linux Basics**

```text
✅ 01 - What is Linux?
✅ 02 - History of Linux
✅ 03 - Why Linux?
✅ 04 - Linux Kernel
✅ 05 - Linux Distributions
✅ 06 - GUI vs CLI
🟢 07 - Terminal Basics (Current Lesson)
⬜ 08 - First Linux Commands
```

---

# 📚 In This Lesson You'll Learn

By the end of this lesson, you'll be able to:

- Understand what a Terminal is
- Learn the difference between Terminal and Shell
- Know what Bash, Zsh, and Fish are
- Understand the Terminal Prompt
- Run your first Linux commands
- Read command output confidently

---

# 👋 Let's Start

Until now, we've talked about Linux.

Today, we'll finally interact with it.

When you open a Terminal, you're opening a doorway to your operating system.

Every command you type is a conversation with Linux.

This is where every Linux engineer, DevOps engineer, cybersecurity analyst, and cloud engineer spends a significant part of their day.

Let's open that door.
---

# 📖 What is a Terminal?

A **Terminal** is an application that allows you to interact with the operating system by typing commands.

Instead of clicking buttons, you communicate directly with Linux through text commands.

Think of it as a bridge between **you** and the **operating system**.

Popular Linux terminals include:

- GNOME Terminal
- Konsole
- Xfce Terminal
- Tilix
- Kitty

---

# 📖 Terminal vs Shell

Many beginners think the Terminal and Shell are the same thing—but they're not.

| Terminal | Shell |
|-----------|-------|
| A program you open | A program that understands your commands |
| Displays text | Executes commands |
| Example: GNOME Terminal | Example: Bash |

Simply put:

> **Terminal = Window**
>
> **Shell = Brain**

The Terminal lets you type commands, while the Shell interprets and executes them.

---

# 🐚 Popular Linux Shells

## Bash (Bourne Again Shell)

- Default shell on many Linux distributions
- Most widely used
- Beginner-friendly
- Great for scripting

---

## Zsh

- More customizable
- Better auto-completion
- Popular with developers

---

## Fish

- Beginner-friendly
- Colorful interface
- Smart suggestions while typing

---

# 📍 Understanding the Terminal Prompt

When you open the terminal, you'll usually see something like:

```bash
rishika@ubuntu:~$
```

Let's break it down:

- **rishika** → Current user
- **ubuntu** → Computer name (hostname)
- **~** → Home directory
- **$** → Normal user

If you ever see:

```bash
#
```

It usually means you're working as the **root user**.

---
# 🖼️ Big Picture

Every command you type follows a simple journey before it reaches the hardware.

> 📁 Diagram available in: `assets/diagrams/terminal-basics-overview.md`

Think of it like this:

- You type a command in the **Terminal**
- The **Shell** understands and processes it
- The **Linux Kernel** performs the requested operation
- The hardware executes the task

# 🚀 Your First Linux Commands

We're finally typing commands! 🎉

---

## 📌 Command

```bash
pwd
```

### 📖 What does it do?

Displays the **current working directory**.

### 🧠 Syntax

```bash
pwd
```

### 💻 Example

```bash
pwd
```

### 📤 Sample Output

```text
/home/rishika
```

### 🌍 Real World Use

Useful whenever you want to know your current location in the Linux file system.

### ⚠️ Common Mistake

Confusing `pwd` with `cd`.

### 💡 Pro Tip

Always run `pwd` if you're unsure where you are.

---

## 📌 Command

```bash
whoami
```

### 📖 What does it do?

Displays the username of the currently logged-in user.

### 🧠 Syntax

```bash
whoami
```

### 💻 Example

```bash
whoami
```

### 📤 Sample Output

```text
rishika
```

### 🌍 Real World Use

Useful when managing multiple users or remote servers.

### ⚠️ Common Mistake

Thinking it shows your full profile—it only displays the username.

---

## 📌 Command

```bash
hostname
```

### 📖 What does it do?

Displays the name of your computer.

### 💻 Example

```bash
hostname
```

### 📤 Sample Output

```text
ubuntu
```

### 🌍 Real World Use

Helpful while working with multiple systems or servers.

---

## 📌 Command

```bash
date
```

### 📖 What does it do?

Displays the current system date and time.

### 💻 Example

```bash
date
```

### 📤 Sample Output

```text
Mon Jul 20 10:35:12 IST 2026
```
---

# 🧪 Try It Yourself

Open your terminal and run:

```bash
pwd
whoami
hostname
date
```

### ✅ Expected Output

- `pwd` → Shows your current directory
- `whoami` → Displays your current username
- `hostname` → Displays your computer's name
- `date` → Shows the current date and time

💡 Don't worry if your output looks different from the examples. Every system has its own username, hostname, and current time.

### 🌍 Real World Use

Useful while checking logs, troubleshooting, or scheduling tasks.
---

## 📌 Command

```bash
clear
```

### 📖 What does it do?

Clears the terminal screen.

### 🧠 Syntax

```bash
clear
```

### 💻 Example

```bash
clear
```

### 🌍 Real World Use

Useful when your terminal becomes cluttered and you want a clean workspace.

---

## 📌 Command

```bash
echo
```

### 📖 What does it do?

Displays text or variables on the terminal.

### 💻 Example

```bash
echo "Hello Linux!"
```

### 📤 Sample Output

```text
Hello Linux!
```

### 🌍 Real World Use

Widely used in shell scripting to display messages or variable values.

---

## 📌 Command

```bash
history
```

### 📖 What does it do?

Displays previously executed commands.

### 💻 Example

```bash
history
```

### 🌍 Real World Use

Useful when you want to rerun or review commands you've already executed.

---

## 📌 Command

```bash
uname
```

### 📖 What does it do?

Displays information about your operating system.

### 💻 Example

```bash
uname -a
```

### 🌍 Real World Use

Helpful for checking kernel and system information while troubleshooting.

---

## 📌 Command

```bash
cal
```

### 📖 What does it do?

Displays a calendar in the terminal.

### 💻 Example

```bash
cal
```

> 💡 Note: On some modern Linux distributions, `cal` may not be installed by default. You can install it later if needed.

---

# 🧩 Fun Fact

Many Linux users spend most of their day inside a terminal. Once you become comfortable with it, you'll often find it faster than using a graphical interface.

---

# 📝 Command Summary

| Command | Purpose |
|---------|---------|
| pwd | Print current directory |
| whoami | Show current user |
| hostname | Show computer name |
| date | Show current date & time |
| clear | Clear terminal screen |
| echo | Display text |
| history | Show command history |
| uname | Show system information |
| cal | Display calendar |

---

# 📝 Quick Recap

Today you learned:

- ✅ What a Terminal is
- ✅ Difference between Terminal and Shell
- ✅ Popular Linux shells
- ✅ Understanding the terminal prompt
- ✅ Your first Linux commands

---

# 🎯 Mini Challenge

Open your terminal and try running these commands:

```bash
pwd
whoami
hostname
date
echo "Linux Quest"
history
uname -a
```

Can you identify what each command does without looking back?

---

# ☕ Coffee Break

Congratulations! 🎉

You've officially started interacting with Linux through the terminal. Every Linux professional starts here.

---

# 🧭 What's Next?

## 📂 Lesson 08 – First Linux Commands

We'll learn:

- ls
- cd
- mkdir
- touch
- rmdir

These are the commands you'll use almost every day.