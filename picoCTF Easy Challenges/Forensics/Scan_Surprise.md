# Scan Surprise
Challenge link: https://play.picoctf.org/practice/challenge/444
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
### Download the file given by the challenge
Use **wget { url }** in Terminal to download the file.
```bash
wget https://artifacts.picoctf.net/c_atlas/3/challenge.zip
```
### Unpack the file and do some analysis
```bash
unzip challenge.zip
```
You can use Terminal to see what's in the directory we just unzipped or use a file explorer on your linux distro.

We could see that there is a image in /home/ctf-player/drop-in/ called **flag.img**. 

Opening the image give us QR code. There is 2 way you can get the flag using the QR code.
- You can use your phone to scan the QR code and it will give the flag.
- Or you can use **zbarimg { file }** on your Terminal to get the flag.
  
After scaninning you should get the flag:
```
picoCTF{SPOILER}
```
### Side note
zbarimg is from zbar-tools, not a pre-installed package, you can install it in terminal. 
## Documentation
[wget - Manual page](https://linux.die.net/man/1/wget)
