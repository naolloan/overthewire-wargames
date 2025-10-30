# Bandit Level 14 → Level 15

## 🧩 Goal
The password for the next level is stored in the file `data.txt`. This file contains **base64-encoded data**. Your task is to decode it to retrieve the password for `bandit15`.

---

## 🔑 Credentials
- **Username:** bandit14  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit14@bandit.labs.overthewire.org -p 2220
   ````

2. Confirm the presence of the file and check its type:

   ```bash
   ls -l
   file data.txt
   head -n 5 data.txt
   ```

   You’ll see that it is a text file containing characters typical of Base64 encoding (letters, digits, `+`, `/`, and `=` padding).

3. Decode the Base64-encoded content:

   ```bash
   base64 -d data.txt > password.txt
   ```

4. Display the decoded password:

   ```bash
   cat password.txt
   ```

   The output is the password for `bandit15`.

---

## ✅ One-liner alternative

You can decode and display in one command without creating an intermediate file:

```bash
base64 -d data.txt
```

---

## 💡 What I Learned

* How to **identify Base64-encoded data** — usually text with A-Z, a-z, 0-9, `+`, `/`, and `=` padding.
* How to **decode Base64 in Linux** using the `base64 -d` command.
* Base64 is a common encoding used to safely transmit binary data in text form, which is useful in emails, data serialization, and CTF challenges.
* This level reinforced pattern recognition: spotting encoded data, then applying the appropriate decoding tool.

```
