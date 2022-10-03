Python Http server:
[[Web Hosting#Python HTTP|Python HTTP Server]]

Read in file
```
f = open("message", "r")  
messageString = f.read()
```
Write to file:
### Python data conversions
Char <--> ASCII
```
ord('a')
> 97

chr(97)
> 'a'
```

to Hex:
```
hexText = hex(text)
```

From Hex to Ascii
```
hexText = 

unhex = nHex = bytes.fromhex(hexText[2:]).decode('utf-8')
print(unhex)

import binascii
binascii.unhexlify(hexText[2:])
```