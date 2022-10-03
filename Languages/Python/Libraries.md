### Beautiful Soup
Web content 
https://www.crummy.com/software/BeautifulSoup/bs4/doc/

BeautifulSoup cheat sheet:
http://akul.me/blog/2016/beautifulsoup-cheatsheet/

```
python -m pip install beautifulsoup4
```

Setup:

```
import requests
from bs4 import BeautifulSoup

URL = "https://realpython.github.io/fake-jobs/"
page = requests.get(URL)

soup = BeautifulSoup(page.content, "html.parser")
```

This creates a "BeautifulSoup" Object

Find by ID:
```
results = soup.find(id="ResultsContainer")
```
Fing multiple by tag type:
	Cannot prettify unless you loop through and prettify each result
```
results = soup.find_all("div")
```

If finding by class use `class_`

Printing:
```
print(results.prettify())
```

# Cryptography
Long to bytes:
Library install
```
python3 -m pip install pycryptodome
```
```
from Crypto.Util.number import long_to_bytes
text = long_to_bytes(m_c)
```

# gmpy2
gmpy2 is an optimized, C-coded Python extension module that supports fast multiple-precision arithmetic.
```
python3 -m pip install gmpy2
```
```
import gmpy2
```

# PwnTools
[Documentation](https://docs.pwntools.com/en/stable/)

```
python3 -m pip install --upgrade pwntools
```

## Pwn
### Reading lines from connection
```
r = remote('saturn.picoctf.net', 63116)

lines = r.recvuntil('Answer:')
print("done")
print(lines)
#Recieves bytes. Decode to Ascii
linesStr = lines.decode("utf-8")

#Perform regex for data (e.g stuff between the "'"s)
a = re.findall(r"(['])([\s\S]+)(['])",linesStr)
print(f'\nRE Result:\n{a[0][1]}\n')
toBytes = bytes(a[0][1], 'utf-8')

result = hashlib.md5(toBytes).hexdigest()
print(f'md5 result: {result}')

r.sendline('{}'.format(result))
```

```
r = remote('jupiter.challenges.picoctf.org', 58617)

#Get lines until known end
lines = r.recvuntil('IS THIS POSSIBLE and FEASIBLE? (Y/N):')

#Grab variables from lines
q = int([l for l in lines.split('\n') if 'q :' in l][0].split(':')[1].strip(), 10)
p = int([l for l in lines.split('\n') if 'p :' in l][0].split(':')[1].strip(), 10)
ans = p * q

#Send and receive data including answer
r.sendline('Y')
print(r.recvuntil('n:'))
print( 'Sending: {}'.format(ans))
r.sendline('{}'.format(ans))


```

### Numpy np
```
import numpy as np
```

Stack columns
```
a = np.array((1,2,3))
b = np.array((2,3,4))

np.column_stack((a,b))
array([[1, 2],
       [2, 3],
       [3, 4]])
```