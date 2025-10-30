
# Custom Encryption

## Solution
Read the program and created a python script for decryption
```
cipher = [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470, 936110, 10885, 674870, 261240, 293895, 65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045]

p = 97
g = 31
a = 88
b = 26

def make_value(base, exp, mod):
    return pow(base, exp, mod)

temp_val = make_value(g, b, p)
secret_key = make_value(temp_val, a, p)

decoded_chars = []
message = ""

for num in cipher:
    decoded_chars.append(chr(num // (311 * secret_key)))

for idx, ch in enumerate(decoded_chars):
    mask = "trudeau"[idx % 7]
    message += chr(ord(ch) ^ ord(mask))

print(message[::-1])
```





## Flag
```
picoCTF{custom_d2cr0pt6d_019c831c}
```

# Concepts Learnt
XOR encryption/decryption




# Notes
None


# Resources
None 
