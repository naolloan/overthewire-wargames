# Bandit Level 3 → Level 4

## 🧩 Goal
Find and read a hidden file located inside the `inhere` directory to retrieve the password for the next level.

---

## 🔑 Credentials
- **Username:** bandit3  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit3@bandit.labs.overthewire.org -p 2220
   ````

2. List the files in the home directory:

   ```bash
   ls
   ```

   You’ll see a directory named `inhere`.

3. Navigate into the directory:

   ```bash
   cd inhere
   ```

4. List all files, including hidden ones:

   ```bash
   ls -a
   ```

   You’ll notice a hidden file named `.hidden`.

5. Display the content of the hidden file:

   ```bash
   cat .hidden
   ```

6. The terminal will print the password for the next level.

---

## ✅ Solution

To summarize the steps:

```bash
cd inhere
ls -a
cat .hidden
```

The output from the last command is the password for the next level (`bandit4`).

---

## 💡 What I Learned

In this level, I learned how to locate **hidden files** in Linux systems.
By default, files and directories whose names start with a dot (`.`) are hidden and don’t appear when using a normal `ls` command.

I discovered that adding the `-a` flag to `ls` (`ls -a`) reveals these hidden files, which is useful when troubleshooting or exploring system directories.
I also practiced **navigating between directories** and **reading file contents** confidently using basic shell commands.

This challenge taught me that even the simplest Linux directories can contain hidden information, and knowing how to uncover it is a key skill for anyone working with systems or cybersecurity.

```
