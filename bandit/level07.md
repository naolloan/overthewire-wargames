# Bandit Level 7 → Level 8

## 🧩 Goal
Find the password in the file `data.txt` — it is located **next to the word `millionth`**. Retrieve the password for the next level.

---

## 🔑 Credentials
- **Username:** bandit7  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit7@bandit.labs.overthewire.org -p 2220
   ````

2. Locate and inspect `data.txt` (usually in your home directory). Start by checking the file:

   ```bash
   ls -l
   file data.txt
   head -n 5 data.txt    # preview first few lines
   ```

3. Search for the line containing the word `millionth`:

   ```bash
   grep -n "millionth" data.txt
   ```

   This prints matching line number(s) and contents.

4. Extract the word immediately next to `millionth`. Several safe options are shown — any of these will work depending on whitespace/punctuation:

   * Using `awk` (robust, prints the word after `millionth` on matching lines):

     ```bash
     awk '/millionth/ {for(i=1;i<=NF;i++) if($i=="millionth") print $(i+1)}' data.txt
     ```

   * Using `grep` + `sed` to show the matching line, then `awk`:

     ```bash
     grep "millionth" data.txt | awk '{for(i=1;i<=NF;i++) if($i=="millionth") print $(i+1)}'
     ```

   * If punctuation is attached to the word, normalize separators and then extract:

     ```bash
     grep "millionth" data.txt | tr -s '[:space:][:punct:]' ' ' | awk '{for(i=1;i<=NF;i++) if($i=="millionth") print $(i+1)}'
     ```

   * Or print the full matching line and visually copy the password:

     ```bash
     grep "millionth" data.txt
     ```

5. The printed value is the password for the next level (`bandit8`). Copy it and use it to log in.

---

## ✅ Example (concise one-liner)

A compact command that finds and prints the word immediately after `millionth`:

```bash
awk '/millionth/ {for(i=1;i<=NF;i++) if($i=="millionth") print $(i+1)}' data.txt
```

---

## 💡 What I Learned

* How to **search for keywords** inside large text files (`grep`).
* How to **select the word next to a match** using text-processing tools like `awk` and `sed`.
* Dealing with punctuation and irregular spacing: sometimes you need to normalize input (e.g., with `tr`) before extracting a token.
* This level reinforced practical text-processing skills in the shell — a core ability when analyzing logs, dumps, or large data files during security investigations.

```
