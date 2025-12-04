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
