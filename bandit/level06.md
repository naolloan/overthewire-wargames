# Bandit Level 5 → Level 6

## 🧩 Goal
Locate the file (somewhere under `/home`) that is **owned by user `bandit7` and group `bandit6`**, and read it to retrieve the password for the next level.

---

## 🔑 Credentials
- **Username:** bandit5  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit5@bandit.labs.overthewire.org -p 2220
   ````

2. Search the `/home` tree for files owned by `bandit7` and group `bandit6`. These `find` commands are reliable ways to locate the target file:

   * To list matching files and their permissions/owners:

     ```bash
     find /home -user bandit7 -group bandit6 -type f -ls
     ```

   * To print the path(s) only:

     ```bash
     find /home -user bandit7 -group bandit6 -type f
     ```

   * To show and immediately display the content of any matching file (use with care):

     ```bash
     find /home -user bandit7 -group bandit6 -type f -exec cat {} \; -print
     ```

   If `find` produces many results, inspect the file types first:

   ```bash
   find /home -user bandit7 -group bandit6 -type f -exec file {} \; -print
   ```

3. Once you identify the correct file (the one containing ASCII text / the password), display it with `cat`:

   ```bash
   cat /path/to/the/found-file
   ```

   Replace `/path/to/the/found-file` with the path returned by `find`.

---

## ✅ Solution

A concise example sequence that finds and prints the password:

```bash
# find a file owned by bandit7:bandit6 and print its content
find /home -user bandit7 -group bandit6 -type f -exec cat {} \; -quit
```

The output produced by the `cat` command is the password for the next level (`bandit6`). Copy it and use it to log in.

---

## 💡 What I Learned

This level taught me how to use the `find` command effectively to search by **file owner** and **group**, which is essential for locating files with specific permission/ownership constraints. Key takeaways:

* `find /home -user <user> -group <group> -type f` searches for regular files with the specified owner and group.
* Combining `find` with `-exec` lets you act on search results immediately (for example, `-exec cat {} \;` to display contents).
* When multiple matches are possible, use `file` to determine which files are human-readable (e.g., ASCII text) before `cat`ing them.
* Understanding ownership and group membership is an important step in filesystem forensics and privilege-aware searching.

This challenge reinforced practical skills in targeted filesystem search and safe inspection of files on Linux systems.

```
```
