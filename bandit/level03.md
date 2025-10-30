# Bandit Level 2 → Level 3

## 🧩 Goal
Find and read a hidden file located inside the `inhere` directory.

---

## 🔑 Credentials
- **Username:** bandit2  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the next level:
   ```bash
   ssh bandit2@bandit.labs.overthewire.org -p 2220
   ````

2. List the files in the current directory:

   ```bash
   ls
   ```

   You’ll see a directory named `inhere`.

3. Move into that directory:

   ```bash
   cd inhere
   ```

4. List all files, including hidden ones:

   ```bash
   ls -a
   ```

   A hidden file named `.hidden` will appear.

5. Display the content of the hidden file:

   ```bash
   cat .hidden
   ```

6. The password for the next level will be shown in the terminal.

---

## ✅ Solution

To summarize the commands used:

```bash
cd inhere
ls -a
cat .hidden
```

The output from the last command is the password for the next level (`bandit3`).

---

## 💡 What I Learned

In this level, I learned about **hidden files** in Linux systems.
I discovered that files starting with a dot (`.`) are hidden by default and don’t appear when using the normal `ls` command.

I had to use the `ls -a` flag to reveal them.
This taught me that Linux hides certain configuration or sensitive files by default — something that’s useful both in system administration and cybersecurity.

This level also reinforced my understanding of **navigating directories** and using simple yet powerful commands like `ls`, `cd`, and `cat`.
It was satisfying to find the hidden file and realize how many secrets a Linux system can conceal if you don’t know where to look.

```
