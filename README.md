# Bandit OverTheWire – Learning Journey

![OverTheWire Logo](https://overthewire.org/wargames/bandit/bandit.png)

This repository documents my **step-by-step journey through the Bandit wargame** on [OverTheWire](https://overthewire.org/wargames/bandit/).  

For each Bandit level, I created a separate Markdown file detailing:

- The **goal of the level**  
- **Credentials** needed to log in  
- **Commands and steps** I used to solve the level  
- **Learnings and insights** gained from the challenge  

The repository is organized in a **professional and structured way**, making it easy to follow and useful for others learning Linux, cybersecurity, or command-line skills.

---

## Repository Structure

```

bandit/
├── level00.md   # Login via SSH and basics
├── level01.md   # Basic file reading
├── level02.md   # Filenames with spaces
├── level03.md   # Hidden files
├── level04.md   # File types
├── level05.md   # Human-readable files in a directory
├── level06.md   # File ownership
├── level07.md   # Searching text in files
├── level08.md   # Unique lines in a file
├── level09.md   # ROT13 encoded text
├── level10.md   # Decoding/compressed data
├── level11.md   # ROT13 again
├── level12.md   # Hexdump and iterative decompression
├── level13.md   # SSH private key usage
├── level14.md   # Base64 decoding
├── level15.md   # …and so on
└── README.md    # This file

```

---

## How I Documented Each Level

Each `levelXX.md` file follows the same **professional format**:

1. **Goal:** What the level requires.  
2. **Credentials:** Username, password, host, port.  
3. **Steps:** Commands and reasoning to solve the level.  
4. **Solution:** Concise command-line workflow.  
5. **What I Learned:** Key takeaways, Linux commands, and cybersecurity concepts.

---

## Learning Outcomes

Through Bandit, I gained hands-on experience with:

- **Linux command line** (file manipulation, navigation, permissions, text processing)  
- **SSH and authentication** (password and key-based login)  
- **Text processing tools**: `grep`, `awk`, `sed`, `tr`, `sort`, `uniq`, `strings`  
- **File identification and decoding**: `file`, `xxd`, `base64`, `gunzip`, `bunzip2`, `tar`  
- **Problem-solving workflow**: inspect → identify → act → verify  

This structured approach reinforces skills that are essential for cybersecurity, system administration, and CTF challenges.

---

## Notes

- This repository is intended for **educational purposes only**.  
- Do **not use the solutions outside of OverTheWire Bandit** — always practice ethical hacking principles.  
- Commands shown may reveal passwords; handle them responsibly.  

---

## References

- [OverTheWire Bandit Wargame](https://overthewire.org/wargames/bandit/)  
- Linux documentation (`man` pages, online guides)  
- Community discussions for learning and tips  

---

## Next Steps

I plan to:

- Complete all remaining Bandit levels  
- Continue documenting with the same structured format  
- Explore other OverTheWire wargames (Narnia, Leviathan) for additional learning
```
