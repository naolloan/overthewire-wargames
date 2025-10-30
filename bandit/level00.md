# Bandit Level 0 → Level 1

## 🧩 Goal
Learn how to connect to a remote server using SSH.

---

## 🔑 Credentials
- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220  
- **Username:** bandit0  
- **Password:** bandit0

---

## 💻 Steps
1. Open your terminal.  
2. Connect using SSH:
   ```bash
   ssh bandit0@bandit.labs.overthewire.org -p 2220

---

3. Once connected, you’re inside the Bandit Level 0 environment.

---

## ✅ Solution

The next level’s password is stored in a file called `readme`:

```bash
cat readme
```

Copy the password and use it to log in to the next level (`bandit1`).

---

## 💡 What I Learned

In this level, I learned how to **log in to remote devices using SSH (Secure Shell)**.
Before attempting this challenge, I didn’t fully understand what SSH was, so I took some time to research it.
I learned that SSH is a **secure protocol for connecting to remote servers** over a network, allowing encrypted communication and command execution.

Thanks to this level, I now understand the basic syntax of the `ssh` command and how it works.
I successfully logged into the **OverTheWire Bandit server** from my own device using SSH — which felt like my first real step into the world of cybersecurity and Linux system access.
