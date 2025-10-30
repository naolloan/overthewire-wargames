# Bandit Level 4 → Level 5

## 🧩 Goal
Find the only human-readable file in the `inhere` directory and retrieve the password for the next level.

---

## 🔑 Credentials
- **Username:** bandit4  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit4@bandit.labs.overthewire.org -p 2220
   ````

2. List the contents of the current directory:

   ```bash
   ls
   ```

   You’ll see a directory called `inhere`.

3. Move into the directory:

   ```bash
   cd inhere
   ```

   Inside it, you’ll notice multiple files without extensions.

4. To identify which one contains readable text, use the `file` command:

   ```bash
   file ./*
   ```

   This command tells you the type of each file. One of them will say something like:

   ```
   ./-file07: ASCII text
   ```

5. Once you find the ASCII text file, display its content:

   ```bash
   cat ./-file07
   ```

6. The output will be the password for the next level.

---

## ✅ Solution

To summarize the commands:

```bash
cd inhere
file ./*
cat ./-file07
```

The content printed by the last command is the password for the next level (`bandit5`).

---

## 💡 What I Learned

In this level, I learned how to **differentiate between binary and text files** in Linux using the `file` command.
The `file` command inspects a file’s contents and reports its type, which makes it extremely helpful when dealing with unknown files.

I also learned to work more confidently with **files that have unusual names** and no extensions.
This level showed me that not everything readable is immediately obvious — and that tools like `file` can help identify hidden information quickly.

This challenge helped strengthen my understanding of file inspection in Linux, which is especially useful when analyzing unknown or potentially suspicious files in cybersecurity tasks.

```
