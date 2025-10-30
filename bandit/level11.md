# Bandit Level 11 → Level 12

## 🧩 Goal
The password for the next level is stored in the file `data.txt`, where **all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13)**. Retrieve and decode the password. :contentReference[oaicite:0]{index=0}

---

## 🔑 Credentials
- **Username:** bandit11  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit11@bandit.labs.overthewire.org -p 2220
   ````

2. Confirm the file is present:

   ```bash
   ls -l
   file data.txt
   head -n 5 data.txt
   ```

3. The file contains ROT13-encoded text. Decode it using `tr` (or another ROT13-capable tool):

   ```bash
   cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
   ```

   That command translates letters by 13 positions (ROT13) and will print the decoded, human-readable string containing the password. ([Medium][1])

4. The decoded output will contain the password for `bandit12`. Copy it and use it to SSH into the next level:

   ```bash
   ssh bandit12@bandit.labs.overthewire.org -p 2220
   ```

---

## ✅ Example (concise one-liner)

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

The printed result is the password for the next level. ([OverTheWire][2])

---

## 💡 What I Learned

* What **ROT13** is (a simple Caesar-like substitution shifting letters by 13 positions) and when it’s useful as a quick obfuscation method. ([OverTheWire][2])
* How to use the `tr` command for character translation and simple decoding tasks (`tr 'A-Za-z' 'N-ZA-Mn-za-m'`). ([Twin Security][3])
* A repeatable workflow for small encoding puzzles: **inspect → identify encoding → apply decoding tool → verify** — useful for many CTF-style and real-world forensic tasks.

```
