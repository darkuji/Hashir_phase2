# Bare Metal Alchemist

## Solution
Used ghidra which i had used for the tameimpala challenge in citadel to open
the file. opened the main function which seemed similar to a C program but had
weird variable names so i got stuck. saw that the function z1() was recurring and 
after seeing it in ghidra i learnt that it was doing byte replacement. the code 
was performing XOR on 0x68 byte abnd 0xA5 till the key value was obtained.
Performed XOR on the memory in 0x68 with 0xA5 but some useless stuff came up so
did the same thing but with 0x0068 and 0xA5 which gave me a sequence of hex which i 
decoded to numbers and then to ascii and obtained the flagh



## Flag
```
TFCCTF{Th1s_1s_som3_s1mpl3_4rdu1no_f1rmw4re}
```

# Concepts Learnt
Learned how to view and inspect programs on Ghidra 


# Notes
None


# Resources
ChatGPT for XOR calculation and conversions
https://www.youtube.com/watch?v=fTGTnrgjuGA

