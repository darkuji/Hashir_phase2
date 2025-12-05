# Hide and Seek 
### Sakamoto’s at it again with a game of hide and seek, but this time, it’s not with Shin or his daughter. An old friend hid some secret data in this image. Can you find it before the others do?

Hint:
Even in retirement, Sakamoto never loses at hide and seek. Maybe stegseek can help you keep up.


## My Solve
Since the hint directly mentions stegseek i installed it and ran it with the image and later figured out that
i need a textfile from which it bruteforces passwords. Got stuck here and had to use gpt to get a file called 
rockyou.txt which has alot of common passwords from GitHub. Ran stegseek with the image and textfile and got the 
flag 

**Flag:** nite{h1d3_4nd_s33k_but_w1th_st3g_sdfu9s8}


```
stegseek sakamoto.jpg /mnt/Users/naira/Downloads/wordlists/rockyou.txt 

```

```
Found passphrase: "iloveyou1"
Original filename: "flag.txt"
Extracting to "sakamoto.jpg.out"
```

## What I Learned
Learned how to use stegseek

## References
ChatGPT



# Nutrela Chunks

### One of my favorite foods is soya chunks. But as I was enjoying some Nutrela today, I noticed a few chunks weren’t quite right. Seems like something’s off with their structure. Could you help me fix these broken chunks so I can enjoy my meal again?


## My Solve
Opened the corrupted image in a hex editor and the encrypted text was similar to that of a normal
png file just in lowercase so i googled the hex dump for a normal png file and made the changes to 
png,ihdr,idat and iend to make them uppercase and got the flag



**Flag:** nite{n0w_y0u_kn0w_ab0ut_PNG_chunk5}


```
 
```

## What I Learned
Learned about the hex dump of a png file 

## References
https://en.wikipedia.org/wiki/PNG


# RAR of the Abyss
### Two philosophers peer into the networked abyss and swap a secret. Use the secret to decrypt the Abyss’ RAwR and pull your flag from the void.


## My Solve

Opened the pcap file in wireshark and analysed the tcp packets and there was a convo bw two people 
in which the password was present. Extracted the raw tcp packet which had the ascii of "RAR" as a 
.rar file and extracted it with the password to replace the empty flag with the actual flag file.
catted the new file 

**Flag:** nite{thus_sp0k3_th3_n3tw0rk_f0r3ns1cs_4n4lyst}


```
winrar x -p"b3y0ndG00dand3vil" abyss_aarchive.rar

```

## What I Learned
Learned how to work with tcp packets 

## References
None


# Ninetails

### Looks like I got a little too clever and hid the flag as a password in Firefox, tucked away like one of NineTails’ many tails. Recover the "logins" and the "key4" and let it guide you to the flag.

Hint:
I named my Ninetails "j4gjesg4", quite a peculiar name isn't it?


## My Solve
Extracted the rar file and got an ad1 file which i opened on ftk imager. Inspected the file tree and 
found the folder GIC2024/AppData/Roaming/Mozilla/Firefox/Profiles/j4gjesg4.default-release similar to the hint,
Exported the logins.json nd key4.db files, took some help from a friend and got my hands on a tool named firefox
decrypt on the folder and got the flag

**Flag:** GCTF{m0zarella_f1ref0x_p4ssw0rd}


```
python firefox_decrypt.py -d "C:\Users\naira\Desktop\j4gjesg4.default-release" 
```

## What I Learned
Learned how to use firefox decrpyytt

## References
None


