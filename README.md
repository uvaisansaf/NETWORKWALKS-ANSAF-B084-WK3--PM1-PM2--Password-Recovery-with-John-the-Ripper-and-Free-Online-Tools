<div align="center">

# 🔐 Password Recovery with John the Ripper & Free Online Tools

### Networkwalks Cybersecurity Internship — Week 3 (Batch B084)

![Status](https://img.shields.io/badge/status-completed-brightgreen)
![Platform](https://img.shields.io/badge/platform-Kali%20Linux-557C94?logo=kalilinux&logoColor=white)
![Tool](https://img.shields.io/badge/tool-John%20the%20Ripper-black?logo=hackthebox&logoColor=white)
![Phase](https://img.shields.io/badge/phase-Gaining%20Access-orange)
![License](https://img.shields.io/badge/use-educational%20only-red)

</div>

---

## 👤 Intern Details

| Field | Value |
|---|---|
| **Name** | Uvais Ansaf Ahameth |
| **Intern ID** | NW-084-3AW |
| **Batch** | B084 |
| **Modules** | W3-PM1 (John the Ripper) · W3-PM2 (Free Online Tools) |
| **Topic** | Password Recovery / Password Cracking |

---

## ⚠️ Disclaimer

> This repository documents a **learning exercise** from the Networkwalks Cybersecurity Internship.
> All passwords, hashes, and accounts used here were created by me on my own test machine.
> **No real account, system, or person was attacked.**
> Password cracking must only be performed on systems and data you own or have explicit written permission to test.

---

## 📦 Modules

- **W3-PM1** — Password Recovery with John the Ripper (offline, Kali Linux)
- **W3-PM2** — Password Recovery with Free Online Tools (MD5 generator + CrackStation)

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **John the Ripper** `1.9.0-jumbo-1` | Offline password cracker (Kali Linux) |
| **unshadow** | Merges `/etc/passwd` and `/etc/shadow` into one crackable file |
| **zip2john** | Extracts the password hash from a protected ZIP |
| **rockyou.txt** | Wordlist used for the dictionary attack |
| **MD5 online generator** | Generates a hash from a plaintext word |
| **CrackStation** | Reverses a hash back to its original word (online) |

---

## 🚀 What I Did

### W3-PM1 — John the Ripper

**1. Verify John the Ripper is installed**
```bash
john --help | head -5
```

**2. Create test users and extract password hashes**
```bash
sudo useradd -m nwtest1 ; sudo useradd -m nwtest2
sudo unshadow /etc/passwd /etc/shadow | sudo tee ~/nw_hashes.txt
```

**3. Crack the hashes with the rockyou wordlist**

Kali uses the modern `yescrypt` hash format, so `--format=crypt` is required:
```bash
john --format=crypt --wordlist=/usr/share/wordlists/rockyou.txt ~/nw_hashes.txt
```

**4. Show the cracked passwords**
```bash
john --show ~/nw_hashes.txt
```
✅ Recovered: `nwtest1 → password123` · `nwtest2 → iloveyou`

**5. (Extra) Crack a password-protected ZIP file**
```bash
zip --password letmein locked.zip secret.txt
zip2john locked.zip > ziphash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt ziphash.txt
```
✅ Recovered ZIP password: `letmein`

### W3-PM2 — Free Online Tools

1. Generated an MD5 hash of the word `sunshine` using an online MD5 generator →
   `0571749e2ac330a7455809c6b0e7af90`
2. Pasted the hash into **CrackStation** → recovered the original word: `sunshine`

This shows that short, common passwords offer little real protection even when hashed, since they already exist in public lookup tables.

---

## 📊 Results Summary

| Task | Result |
|---|---|
| Linux user `nwtest1` | `password123` ✅ recovered |
| Linux user `nwtest2` | `iloveyou` ✅ recovered |
| Locked ZIP file | `letmein` ✅ recovered |
| Online MD5 hash | `sunshine` ✅ recovered |

---

## 🧩 Problems Faced

| Problem | Solution |
|---|---|
| `john` said "No password hashes loaded" | Kali uses `yescrypt`, which John didn't auto-detect — added `--format=crypt` |
| Test password `summer2024` wasn't in the wordlist | Switched to a common word (`iloveyou`) that's in `rockyou.txt` |
| Pasting multiple `sudo` commands at once mixed up input | Ran the `sudo` step first, then the rest separately |

---

## 🛡️ Recommendations

- Use long passwords (12+ characters) mixing letters, numbers, and symbols
- Never reuse the same password across accounts
- Store passwords with a strong, slow, salted hash (e.g. `yescrypt`, `bcrypt`)
- Protect important files with strong passwords, not simple words
- Use a password manager to generate and store credentials

---

## 📁 Files

```
├── W3-PM-FINAL_Report_Uvais_Ansaf_Ahameth.pdf   # Full report with steps & screenshots
└── screenshots/                                  # Evidence images
```

---

<div align="center">

**Uvais Ansaf Ahameth** · NW-084-3AW · Week 3 · Networkwalks Cybersecurity Internship

</div>
