# Transformation
Challenge link: https://play.picoctf.org/practice/challenge/104
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
Download the file given using `wget`
```bash
wget https://mercury.picoctf.net/static/0d3145dafdc4fbcf01891912eb6c0968/enc
```
Opening the file or using `cat` to read the file
```bash
cat enc
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸弰摤捤㤷慽
```
It printed out weird words in the file, maybe the flag is encoded.
### Solution 1: Using Cyberchef
Using [CyberChef](https://gchq.github.io/CyberChef) we can decoded the flag. In CyberChef main menu we can use `Encode text` function to get the flag. After trying out many encoding pattern. We can use `UTF-16BE(1201)` to get the flag.

![image](https://github.com/user-attachments/assets/b7243391-096a-4d2f-9daa-0ff3aa2d5aa4)

### Solution 2: Using python.
Reading the code given by the challenge
```python
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
```
Let's explain the code, one by one.
```python
for i in range(0, len(flag),2)
```
Creates a sequence of indices starting from 0 going up to length of the flag with the step of 2 (0,2,4,...)
```python
ord(flag[i] << 8 + ord(flag[i+1])
```
Convert the first character to ASCII/Unicode value and shift its value by 8 bit to the left ( multiplies by 256 ). Convert the second character to ASCII/Unicode value and combines it with the first character shifted value using addition resulted in a large number. The process repeats until the end of the flag.
```python
''.join([chr()])
```
Converts the number back to a character. And combine them into a string. Resulted in a encoded flag.

We can use python to decode the flag. 
```python 
enc_flag = '灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸弲㘶㠴挲ぽ'    

def decode_flag(encoded):
    decoded = ''
    for char in encoded:
        # Get numeric value of the encoded character
        value = ord(char)
        
        # Extract first character (upper 8 bits)
        first_char = chr(value >> 8)
        
        # Extract second character (lower 8 bits)
        second_char = chr(value - ((value>>8)<<8))
        
        # Add both characters to result
        decoded += first_char + second_char
        
    return decoded

print(decode_flag(enc_flag))
```
Running the program give us the flag.
`picoCTF{SPOILER}`
##Documentation
[Bitwise in Python](https://www.geeksforgeeks.org/python-bitwise-operators/)

[wget - Manual page](https://linux.die.net/man/1/wget)
