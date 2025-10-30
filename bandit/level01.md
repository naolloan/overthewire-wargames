# Bandit Level 1 → Level 2

## 🧩 Goal
Learn how to read files with unusual names in the Linux terminal.

---

## 🔑 Credentials
- **Username:** bandit1  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the next level:
   ```bash
   ssh bandit1@bandit.labs.overthewire.org -p 2220
````

---

2. List the files in the home directory:

   ```bash
   ls
   ```

   You’ll see a file named `-

---`.

3. Since the file name starts with a dash (`-`), typing `cat -` won’t work because the terminal interprets it as an option.
   Instead, specify the full path to the file:

   ```bash
   cat ./-
   ```

---

4. This displays the password for the next level.

---

## ✅ Solution

The file `-` contains the password needed to log in to the next level (`bandit2`):

```bash
cat ./-
```

---

Copy the output and save it for the next login.

---

## 💡 What I Learned

In this level, I learned how Linux handles **files with special or confusing names**, such as those that begin with a dash (`-`).
At first, I tried `cat -`, but it didn’t work as expected — that’s when I learned that the shell thought I was passing an **option** instead of a **file name**.

After some research, I discovered that adding `./` before the file name tells the shell that the file is in the current directory, not a command option.
This small but important concept helped me understand how **Linux interprets paths and arguments**.

I also got more comfortable navigating directories and reading files through the terminal, which is a skill I’ll definitely use in later levels.
```
