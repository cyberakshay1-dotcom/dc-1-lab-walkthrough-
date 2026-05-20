# dc-1-lab-walkthrough-

## 📌 Description
DC-1 is a beginner-friendly boot2root machine designed for penetration testing practice.  
The goal is to gain root access by exploiting vulnerabilities and performing privilege escalation.

---

# 🛠️ Tools Used

- Nmap
- Nikto
- Gobuster
- Burp Suite
- Linux Privilege Escalation Techniques

---

# 🔍 Step 1: Network Scanning

We first identify the target machine IP address.

```bash
netdiscover
```

Then perform a full Nmap scan.

```bash
nmap -sV -sC <TARGET-IP>
```

## Open Ports Found

- 22 → SSH
- 80 → HTTP

---

# 🌐 Step 2: Web Enumeration

Open the target website in the browser.

We discover the machine is running Drupal CMS.

Use Nikto for vulnerability scanning.

```bash
nikto -h http://<TARGET-IP>
```

Directory enumeration:

```bash
gobuster dir -u http://<TARGET-IP> -w /usr/share/wordlists/dirb/common.txt
```

---

# 💥 Step 3: Exploiting Drupal

Search for Drupal vulnerabilities using Searchsploit.

```bash
searchsploit drupal
```

Use Drupalgeddon exploit to gain access.

```bash
python exploit.py http://<TARGET-IP>
```

After exploitation, we obtain a shell.

---

# 🔑 Step 4: User Enumeration

Check system users and configuration files.

```bash
cat /etc/passwd
```

Look for sensitive files and credentials.

---

# 🚀 Step 5: Privilege Escalation

Check SUID binaries.

```bash
find / -perm -4000 2>/dev/null
```

Exploit misconfigured permissions to gain root access.

```bash
sudo -l
```

Finally obtain root shell.

```bash
whoami
```

Output:

```bash
root
```

---

# 🏁 Conclusion

Successfully completed the DC-1 machine by:
- Enumeration
- Exploitation
- Privilege Escalation

This lab helped improve practical penetration testing skills and Linux enumeration techniques.

---

# ⚠️ Disclaimer

This walkthrough is for educational purposes only.  
Practice only in legal lab environments like VulnHub or Hack The Box.
