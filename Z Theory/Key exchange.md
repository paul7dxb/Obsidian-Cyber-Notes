### Diffie Helman Exchange
Public g, n
Private a and b

A | Public |     B
--- | --- | ---
a | g n | b
g^a mod n |  | g^b mod n
send to B | | send to A
(g^b)^a mod n| | (g^a)^b mod n
These are equal by [[#mod power proof]] |

#### Diffie Helman problems
MITM:
A | Sean |     B
--- | --- | ---
a | s | b
g^a mod n | g^s mod n | g^b mod n
send to S | Send to A/B | send to S
(g^s)^a mod n| | (g^s)^b mod n
Have two different keys with each one. Decrypt and Encrypt with other key at each step

Solution:
[[Z Theory/RSA]]


### Proof
#### mod power proof
(g^a)^b mod n = (g^b)^a mod n

lets say:
g^a = k*n+x
where x is an unknown number

because: (u + v) mod n =(u mod n + v mod n) mod n 
and because: k*n mod n = 0
we get:
(g^a) mod n = (k*n+x) mod n = x
<=> ((g^a) mod n)^b mod n = x^b mod n

i used the binomial theorem nCr to get:
(g^a)^b = (k*n+x)^b = (k*n)^b + (nC1)*(k*n)^(b-1)*x + ... + (nC(b-1))*( (k*n)^(1)*x^(b-1) + x^b

since n appears in every part except in x^b every other part is set to 0 when we take the modulo:
<=> (g^a)^b mod n = x^b mod n

so therefore (g^a)^b mod n = ((g^a) mod n)^b mod n