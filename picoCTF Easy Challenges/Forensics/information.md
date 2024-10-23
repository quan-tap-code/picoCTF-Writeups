![image](https://github.com/user-attachments/assets/183aa684-5dc3-427f-ade4-b526e7491a21)# information
Challenge link: https://play.picoctf.org/practice/challenge/186
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
### Download the file given by the challenge
Use `wget { url }` in Terminal to download the file.
```bash
wget https://mercury.picoctf.net/static/a614a27d4cb251d04c7d2f3f3f76a965/cat.jpg
```
### Analyze the file
We got a `.jpg` file. We could use `exiftool` to check the metadata of the image. 
```bash
exiftool cat.jpg
ExifTool Version Number         : 12.52
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2022:04:17 04:35:09-04:00
File Access Date/Time           : 2023:08:04 13:52:19-04:00
File Inode Change Date/Time     : 2022:04:17 04:35:09-04:00
File Permissions                : -rwxrwxrwx
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```
We could see all the data look normal but the `License` doesn't really make sense. It maybe a encoded message. Let guess that it's base64 encoded. 

We could use `CyberChef` to decode.

![image](https://github.com/user-attachments/assets/2c1359d6-2463-4c7b-916d-579c33ee9699)

So our guess is right.

Alternatively, we could use `base64` in terminal to decode.

```bash
echo "cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" | base64 -d
picoCTF{SPOILER}
```
## Documentation
[wget - Manual page](https://linux.die.net/man/1/wget)

[exiftool - Manual page](https://linux.die.net/man/1/exiftool)

[wget - Manual page](https://linux.die.net/man/1/wget)

[base64 - Manual page](https://linux.die.net/man/1/base64)

[CyberChef](https://gchq.github.io/CyberChef/)
