# 🧪 Linux Quest — Level 02
# Lab 06: Linux Users & Groups

> Practice Linux user management, group management, UID, GID, identity files, and administrative privileges.

---

## 🎯 Lab Objectives

In this lab, you will practice:

- Identifying the current user
- Checking UID and GID
- Checking logged-in users
- Exploring `/etc/passwd`
- Exploring `/etc/group`
- Understanding `/etc/shadow`
- Creating users
- Creating groups
- Setting passwords
- Adding users to groups
- Managing primary and secondary groups
- Modifying users
- Removing users from groups
- Deleting users and groups
- Using `sudo`
- Verifying user and group configuration

---

# ⚠️ Important Safety Note

This lab modifies users and groups on your Linux system.

For practice, use test names such as:

```text
questuser
questgroup
```

Do not delete or modify important system users or groups.

If you are using a college Linux machine or shared system, perform only the commands permitted by your administrator.

---

# 🧩 Part 1 — Check the Current User

## Task

Find the username of the currently logged-in user.

Run:

```bash
whoami
```

### Expected Result

You should see your current username.

Example:

```text
rishika
```

### Record Your Result

```text
Current User:
```

---

# 🧩 Part 2 — Check UID and GID

## Task

Display your complete user and group identity information.

Run:

```bash
id
```

### Expected Output

You may see something similar to:

```text
uid=1000(rishika) gid=1000(rishika) groups=1000(rishika)
```

### Questions

1. What is your UID?

```text
Answer:
```

2. What is your primary GID?

```text
Answer:
```

3. What groups does your user belong to?

```text
Answer:
```

---

## Task 2.1 — Display Only UID

Run:

```bash
id -u
```

Record:

```text
My UID:
```

---

## Task 2.2 — Display Only Groups

Run:

```bash
id -G
```

Record:

```text
My Group IDs:
```

---

# 🧩 Part 3 — Check Group Membership

## Task

Run:

```bash
groups
```

### Record Your Result

```text
My Groups:
```

### Question

What is the difference between:

```bash
id
```

and:

```bash
groups
```

### Answer

```text
id:
Displays UID, GID, and detailed group information.

groups:
Displays the groups associated with the user.
```

---

# 🧩 Part 4 — Check Logged-in Users

## Task 4.1

Run:

```bash
who
```

Observe the output.

---

## Task 4.2

Run:

```bash
w
```

Observe the additional information.

---

## Task 4.3

Run:

```bash
users
```

Compare the outputs.

### Questions

1. Which command provides detailed information about logged-in users?

```text
Answer:
```

2. Which command mainly displays usernames?

```text
Answer:
```

---

# 🧩 Part 5 — Explore `/etc/passwd`

## Task

Display the contents of `/etc/passwd`.

Run:

```bash
cat /etc/passwd
```

For easier viewing:

```bash
less /etc/passwd
```

### Find Your User

Run:

```bash
grep "^$(whoami):" /etc/passwd
```

### Observe

Identify:

```text
Username:
UID:
GID:
Home Directory:
Login Shell:
```

---

## 🔎 Challenge

Run:

```bash
getent passwd $(whoami)
```

Compare the output with:

```bash
grep "^$(whoami):" /etc/passwd
```

### Question

Why might `getent` be preferred in some environments?

### Answer

```text
getent queries the system's configured name service databases,
which may include sources beyond local files.
```

---

# 🧩 Part 6 — Understand `/etc/passwd` Fields

Consider this example:

```text
questuser:x:1001:1001:Quest User:/home/questuser:/bin/bash
```

Identify:

```text
Username:
Password Placeholder:
UID:
GID:
User Information:
Home Directory:
Login Shell:
```

### Expected Answer

```text
Username            → questuser
Password Placeholder → x
UID                 → 1001
GID                 → 1001
User Information    → Quest User
Home Directory      → /home/questuser
Login Shell         → /bin/bash
```

---

# 🧩 Part 7 — Explore `/etc/group`

## Task

Display group information.

Run:

```bash
cat /etc/group
```

Or:

```bash
less /etc/group
```

Find a specific group:

```bash
getent group sudo
```

If your system has a `sudo` group, observe its members.

