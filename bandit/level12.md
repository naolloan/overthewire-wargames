# Bandit Level 12 → Level 13

## 🧩 Goal
The password for the next level is stored in the file `data.txt`. That file is a **hexdump** (hex representation) of a file that has been **repeatedly compressed**. Your task is to reconstruct the original binary from the hexdump, then iteratively detect and decompress/unpack until you reveal the password. :contentReference[oaicite:0]{index=0}

---

## 🔑 Credentials
- **Username:** bandit12  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps (copy-ready)

1. Create a working directory under `/tmp` and copy the file there (keeps your home clean):
   ```bash
   mkdir /tmp/bandit12-work
   cp data.txt /tmp/bandit12-work/
   cd /tmp/bandit12-work
   ````

2. Convert the hexdump back to a binary. `xxd -r -p` reverses a plain hexdump to raw bytes:

   ```bash
   xxd -r -p data.txt > data
   ```

3. Inspect the produced file to see what it is:

   ```bash
   file data
   ```

4. Repeatedly identify the file type and handle it accordingly. Typical sequence of actions (run these step-by-step and repeat until `file` reports plain text or you can `cat` a password file):

   * If `file` reports **gzip compressed data**:

     ```bash
     mv data data.gz
     gunzip data.gz            # produces `data` again (decompressed)
     file data
     ```

   * If `file` reports **bzip2 compressed data**:

     ```bash
     mv data data.bz2
     bunzip2 data.bz2
     file data
     ```

   * If `file` reports a **tar archive**:

     ```bash
     mv data data.tar
     tar -xvf data.tar
     # explore extracted files (they may be named like data2.bin, data3.bin, etc.)
     ```

   * If `file` reports another **heavily nested archive** (tar inside gzip inside bzip2 etc.), repeat the `file` → rename → appropriate unpack step until you get plain text.

5. Useful helpers while iterating:

   ```bash
   # show first few bytes / magic bytes
   hexdump -C data | head

   # show printable strings inside a binary (quick check)
   strings data | head -n 50
   ```

6. Eventually you will extract a plain text file (or a file that `file` reports as ASCII text). Display it to reveal the password:

   ```bash
   cat extracted-file.txt
   # or if the final file is named data.txt again:
   cat data
   ```

---

## ✅ One example condensed flow

(Depending on how many layers there are you may need to repeat steps — this example shows a common base64/hex → gzip → bzip2 → tar pattern)

```bash
xxd -r -p data.txt > data
file data
# if gzip:
mv data data.gz; gunzip data.gz
file data
# if bzip2:
mv data data.bz2; bunzip2 data.bz2
file data
# if tar:
mv data data.tar; tar -xvf data.tar
# repeat until you reach a text file
```

This iterative approach is documented in community walkthroughs for this level. ([Gist][1])

---

## 💡 What I Learned

* How to **reverse a hex dump** with `xxd -r -p` and why hexdumps are used to represent binary data as text. ([OverTheWire][2])
* A repeatable workflow: **inspect (`file`) → convert/unpack (`xxd`, `gunzip`, `bunzip2`, `tar`) → inspect again** until you reach readable output. ([Gist][1])
* Using `strings`, `hexdump`, and `file` to gain quick insight into unknown binaries is invaluable in CTFs and forensic work.

---
