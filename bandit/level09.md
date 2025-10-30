# Bandit Level 9 → Level 10

## 🧩 Goal
The password for the next level is stored in the file `data.txt` in one of the few human-readable strings — but all letters have been **rotated by 13 positions**.  
This means the text is **ROT13-encoded** and needs to be decoded to reveal the password.

---

## 🔑 Credentials
- **Username:** bandit9  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit9@bandit.labs.overthewire.org -p 2220
   ````

2. Confirm the file exists and check its type:

   ```bash
   ls -l
   file data.txt
   ```

3. Display the file contents:

   ```bash
   cat data.txt
   ```

   You’ll see what looks like gibberish text — that’s ROT13-encoded.

4. Decode the ROT13 text using one of the following commands:

   * Using the built-in `tr` command:

     ```bash
     cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
     ```

     * `tr` — translates characters
     * `'A-Za-z'` — all letters
     * `'N-ZA-Mn-za-m'` — shifts letters by 13 positions

   * Alternatively, if you have `rot13` or `perl` installed (for practice):

     ```bash
     cat data.txt | perl -pe 'y/A-Za-z/N-ZA-Mn-za-m/'
     ```

5. The output of the command will reveal the **decoded password**.
   Copy it and use it to log in to the next level (`bandit10`).

---

## ✅ Example (concise one-liner)

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

## 💡 What I Learned

* Learned about **ROT13 encoding**, a simple substitution cipher that rotates letters by 13 positions in the alphabet.
* Practiced using the `tr` command for character translation and encoding transformations.
* Understood how data can appear unreadable until correctly decoded — a common concept in cybersecurity and CTF-style puzzles.
* This level reinforced text manipulation and decoding techniques useful for analyzing obfuscated data.

```
