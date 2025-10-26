# Trivial Flag Transfer Protocol

## Solution

Opened the the pcapng file using wireshark after which I went on to filter all
the tftp files in it then exported all of the data that was there in the files
Found 3 images with no hints of a flag as such but also had more files like 
an instructions.txt file and a plan file which had a ciphered code in it. Went online to decipher
it to find that it was ciphered using ROT13 and the actual text said something
along the lines of "we must disguise our flag" and "I have hidden this with due diligence" then
Opened the program file which had some content along with
a file that said steghide so it was highly possible that steghide had been used
to hide the flag within the images then I opened wsl and ran steghide extract -sf with
all 3 images and DUEDILIGENCE as the password to finally obtain the flag from the 3rd image


## Flag
```
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```
#Concepts Learnt

Learnt how to decipher simple codes like ROT13 ones and learnt to use steghide which is 
basically used to hide flags or other information behind pictures

# Notes
Couldn't figure out how to use steghide properly could've used man to make it easier

# Resources
https://www.dcode.fr/shift-cipher
