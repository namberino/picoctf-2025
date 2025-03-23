# Quantum Scrambler

This requires us to unscramble an array of bytes to derive the flag. Below is the scramble function:

```python
def scramble(L):
  A = L
  i = 2
  while (i < len(A)):
    A[i-2] += A.pop(i-1)
    A[i-1].append(A[:i-2])
    i += 1
    
  return L
```

It takes in an array of byte-strings and return an array of byte-strings. Each subarray in this `L` array contains 2 byte-strings. What this does is taking the subarray 2 indices behind the current subarray and append it to the middle of the current subarray. We can observe this effect in the first 4 subarrays:

```python
[['0x70', '0x69'], ['0x63', [], '0x6f'], ['0x43', [['0x70', '0x69']], '0x54'], ['0x46', [['0x70', '0x69'], ['0x63', [], '0x6f']], '0x7b']]
```

So all we need to do is identify the byte-strings within each subarrays and only grab those into a separate array for decoding.

```python
plaintext = []

for c in cipher:
    for b in c:
        if (isinstance(b, str)):
            plaintext.append(b)

for b in plaintext:
    dec_val = int(b, 16)
    ch = chr(dec_val)
    print(ch, end='')
```
