Used in TLS, IKE
Helps prevent MITM for Diffie-Helman
	[[Key exchange#Diffie Helman Exchange|Diffie Helman Exchange]]


### Theory
A | Public |     B
--- | --- | ---
a | g, key pub | k pri
Sends ga |  | Sends gb & hashed(gb) from k priv
use k pub to verify gb | |

### Creating key
- n = p . q    (p and q distinct random primes)
- [Carmichael's totient function](https://en.wikipedia.org/wiki/Carmichael%27s_totient_function "Carmichael's totient function") of the product as _λ_(_n_)
	- λ(n) =  Lowest Common Multiple (_p_ − 1, _q_ − 1)
- Choose e
	- 1 < e < λ(n) AND e is coprime to λ(n) (Highest common divisor 1)
- Calculate d
	- d = modular mutiplicative inverse of e (mod λ(n))
		- e . d ≡ 1 (mod _φ_(_n_))
		- (can use extended Euclidean algorithm to calculate)
		- `from Crypto.Util.number import inverse`
		- `d = inverse(e,phi)`
- Euler totient φ(n) 
	- φ(n) = (p-1)(q-1)

### Keys
- Public key (n, e)
	- cipher of message c(m):
	- c(m) = c^e mod n
- Private key (n, d)
	- m(c) = c^d mod n
- Encrypt
	- cipher message (c) message (m)
	- c = m^e mod n
	- m = c^d mod n

### Vulnerabilities
- Is not [semantically secure](https://en.wikipedia.org/wiki/Semantically_secure "Semantically secure") 
- 
#### Low e & m
- low e (3) and small m (m < n ^(1/e))
	- m^e < n
	- Take the eth root of the ciphertext (integers)

#### Multiple receivers so clear text
- Same clear text to e or more recipients
- receivers same e
- p,q,n different
- Coppersmith's attack

#### Insecure if not padded
[Stack OVerflow Explanation](https://crypto.stackexchange.com/questions/1448/definition-of-textbook-rsa)
- It is malleable. I.e., if you give me a ciphertext c which encrypts m, I can compute c′≡c⋅2emodn. When the owner of the private key decrypts c′, she will get 2mmodn. In other words, I can make predictable changes to ciphertexts.