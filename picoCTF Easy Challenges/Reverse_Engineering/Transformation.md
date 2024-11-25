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
