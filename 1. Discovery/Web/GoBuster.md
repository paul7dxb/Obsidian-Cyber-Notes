
```
gobuster dir -u http:<IP>:<PORT> -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x php,sh,txt,cgi,html,js,css -t 100

```
```
gobuster dir -u http://<ip>:3333 -w <word list location>

gobuster dir -u http://$TGT:3333 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt 
```

-e : print full URL's
-U: username
-P: password
`-p <x>`: proxy to use
`-c <http cookies>`:	Specify a cookie for simulating your auth
-t: threads

### Error non existing URL's
Occurs when bad URL's get redirected to an actual page
Can change command to positive esponse to different codes
```
gobuster dir -u $URL -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -s "204,301,302,307,401,403"
```

## File types
```
-x php,txt,html,cms
```

## Worldlists
[[Wordlists#Web Wordlists]]

```
/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt 
```