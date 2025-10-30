# Bandit Level 2 → Level 3

## 🧩 Goal
Find and read the file named `--spaces in this filename--` located in the home directory and retrieve the password for the next level.

---

## 🔑 Credentials
- **Username:** bandit2  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit2@bandit.labs.overthewire.org -p 2220
   ````

2. List files in the home directory:

   ```bash
   ls -la
   ```

   You should see a file named `--spaces in this filename--`.

3. Read the file. Because the filename contains spaces and begins with dashes, you can use any of these safe forms:

   * Using `./` to avoid option parsing:

     ```bash
     cat ./--spaces\ in\ this\ filename--
     ```

   * Quoting the filename:

     ```bash
     cat "--spaces in this filename--"
     ```

   * Using `--` to mark the end of options, then the filename:

     ```bash
     cat -- --spaces\ in\ this\ filename--
     ```

   * Or combine `./` with quotes:

     ```bash
     cat "./--spaces in this filename--"
     ```

4. The command will print the password for the next level to your terminal.

---

## ✅ Solution

Any of the commands above will display the password. For example:

```bash
cat "./--spaces in this filename--"
```

Copy the printed password and use it to log in as `bandit3`.

---

## 💡 What I Learned

This level taught me how to handle **filenames that include spaces and leading dashes**, both of which can confuse shell commands:

* Filenames that begin with `-` can be mistaken for command options. Using `./` or `--` prevents the shell from interpreting the filename as an option.
* Filenames with spaces must be quoted or have their spaces escaped (e.g., `\ `).
* Multiple safe techniques exist (`./`, quoting, `--`), and knowing them helps prevent mistakes when working with unusual file names.

This exercise strengthened my understanding of how the shell parses arguments and the practical ways to avoid argument-parsing pitfalls.
