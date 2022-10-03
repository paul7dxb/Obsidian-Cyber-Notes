### Open file:
```
f = open("demofile.txt", "r")  
print(f.read())
```

### Sending and recieving to netcat
[[Libraries#Reading lines from connection|Using PwnTools]]

### Try catch except
```
try:  
  print(x)  
except NameError:  
  print("Variable x is not defined")  
except:  
  print("Something else went wrong")
```

### Index of element
```
pos = ALPHABET.index(c)
```

### Enumerate
```
>>> for count, value in enumerate(values):
...     print(count, value)
...
0 a
1 b
2 c
```

### Regex
[Cheat Sheet](https://cheatography.com/davechild/cheat-sheets/regular-expressions/)

[Python regex docs](https://docs.python.org/3/howto/regex.html)

`import re`

```
import re

#Perform regex for data (e.g stuff between the "'"s)
a = re.findall(r"(['])([\s\S]+)(['])",linesStr)

print(f'\n RE Result: \n {a[0][1]} \n')

toBytes = bytes(a[0][1], 'utf-8')
```

## Splat / unpack
Takes a tuple and unpacks the one tuple object into individual objects
```
#Get a tuple
(1,2)
#Unpack it with *
*(1,2)
#Gives
1 , 2
```