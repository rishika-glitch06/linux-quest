# 🛣️ Linux File Paths & Navigation

> A visual guide to understanding absolute paths, relative paths, and special path symbols in Linux.

---

# 🌳 Linux Path Structure

```text
/
│
├── home/
│   └── rishika/
│       ├── Documents/
│       │   └── Linux/
│       │
│       ├── Downloads/
│       │
│       └── Projects/
│
├── etc/
│
├── var/
│   └── log/
│
└── usr/
    ├── bin/
    └── share/
```

---

# 1. 📍 Absolute Path

An absolute path starts from the Root Directory `/`.

```text
/
└── home
    └── rishika
        └── Documents
            └── Linux
```

The absolute path is:

```text
/home/rishika/Documents/Linux
```

### Example

```bash
cd /home/rishika/Documents/Linux
```

### 🧠 Remember

```text
Absolute Path
      │
      ▼
Starts from /
      │
      ▼
Complete location
```

---

# 2. 📂 Relative Path

A relative path starts from the current working directory.

Suppose you are currently here:

```text
/home/rishika
```

And the structure is:

```text
/home/rishika
├── Documents
│   └── Linux
├── Downloads
└── Projects
```

You can navigate using:

```bash
cd Documents/Linux
```

Here:

```text
Documents/Linux
```

is a relative path.

### 🧠 Remember

```text
Relative Path
      │
      ▼
Starts from current location
      │
      ▼
Does NOT start with /
```

---

# 3. ⚖️ Absolute vs Relative Path

```text
Current Location:
/home/rishika
        │
        │
        ├─────────────── Absolute Path
        │
        ▼
/home/rishika/Documents/Linux


        │
        │
        └─────────────── Relative Path
                        │
                        ▼
                  Documents/Linux
```

Both reach:

```text
/home/rishika/Documents/Linux
```

---

# 4. 🧭 Navigation Symbols

```text
┌────────┬──────────────────────────────┐
│ Symbol │ Meaning                      │
├────────┼──────────────────────────────┤
│   /    │ Root Directory               │
│   ~    │ Current User's Home          │
│   .    │ Current Directory            │
│   ..   │ Parent Directory             │
│   -    │ Previous Working Directory   │
└────────┴──────────────────────────────┘
```

---

# 5. 🌳 Root Directory `/`

```text
/
│
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

The `/` directory is the starting point of the entire Linux file system.

Command:

```bash
cd /
```

---

# 6. 🏠 Home Directory `~`

The `~` symbol represents the current user's home directory.

```text
~
│
▼
/home/rishika
```

Command:

```bash
cd ~
```

Equivalent to:

```bash
cd /home/rishika
```

---

# 7. 📍 Current Directory `.`

The `.` symbol represents the current directory.

Example:

```bash
ls .
```

Meaning:

```text
List contents of current directory
```

Visual:

```text
Current Directory
       │
       ▼
      .
```

---

# 8. ⬆️ Parent Directory `..`

The `..` symbol represents the parent directory.

Example:

```text
/home/rishika/Documents
                │
                │ cd ..
                ▼
/home/rishika
```

Command:

```bash
cd ..
```

---

# 9. 🔙 Previous Directory `-`

The `-` symbol with `cd` takes you to the previous working directory.

Example:

```text
/etc
  │
  │ cd /var
  ▼
/var
  │
  │ cd -
  ▼
/etc
```

Command:

```bash
cd -
```

---

# 10. 🧭 Navigation Flow

```text
                 Start
                   │
                   ▼
             pwd
                   │
                   ▼
       Current Working Directory
                   │
                   ▼
             ┌───────────┐
             │    cd     │
             └───────────┘
                   │
          ┌────────┴────────┐
          │                 │
          ▼                 ▼
    Absolute Path      Relative Path
          │                 │
          ▼                 ▼
   /home/rishika      Documents/Linux
          │                 │
          └────────┬────────┘
                   ▼
             New Location
                   │
                   ▼
                  pwd
```

---

# 11. 🛠️ Essential Navigation Commands

```text
pwd
│
└── Show current location


ls
│
└── List directory contents


cd /
│
└── Go to Root


cd ~
│
└── Go to Home


cd ..
│
└── Go to Parent Directory


cd -
│
└── Go to Previous Directory


cd <directory>
│
└── Enter a directory
```

---

# 🧠 Quick Memory Map

```text
/   → Root
~   → Home
.   → Current Directory
..  → Parent Directory
-   → Previous Directory
```

---

# 🎯 Key Takeaway

```text
Absolute Path
    ↓
Starts from /
    ↓
Complete location

Relative Path
    ↓
Starts from current location
    ↓
Depends on where you are
```

---

## 🔗 Related Resources

📖 [Lesson 03 — Linux File Paths & Navigation](../../levels/level-02-file-system/03-linux-file-paths-and-navigation.md)

💼 [Linux File System Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [Linux File System Lab](../../labs/01-linux-file-system-lab.md)

🏠 [Back to Linux Quest](../../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 03**

> *Understand paths. Navigate with confidence.*