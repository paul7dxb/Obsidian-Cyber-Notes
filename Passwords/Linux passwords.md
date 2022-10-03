### Unshadow

```
cat /etc/shadow > shadow.txt
cat /etc/passwd > password.txt

unshadow shadow.txt password.txt > hashes.txt

john --wordlist <WL> hashes.txt
```

### 
