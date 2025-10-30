# miniRSA

## Solution
Researched about RSA and figured out from the hint about the case where e
is very small and the message m^e <n the encryption doesn't wrap around
the modulus so we can decrypt it simply by taking the eth root of the text
hence i used a long number cube root algorithm and edited it a bit so that
it changes the cube root to hex, then binary, then ascii and finally 
give me the flag

```
from gmpy2 import iroot
from Crypto.Util.number import long_to_bytes


c = 2205316413931134031074603746928247799030155221252519872649649212867614751848436763801274360463406171277838056821437115883619169702963504606017565783537203207707757768473109845162808575425972525116337319108047893250549462147185741761825125
N = 29331922499794985782735976045591164936683059380558950386560160105740343201513369939006307531165922708949619162698623675349030430859547825708994708321803705309459438099340427770580064400911431856656901982789948285309956111848686906152664473350940486507451771223435835260168971210087470894448460745593956840586530527915802541450092946574694809584880896601317519794442862977471129319781313161842056501715040555964011899589002863730868679527184420789010551475067862907739054966183120621407246398518098981106431219207697870293412176440482900183550467375190239898455201170831410460483829448603477361305838743852756938687673

m = None
for k in range(10000):
    candidate = c + k * N
    root, exact = iroot(candidate, 3)
    if exact:
        m = int(root)
        print(f"Found perfect cube at k = {k}")
        break

if m is None:
    print("No perfect cube found in the range.")
else:
    print(f"m = {m}")
    try:
        flag = long_to_bytes(m)
        print("Flag:", flag)
    except Exception as e:
        print("Raw bytes:", long_to_bytes(m))

```



## Flag
```
picoCTF{n33d_a_lArg3r_e_606ce004}

```

# Concepts Learnt
Learnt about RSA decryption and about this special case which makes it a bit easier



# Notes
None


# Resources
ChatGPT for the cube root algorithm

