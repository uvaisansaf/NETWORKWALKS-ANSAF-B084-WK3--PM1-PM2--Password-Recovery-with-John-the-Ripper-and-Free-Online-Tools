# Networkwalks Cybersecurity Internship - Week 3 (B084)

**Name:** Uvais Ansaf Ahameth
**Intern ID:** NW-084-3AW
**Topic:** Password Recovery / Password Cracking

## Modules
- **W3-PM1:** Password Recovery with John the Ripper (Kali Linux)
- **W3-PM2:** Password Recovery with Free Online Tools

## What I did
- Verified John the Ripper (v1.9.0-jumbo-1) in Kali Linux
- Created test users and extracted their password hashes using `unshadow`
- Cracked the hashes with the `rockyou` wordlist → `password123`, `iloveyou`
- Cracked a password-protected ZIP file using `zip2john` → `letmein`
- Generated an MD5 hash online and recovered it with CrackStation → `sunshine`

## Tools
John the Ripper, unshadow, zip2john, rockyou wordlist, MD5 online generator, CrackStation.

## Files
- `W3-PM-FINAL_Report_Uvais_Ansaf_Ahameth.pdf` - full report with steps and screenshots
- `screenshots/` - evidence images

## Note
Done for learning purposes only. All passwords and hashes were created on my own test machine. Password cracking must only be used on systems you own or have permission to test.
