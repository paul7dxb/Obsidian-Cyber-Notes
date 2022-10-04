# 0. Setup

# 1. Recon & Enumration
## 1.1 nmap

```bash
sudo nmap -A -T4 $TGT -p- -oN nmapOutput.nmap
```

Options explained: -A runs version detection& default scripts, -T4 is the timing template to use (0: slowest, 5: quickest), $TGT is the target IP variable I have set, -p- scan all ports, -oN is used to output the nmap scan results to a file.

**nmap results:**

IMAGE NMAP

Points of interest from nmap results:
- Port 80 open hosting [Werkzeug](https://pypi.org/project/Werkzeug/)

## 1.2 View Website

We can navigate to the website in browser using the target IP `http://<TGTIP>`
IMAGE WEBSITE BLANK

From here I generally browse the website as a user would do (alongside viewing page sources) to get an idea of the websites functionality and purpose before using enumeration tools.

# 2. Exploitation

# 3. Post Compromise Enumeration

# 4. Privilege Escalation
