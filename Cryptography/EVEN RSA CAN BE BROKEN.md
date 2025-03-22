# EVEN RSA CAN BE BROKEN???

This requires us to crack an RSA cipher. It gave us `N` and `e` along with the ciphertext.

We need to factor `N` to find `p` and `q`, which are necessary to derive the `d` private key. After factoring out `N`, we use `p` and `q` to find `phi(n)`, which is then used to derive `d`. With `d`, we can use it to decrypt the ciphertext.

```py
from sympy import factorint
from Crypto.Util.number import inverse, long_to_bytes

N = 16799813059474040683521193677604008137662933246608574497020627035385766086643037497044518435908962498627523416087485663437313731846828723869555831257812058
e = 65537
ciphertext = 644912162177182712751395078689059284647199680614972391207230117200642554428903113734876273092725396597616428315657339723215316859750482944673415462938023

p, q = list(factorint(N))
phi_n = (p - 1) * (q - 1)
d = inverse(e, phi_n)
plaintext = pow(ciphertext, d, N)
plaintext = long_to_bytes(plaintext)

print(plaintext)
```
