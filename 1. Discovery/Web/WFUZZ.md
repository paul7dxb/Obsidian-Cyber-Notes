Basic user pass
```
wfuzz -c -z file,mywordlist.txt -d “username=FUZZ&password=FUZZ” -u http://shibes.thm/login.php
```

If usernames preceed a file
```
wfuzz -c -z file,/usr/share/wordlists/dirb/big.txt localhost:80/FUZZ/note.txt
```

Fuzz a range
```bash
wfuzz -z range,0-10 --hl 97 http://testphp.vulnweb.com/listproducts.php?cat=FUZZ
```

| option | desc |
| --- | --- |
| --hw x | hide x word count |
| -c | Shows the output in color |
| -d |Specify the parameters you want to fuzz with, where the data is encoded for a HTML form |
| -z | Specifies what will replace FUZZ in the request. For example `-z file,big.txt`. We're telling wfuzz to look for files by replacing "FUZZ" with the words within "big.txt" |
| --hc | Don't show certain http response codes. I.e. Don't show **404** responses that indicate the file _doesn't_ exist, or "**200**" to indicate the file _does_ exist |
| --hl | Don't show for a certain amount of lines in the response |
| --hh | Don't show for a certain amount of characters |
|-t N| Specify the number of concurrent connections (10 default)
|-s N| Specify time delay between requests (0 default)
