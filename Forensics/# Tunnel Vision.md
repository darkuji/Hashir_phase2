# Tunnel Vision

## Solution
Downloaded the given file and tried to open it but it was corrupted
Opened the file in HxD which is a hex editor. Saw that the first 3 bytes
which were 42 4D 8E were similar to that of a BMP file indicating that it 
was originally a BMP file. Opened a normal bmp file from another challenge on
hxd and compared the bits of the first line to the corrupted one and modified the
corrupted one accordingly which actually worked and opened the file. The image
was kinda cropped and said not the flag so i thought of changing the resolution but
couldn't figure out how to. Found out that the image was of 1134x306 resolution then
tried to change it in hxd had to take some help from chatgpt from which i found out
how to edit the height of the image in hxd and set it to 850 which was a little less
than the max limit by setting the bits to 52, 03 then opened the image again and obtained
the flag




## Flag
```
picoCTF{qu1t3_a_v13v_2020}
```
#Concepts Learnt
Learnt how to use HxD for basic forensics and how to repair a slightly corrupted file



# Notes
None


# Resources
ChatGPT

