# Bandit Level 13 → Level 14

## 🧩 Goal
Retrieve the private SSH key provided in the home directory, use it to log in as `bandit14` (the next level), and then read `/etc/bandit_pass/bandit14` to get the password for that level. :contentReference[oaicite:0]{index=0}

---

## 🔑 Credentials
- **Username:** bandit13  
- **Password:** [password from previous level]  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit13@bandit.labs.overthewire.org -p 2220
   ````

2. List the files in the home directory. You should see a private key file (commonly named `sshkey.private`):

   ```bash
   ls -l
   # expected output includes: sshkey.private
   ```

   Confirm the file is present and inspect it (do not print private key to public places):

   ```bash
   file sshkey.private
   head -n 5 sshkey.private
   ```

   (The file is your SSH private key — you will use it to authenticate as `bandit14`.) ([MayADevBe Blog][1])

3. Fix the key file permissions locally or on the remote host so SSH will accept it. From the `bandit13` shell:

   ```bash
   chmod 600 sshkey.private
   ```

   (SSH requires private keys to be readable only by the owner; if permissions are too open, SSH will refuse to use the key.) ([MayADevBe Blog][1])

4. Use the private key to SSH into the next level. You can connect **from the remote host** (recommended) using `localhost`:

   ```bash
   ssh -i sshkey.private -p 2220 bandit14@localhost
   ```

   Or, if you prefer to transfer the key to your local machine first, do that safely (from *your* machine):

   ```bash
   # copy the key from remote to local machine (replace <localpath> with where you want it)
   scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private <localpath>/sshkey.private

   # on your local machine, restrict permissions and use the key
   chmod 600 <localpath>/sshkey.private
   ssh -i <localpath>/sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
   ```

   Note: if you scp the key to your local machine, keep it secure and delete it when finished. ([Medium][2])

5. Once logged in as `bandit14`, read the password file:

   ```bash
   cat /etc/bandit_pass/bandit14
   ```

   The printed string is the password for `bandit14`. Use it to SSH into `bandit14` from your normal workflow if needed.

---

## ✅ Concise solution (typical)

From the `bandit13` session:

```bash
chmod 600 sshkey.private
ssh -i sshkey.private -p 2220 bandit14@localhost
# then on bandit14:
cat /etc/bandit_pass/bandit14
```

---

## 💡 What I Learned

* This level introduced **public-key SSH authentication**: instead of a password you use a private key that matches a public key on the remote host. ([MayADevBe Blog][1])
* Private key **file permissions matter** — SSH refuses to use keys that are group/world-readable. Use `chmod 600` (or `700` on some walkthroughs) to secure the key before using it. ([MayADevBe Blog][1])
* How to **safely transfer keys** with `scp`, and the importance of deleting sensitive keys from local machines after use. ([Medium][2])

```
