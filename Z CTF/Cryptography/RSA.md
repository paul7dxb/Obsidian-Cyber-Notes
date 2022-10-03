Theory:
	[[Z Theory/RSA|RSA Theory]]

Tools
[[CTF Tools#RSACtfTool|RsaCTTool]]

### Factorising n = p.q
[Online Factorisation](https://www.alpertron.com.ar/ECM.HTM)
Brute force find p,q:
```
n = 4966306421059967
# // is floor division
[(d, n//d) for d in range(1, int(sqrt(n))+1, 2) if n % d == 0]
```

### Decrypting
```
from Crypto.Util.number import inverse

n = 
e = 

c = 

#factorise n to get p and q
p = 
q = 

phi = (p-1)*(q-1)
d = inverse(e,phi)

#m = c^d mod n
m = pow(c,d,n)
hexM = hex(m)
unHex = bytes.fromhex(hexM[2:]).decode('utf-8')
print(unHex)

```

### Weiner attack on RSA
Useful when d is small
```
python3 -m pip install owiener
```

```
import owiener

e = <Value for e>
n = <Value for n>
d = owiener.attack(e, n)

if d is None:
    print("Failed")
else:
    print("Hacked d={}".format(d))
```

## low m, e value
[[Z Theory/RSA#Low e m|Theory]]
```
import gmpy2

n = <value for n>
e = 3
c = <value for c>

for i in range(10000):
    m, is_true_root = gmpy2.iroot(i*n + c, e)
    if is_true_root:
        print(f"Found i = {i}")
        print("Message: {}".format(bytearray.fromhex(format(m, 'x')).decode()))
        break
```

For multiple ciphers:
[Multiple low m,low e](https://www.programcreek.com/python/example/98527/gmpy2.iroot)


## Pollard p-1
Imports:
```
python3 -m pip install primefac
```
```
from Crypto.Util.number import *
import gmpy2
import primefac

n = "nHexValue"
c = "cInHex"
n = int(n,16)

#Common e about 65000.This is most common 65537 
e = 0x10001
q = primefac.pollard_pm1(n)
p = n//q
phi = (p-1)*(q-1)
d = inverse(e,phi)

print(f'p: {p}')
print(f'q: {q}')

#16 used from smoothness
print(long_to_bytes(pow(int(c,16),d,n)))
```

### Decryption wont do m
Use c^d mod(n) == (c+n)^d mod(n) (By binomial expansion)

### No padding
[[Z Theory/RSA#Insecure if not padded|Theory]]

```
n = 
e = 65537
c = 

cPrime = c * (pow(2,e,n))
x = pow(2, e, n)

#Send cPrime to RSA and input returned value
print(f'cprime:\n {cPrime}')
returned = input('give number: ')
#returned = 

#Send cPrime will give 2m mod n
#Try reverse by brute force
# (2m , 2m + n , 2m + 2n, 2m + 3n)
# take away i * n starting 0 then divide by 2

error = 0
i = 0
while True:
	if i % 10000 == 0:
		print(f'i = {i}')
	twoM = returned - i*n
	m = twoM//2


	hexM = hex(m)
	#print(f'hexm: {hexM} :end')

	#Try to unhex
	try:
		unHex = bytes.fromhex(hexM[2:]).decode('utf-8')
		pass
		print(f'Result at i = {i}\nunhex: {unHex}')
	except Exception as e:
		#print("error")
		error +=1

	#Increment i
	i += 1
```