You can also search for your username:

```bash
grep "$(whoami)" /etc/group
```

---

# 🧩 Part 8 — Understand `/etc/shadow`

## Task

Check the permissions of `/etc/shadow`.

Run:

```bash
ls -l /etc/shadow
```

Try:

```bash
cat /etc/shadow
```

### Expected Result

A normal non-root user may receive a permission denied error.

If you have administrative privileges, you can inspect it with:

```bash
sudo cat /etc/shadow
```

⚠️ Do not copy or share the contents of this file.

### Questions

1. Why is `/etc/shadow` protected?

```text
Answer:
```

2. What kind of information does it contain?

```text
Answer:
```

### Expected Answer

```text
/etc/shadow contains sensitive password and authentication-related
information, so access to it is restricted.
```

---

# 🧩 Part 9 — Check the Root User

## Task

Run:

```bash
id root
```

### Expected Result

You should see:

```text
uid=0(root)
```

### Questions

1. What is the UID of root?

```text
Answer: 0
```

2. Why is UID 0 special?

```text
Answer:
UID 0 represents the superuser identity and has extensive
administrative privileges.
```

---

# 🧩 Part 10 — Create a Test Group

## Task

Create a group called:

```text
questgroup
```

Run:

```bash
sudo groupadd questgroup
```

Verify:

```bash
getent group questgroup
```

### Expected Output

Something similar to:

```text
questgroup:x:1001:
```

The GID may be different on your system.

### Record

```text
Quest Group GID:
```

---

# 🧩 Part 11 — Create a Test User

## Task

Create a user called:

```text
questuser
```

Create it with a home directory:

```bash
sudo useradd -m questuser
```

Verify:

```bash
id questuser
```

Also check:

```bash
getent passwd questuser
```

### Record

```text
Username:
UID:
Primary GID:
Home Directory:
Login Shell:
```

---

# 🧩 Part 12 — Set a Password

## Task

Set a password for the test user.

Run:

```bash
sudo passwd questuser
```

Enter a temporary practice password.

⚠️ Do not use a real password that you use elsewhere.

---

# 🧩 Part 13 — Add User to Secondary Group

## Task

Add `questuser` to `questgroup`.

Run:

```bash
sudo usermod -aG questgroup questuser
```

Verify:

```bash
id questuser
```

Also run:

```bash
groups questuser
```

### Expected Result

The user should now belong to:

```text
questgroup
```

---

# 🧩 Part 14 — Understand `-aG`

## Question

What does this command mean?

```bash
sudo usermod -aG questgroup questuser
```

### Answer

```text
-a
→ Append the group without removing existing supplementary groups.

-G
→ Specify supplementary groups.

questgroup
→ Group to add.

questuser
→ User being modified.
```

### Important

The following is safer for adding a secondary group:

```bash
sudo usermod -aG questgroup questuser
```

The `-a` option helps preserve existing supplementary group memberships.

---

# 🧩 Part 15 — Check Primary and Secondary Groups

Run:

```bash
id questuser
```

Observe:

```text
uid=
gid=
groups=
```

### Identify

```text
UID:
Primary GID:
Secondary Groups:
```

### Question

Which field represents the primary group?

### Answer

```text
gid=
```

---

# 🧩 Part 16 — Modify the User

## Task

Change the login shell of `questuser`.

Run:

```bash
sudo usermod -s /bin/bash questuser
```

Verify:

```bash
getent passwd questuser
```

Look at the final field.

Expected:

```text
/bin/bash
```

---

# 🧩 Part 17 — Remove User from Group

## Task

Remove `questuser` from `questgroup`.

Run:

```bash
sudo gpasswd -d questuser questgroup
```

Verify:

```bash
groups questuser
```

Or:

```bash
id questuser
```

### Question

Is `questgroup` still listed as a supplementary group?

```text
Answer:
```

---

# 🧩 Part 18 — Delete the Test User

⚠️ Make sure you are deleting only the test user created for this lab.

Run:

```bash
sudo userdel -r questuser
```

Verify:

```bash
id questuser
```

### Expected Result

You should receive an error indicating that the user does not exist.

---

# 🧩 Part 19 — Delete the Test Group

