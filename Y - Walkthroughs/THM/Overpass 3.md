**nmap**
sudo nmap -sV $TGT
	PORT   STATE SERVICE VERSION
	21/tcp open  ftp     vsftpd 3.0.3
	22/tcp open  ssh     OpenSSH 8.0 (protocol 2.0)
	80/tcp open  http    Apache httpd 2.4.37 ((centos))
	Service Info: OS: Unix

# Version vulnerabilities
vsftpd: Vulnerabilities for before 3.0.3

# Website
**Directory Discovery**
	random URL gives not found page so will try gobuster
	gobuster dir -u http://$TGT -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt 
	Breaks VM after a small amount of tests
	Found backup.zip at /backups containging CustomerDetails.xlsx.gpg

**Main page**
	Paradox: desginer
	Elf: Intern
	MuirlandOracle: HTTPS and netwroking
	NinjaJc01: Jame

# Backup.zip
**Extracting**
```
unzip backup.zip
```
Gives two files (gpg and priv.key)
```
gpg --import priv.key  
gpg --output customerdataDecrypted --decrypt Customerdetails.xlsx.gpg 
```
Gives customer details
Customer Name|	Username|	Password|	Credit card number	|CVC
---|---|---|---|---
Par. A. Doxx|	paradox|	ShibesAreGreat123|	4111 1111 4555 1142	|432
0day Montgomery|	0day|	OllieIsTheBestDog|	5555 3412 4444 1115|	642
Muir Land|	muirlandoracle|	A11D0gsAreAw3s0me|	5103 2219 1119 9245|	737


# FTP
