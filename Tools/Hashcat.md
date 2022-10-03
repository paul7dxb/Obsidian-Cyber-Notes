Hash codes:
https://hashcat.net/wiki/doku.php?id=example_hashes

| Hash mode | Hash name | example |
| --- | --- | --- |
| 0 | md5 | 8743b52063cd84097a65d1633f5c74f5 |
|1700 | sha2 512 | 82a9dda829eb7f8ffe9fbe49e45d47d2dad9664fbb7adf72492e3c81ebd3e29134d9bc12212bf83c6840f10e8246b9db54a4859b7ccd0123d86e5872c1e5082f |
| 1710 | sha512($pass.$salt) | e5c3ede3e49fb86592fb03f471c35ba13e8d89b8ab65142c9a8fdafb635fa2223c24e5558fd9313e8995019dcbec1fb584146b7bb12685c7765fc8c0d51379fd:6352283260 |

Cheat sheet
https://cheatsheet.haax.fr/passcracking-hashfiles/hashcat_cheatsheet/

Hash type:
-m

Attack mode:
-a
```
-a 0 # Straight : hash dict
-a 1 # Combination : hash dict dict
-a 3 # Bruteforce : hash mask
-a 6 # Hybrid wordlist + mask : hash dict mask
-a 7 # Hybrid mask + wordlist : hash mask dict
```

Crack SHA1 by using wordlist with 2 char at the end 
```
hashcat -m 100 -a 6 hashes.txt wordlist.txt ?a?a -o output.pot
```


Crack MD5 hashes using dictionnary and rules
```
hashcat -a 0 -m 0 example0.hash example.dict -r rules/best64.rules

hashcat -m 0 "2cb42f8734ea607eefed3b70af13bbd3" /usr/share/wordlists/rockyou.txt 
```