Delete the test group:

```bash
sudo groupdel questgroup
```

Verify:

```bash
getent group questgroup
```

### Expected Result

No matching group should be returned.

---

# 🧩 Part 20 — Final Verification

Run the following commands:

```bash
whoami
```

```bash
id
```

```bash
groups
```

```bash
who
```

```bash
w
```

```bash
users
```

You have now practiced Linux identity and user management commands.

---

# 🧠 Lab Questions

## Q1. What command shows your current username?

```text
Answer:
```

---

## Q2. What command shows UID and GID?

```text
Answer:
```

---

## Q3. What is the UID of root?

```text
Answer:
```

---

## Q4. Which file stores basic user information?

```text
Answer:
```

---

## Q5. Which file stores password-related information?

```text
Answer:
```

---

## Q6. Which file stores group information?

```text
Answer:
```

---

## Q7. What command creates a user?

```text
Answer:
```

---

## Q8. What command creates a group?

```text
Answer:
```

---

## Q9. How do you add a user to a secondary group?

```text
Answer:
```

---

## Q10. Why is `-a` important in `usermod -aG`?

```text
Answer:
```

---

## Q11. What is the difference between primary and secondary groups?

```text
Answer:
```

---

## Q12. What is `sudo` used for?

```text
Answer:
```

---

# 🎯 Challenge Tasks

Complete these tasks without looking at previous commands.

### Challenge 1

Create:

```text
User: linuxquest
Group: learners
```

---

### Challenge 2

Create the user with a home directory.

---

### Challenge 3

Set a password for the user.

---

### Challenge 4

Add the user to the `learners` group.

---

### Challenge 5

Verify:

```text
UID
GID
Primary Group
Secondary Group
Home Directory
```

---

### Challenge 6

Remove the user from the `learners` group.

---

### Challenge 7

Delete the test user.

---

### Challenge 8

Delete the test group.

---

# 🏆 Lab Completion Checklist

- [ ] Checked current user using `whoami`
- [ ] Checked UID using `id`
- [ ] Checked GID using `id`
- [ ] Checked groups using `groups`
- [ ] Checked logged-in users using `who`
- [ ] Used `w`
- [ ] Used `users`
- [ ] Explored `/etc/passwd`
- [ ] Explored `/etc/group`
- [ ] Checked `/etc/shadow` permissions
- [ ] Checked root UID
- [ ] Created a test group
- [ ] Created a test user
- [ ] Created a home directory
- [ ] Set a password
- [ ] Added user to a secondary group
- [ ] Verified group membership
- [ ] Modified the user
- [ ] Removed user from group
- [ ] Deleted test user
- [ ] Deleted test group
- [ ] Completed challenge tasks

---

# 📊 Skills Practiced

```text
Linux Users
     │
     ▼
UID & GID
     │
     ▼
Linux Groups
     │
     ▼
Primary & Secondary Groups
     │
     ▼
User Management
     │
     ▼
Group Management
     │
     ▼
Authentication Files
     │
     ▼
sudo & Privilege Management
     │
     ▼
Linux System Administration
```

---

# 🧠 What I Learned

Write a short summary of what you learned in this lab:

```text
1.
2.
3.
4.
5.
```

---

# 📝 Lab Reflection

### The most useful command I learned:

```text
Command:
```

### The most difficult concept:

```text
Concept:
```

### One thing I want to practice again:

```text
Topic:
```

### One interview question I can now answer confidently:

```text
Question:
```

---

# 🏁 Lab Status

```text
Lab 06 — Linux Users & Groups

Status: 🟢 Completed

Level 02 Progress:
████████████████████ 100%
```

> 🐧 **Linux Quest — Level 02, Lab 06 Complete**

> *Understand users. Manage groups. Control privileges. Secure Linux.*

---

## 🔗 Related Resources

📖 [Lesson 06 — Linux Users & Groups](../levels/level-02-file-system/06-linux-users-and-groups.md)

🖼️ [Linux Users & Groups Diagram](../assets/diagrams/linux-users-and-groups.md)

💼 [Linux Users & Groups Interview Preparation](../interview-prep/linux-file-system.md)

🏠 [Back to Linux Quest](../README.md)