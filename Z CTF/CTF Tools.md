https://int0x33.medium.com/day-18-essential-ctf-tools-1f9af1552214

### Factorisation tool
[Factorisation Tool](https://www.alpertron.com.ar/ECM.HTM)

### RSA
#### RSACtfTool
[Github docs link](https://github.com/Ganapati/RsaCtfTool)

```
git clone https://github.com/Ganapati/RsaCtfTool.git
```

Show help
```
python RsaCtfTool.py
```

Print private key
```
./RsaCtfTool.py --publickey ./key.pub --private
```

Private key and uncipherfile
```
python ../../MyPrograms/RsaCtfTool/RsaCtfTool.py --publickey pubkey.pem --uncipherfile flag.txt.aes 
```

Specify attack with `--attack`
```
python ../../MyPrograms/RsaCtfTool/RsaCtfTool.py --publickey pubkey.pem --uncipherfile flag.txt.aes --attack wiener
```

Display private key
```
python ../../MyPrograms/RsaCtfTool/RsaCtfTool.py --publickey pubkey.pem --uncipherfile flag.txt.aes --private
```

Specify values
```
python ../MyPrograms/RsaCtfTool/RsaCtfTool.py -n <NValue> -e 3 --uncipherfile message.txt
```