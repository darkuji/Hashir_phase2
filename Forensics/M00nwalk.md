# M00nwalk

## Solution
Couldn't Figure anything out so looked at the hint and went to GitHub
to install a program named SSTV which decodes the SSTV signal to generate
an image from an audio file then ran the command in the specified format to
get the flag


```
root@ASUS-ZN14:/mnt/c/Users/naira/Downloads/sstv# sstv -d /mnt/c/Users/naira/Downloads/message.wav -o result.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [######################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
root@ASUS-ZN14:/mnt/c/Users/naira/Downloads/sstv# dir result.png
result.png
root@ASUS-ZN14:/mnt/c/Users/naira/Downloads/sstv# sstv -d /mnt/c/Users/naira/Downloads/message.wav -o /mnt/c/Users/naira/Downloads/result.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [######################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```


## Flag
```
picoCTF{beep_boop_im_in_space}
```

#Concepts Learnt
Learnt the basic function of sstv



# Notes
None


# Resources
https://github.com/colaclanth/sstv
