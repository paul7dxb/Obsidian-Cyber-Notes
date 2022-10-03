rot13
```
cat chars.txt > tr 
```

Remove new lines or white spaces
```
tr -d "\n"
tr -d ' '
```
Remove multiple chars (e.g >< space and new line):
```
tr -d '>< \n'
```

Change spaces to new lines:
```
tr " "  "\n"
```

rot 13
```
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```