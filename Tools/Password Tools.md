## Hydra
[[Hydra]]
```
hydra -l <username> -P /usr/share/wordlists/<wordlist> <ip> http-post-form
```

## John the ripper
```
john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt --format=Raw-SHA256
```

#### Crack simple hash
```
john -w=/usr/share/wordlists/rockyou.txt hash.txt
```

Show previosuly cracked passwords
```
john --show hashed_passwords.txt
```

#### Password protected zip
```
zip2john <file,zip> > hashes
```
Then use [[#Crack simple hash]]

### ssh2john
```
ssh2john encr_rsa > id_rsa.hash
```


