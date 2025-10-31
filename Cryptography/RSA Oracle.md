# RSA Oracle

## Solution
Did some research on RSA and found a property which basically states  that
m^e%n * x^e%n = x*m ^ e % n and here the password was m^e % n and after decrypting 
the number whose hex is 2 i got 2^e % n and then multiplied them and carried out the
operations shown to get the flag
```
>>> var1 = 2336150584734702647514724021470643922433811330098144930425575029773908475892259185520495303353109615046654428965662643241365308392679139063000973730368839
>>> var2 = 5067313465613043651275429665315895824157755779222372979446076012356324498190828210335763979330272318657269048435311897896433721115606764442199497891219230
>>> var1*var2
11838007315725944462917501970869949019150019153714056931355027069712797420929418502601441873895368228007950352680183762125090436285497800797519302174079230053776230956741880244950163145869820928702272465467607694948245076340696759487604021251562488669723292161136993721794819524990850096959527503527309573970
>>> int('6c60cc6a60',16)
465480477280
>>> 465480477280//2
232740238640
>>> hex(465480477280)
'0x6c60cc6a60'
>>> hex(232740238640_
  File "<stdin>", line 1
    hex(232740238640_
                    ^
SyntaxError: invalid decimal literal
>>> hex(232740238640)
'0x3630663530'
>>> bytes.fromhex('3630663530')
b'60f50'
>>> b'60f50'.decode()
'60f50'


```
```
root@ASUS-ZN14:/mnt/c/Users/naira/Downloads# { printf 'e\n'; sleep 3; echo -e '\x02\n'; } | nc titan.picoctf.net 61553             nc titan.picoctf.net 61553
*****************************************
****************THE ORACLE***************
*****************************************
what should we do for you?
E --> encrypt D --> decrypt.
d
Enter text to decrypt: 11838007315725944462917501970869949019150019153714056931355027069712797420929418502601441873895368228007950352680183762125090436285497800797519302174079230053776230956741880244950163145869820928702272465467607694948245076340696759487604021251562488669723292161136993721794819524990850096959527503527309573970
decrypted ciphertext as hex (c ^ d mod n): 6c60cc6a60
decrypted ciphertext: l`Ìj`

what should we do for you?
E --> encrypt D --> decrypt.
^C
root@ASUS-ZN14:/mnt/c/Users/naira/Downloads# openssl enc -aes-256-cbc -d -in secret.enc
enter AES-256-CBC decryption password:
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
picoCTF{su((3ss_(r@ck1ng_r3@_60f50766}
```


## Flag
```
picoCTF{su((3ss_(r@ck1ng_r3@_60f50766}
```

# Concepts Learnt
RSA encryption and decryption


# Notes
None


# Resources
https://crypto.stackexchange.com/questions/24880/how-multiplicative-property-of-rsa-can-be-exploited