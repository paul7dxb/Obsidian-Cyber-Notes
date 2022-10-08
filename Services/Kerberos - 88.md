[Kerberos Theory](../Windows/Active%20Directory%20Theory.md#Kerberos)

## Kerbrute

[Download link version 386](https://github.com/ropnop/kerbrute/releases)

Available Commands:
  bruteforce    Bruteforce username:password combos, from a file or stdin
  bruteuser     Bruteforce a single user's password from a wordlist
  help          Help about any command
  passwordspray Test a single password against a list of users
  userenum      Enumerate valid domain usernames via Kerberos
  version       Display version info and quit

### User Enumeration
```bash
sudo nano /etc/hosts # Add IP to etc hosts

./kerbrute_linux_386 userenum -d spookysec.local --dc spookysec.local usernames.txt 
```

Flags:
--dc string   The location of the Domain Controller (KDC) to target. If blank, will lookup via DNS
--delay int       Delay in millisecond between each attempt. Will always use single thread if set
-d, --domain string   The full domain to use (e.g. contoso.com)
-h, --help       help for kerbrute
-o, --output string   File to write logs to. Optional.
--safe      Safe mode. Will abort if any user comes back as locked out. Default: FALSE
-t, --threads int     Threads to use (default 10)
-v, --verbose         Log failures and errors
