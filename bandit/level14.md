# Bandit Level 14 → Level 15

## 🧩 Goal
Submit the password of the current level to a service listening on **localhost port 30000**. The service will return the password for the next level.

---

## 🔑 Credentials
- **Username:** bandit14  
- **Password:** (password from previous level / the one you used to login to bandit14)  
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220 (SSH)

---

## 💻 Steps
1. SSH into the level:
   ```bash
   ssh bandit14@bandit.labs.overthewire.org -p 2220
   ````

2. Once logged in, send your current password to **localhost:30000**. Replace `CURRENT_PASSWORD` with the password you used to get into bandit14. Use one of these safe methods:

   * Using `nc` (netcat):

     ```bash
     # prints the response (the next password)
     echo -n 'CURRENT_PASSWORD' | nc localhost 30000
     ```

   * Using `printf` (avoids adding a newline if that's required):

     ```bash
     printf '%s' 'CURRENT_PASSWORD' | nc localhost 30000
     ```

   * If your system's `nc` supports `-q` to quit after sending:

     ```bash
     printf '%s\n' 'CURRENT_PASSWORD' | nc -q 1 localhost 30000
     ```

   * Using bash /dev/tcp (if available):

     ```bash
     printf '%s' 'CURRENT_PASSWORD' > /dev/tcp/localhost/30000
     # to capture response to a variable:
     exec 3<>/dev/tcp/localhost/30000
     printf '%s' 'CURRENT_PASSWORD' >&3
     cat <&3
     exec 3>&-  # close
     ```

   * If `telnet` is available (interactive):

     ```bash
     telnet localhost 30000
     # then paste the password and press Enter
     ```

   Note: If the service expects a newline-terminated string, include `\n` (e.g., `printf '%s\n' 'CURRENT_PASSWORD' | nc ...`).

3. The service will reply with the **password for bandit15**. Copy that response.

4. Use the returned password to SSH into the next level:

   ```bash
   ssh bandit15@bandit.labs.overthewire.org -p 2220
   ```

---

## ✅ Example one-liner (typical)

```bash
echo -n 'CURRENT_PASSWORD' | nc localhost 30000
```

Replace `CURRENT_PASSWORD` with the password for `bandit14`. The output is the password for `bandit15`.

---

## 💡 What I Learned

* How to interact with **local network services** (TCP) from the shell using `nc`, `telnet`, or `/dev/tcp`.
* How to safely send a secret string over a TCP connection from a shell and capture the response.
* Using `printf` instead of `echo` can avoid unintended newlines or interpretation differences across shells.
* Small network services on localhost are common in CTFs — knowing how to send and receive raw TCP data is a useful skill for protocols and forensics.

---

Want me to also update the `bandit/README.md` progress table to reflect that Level 14 is complete (or whatever current status you want)?
::contentReference[oaicite:0]{index=0}
```
