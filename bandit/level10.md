# Bandit Level 10 → Level 11

## 🧩 Goal
Recover the password for the next level from the file `data.txt`. The file contains encoded and/or compressed data — you must identify the format(s) and decode/unpack it to reveal the password.

---

## 🔑 Credentials
- **Username:** bandit10  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit10@bandit.labs.overthewire.org -p 2220
   ````

2. Inspect the file to get clues about its contents:

   ```bash
   ls -l data.txt
   file data.txt
   head -n 5 data.txt
   ```

3. Common patterns & tools to try (work through them until you find the right one):

   * **If it looks like printable encoded text (base64-like):**

     ```bash
     # try base64 decoding and save result to a file
     cat data.txt | base64 -d > decoded.bin
     file decoded.bin
     # if decoded.bin is text, view it:
     cat decoded.bin
     ```

   * **If `file` or `decoded.bin` shows a compressed archive (gzip, bzip2, tar, etc.):**

     ```bash
     # if gzip
     gunzip -c decoded.bin > decoded.txt         # or: zcat decoded.bin
     # if bzip2
     bunzip2 -c decoded.bin > decoded.txt        # or: bzcat decoded.bin
     # if tar.gz archive
     tar -tzf decoded.bin                        # list files
     tar -xzf decoded.bin                        # extract files
     ```

   * **If the file contains binary data with visible strings (password might be in plain text inside):**

     ```bash
     strings decoded.bin | less
     # or search for likely patterns (e.g., lines with many alphanumeric chars)
     strings decoded.bin | grep -E '[A-Za-z0-9]{20,}'
     ```

   * **If it’s uuencoded:**

     ```bash
     # try uudecode (writes file in current directory)
     uudecode data.txt
     ```

   * **If it’s hex or otherwise hexdumped:**

     ```bash
     # try xxd reverse
     xxd -r -p data.txt > decoded.bin
     file decoded.bin
     ```

   * **If unsure, try a pipeline that guesses common encodings:**

     ```bash
     # base64 decode, then try to gunzip (safe to run; if not gzip, output will remain)
     cat data.txt | base64 -d 2>/dev/null | gunzip -c 2>/dev/null > try.txt || true
     file try.txt || true
     head -n 20 try.txt
     ```

4. Once you decode/unpack successfully, read the resulting file that contains the password (it will usually be a short alphanumeric string). Example:

   ```bash
   cat decoded.txt
   # or if extraction created a file like password.txt
   cat password.txt
   ```

---

## ✅ Example (typical one-liner flow)

A common successful sequence (base64 → gzip) can look like:

```bash
cat data.txt | base64 -d > decoded.bin
file decoded.bin
# if file reports gzip compressed data:
gunzip -c decoded.bin > password.txt
cat password.txt
```

(If the file requires a different combination — e.g., base64 then tar extraction, or plain gzip, or hex → binary — the same approach of `file`, then the appropriate unpack/convert tool will work.)

---

## 💡 What I Learned

* How to **identify file formats** using `file`, `head`, and quick inspection.
* How to **decode common encodings** such as Base64 (`base64 -d`), uuencode/uudecode, and hex (`xxd -r -p`).
* How to **handle compressed archives** (`gunzip`, `bunzip2`, `tar`) after decoding.
* How to use `strings` to pull readable text out of binary blobs.
* This level reinforced a practical workflow: **inspect → decode → unpack → read** — a repeatable method for recovering hidden content in various CTF tasks and real-world forensics.

```
