# Bandit Level 8 → Level 9

## 🧩 Goal
The password for the next level is stored in the file `data.txt` and is **the only line that occurs once** in the file.

---

## 🔑 Credentials
- **Username:** bandit8  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit8@bandit.labs.overthewire.org -p 2220
   ````

2. Verify that `data.txt` exists:

   ```bash
   ls -l
   file data.txt
   ```

3. The goal is to find the **unique** line — that is, the line that appears only once.
   The `sort` and `uniq` commands can help:

   ```bash
   sort data.txt | uniq -u
   ```

   * `sort` — sorts all lines alphabetically (required for `uniq` to group duplicates correctly).
   * `uniq -u` — prints only lines that appear exactly once.

4. The output of the above command is the password for the next level (`bandit9`).

---

## ✅ Example (concise one-liner)

```bash
sort data.txt | uniq -u
```

---

## 💡 What I Learned

* How to use `sort` and `uniq` together to find **unique entries** in a dataset.
* The importance of sorting before using `uniq`, since `uniq` only detects consecutive duplicates.
* This challenge emphasized data filtering and pattern recognition — essential for log analysis and data forensics.

```
