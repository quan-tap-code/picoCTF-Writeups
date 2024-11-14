# CanYouSee
Challenge link: https://play.picoctf.org/practice/challenge/408
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
### Download the file given by the challenge
Use `wget { url }` in Terminal to download the file.
```bash
wget https://artifacts.picoctf.net/c_titan/6/unknown.zip
```
### Unpack the file 
Unpack the file by using `unzip { file }` in Terminal.
```bash
unzip unknown.zip
```
After we unzipped the file, we got a `.jpg` file. Open the file doesn't give us anything. 

Using the hint, we could assume that we need to find the information about the picture.

We could use `exiftool {file}` to see [metadata](https://en.wikipedia.org/wiki/Metadata) of the image.
```
exiftool ukn_reality.jpg
ExifTool Version Number         : 12.52
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2024:02:15 23:40:14+01:00
File Access Date/Time           : 2024:02:15 23:40:14+01:00
File Inode Change Date/Time     : 2024:02:15 23:40:14+01:00
File Permissions                : -rwxrwxrwx
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4
```
All of the data seem normal except the `Attribution URL` which isn't a URL. Instead it looks like a encoded message. 

We could guess the flag is [base64-encoded](https://en.wikipedia.org/wiki/Base64)

Using [CyberChef](https://gchq.github.io/CyberChef/) we can decode and get the flag

![image](https://github.com/user-attachments/assets/860168ee-3efb-4f2f-90d3-dcc02fd1e763)

or we could use the terminal to decode using `base64`
```
echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==" | base64 -d
```
```bash
picoCTF{SPOILER}
```
## Documentation 
[wget - Manual page](https://linux.die.net/man/1/wget)

[exiftool - Manual page](https://linux.die.net/man/1/exiftool)

[base64 - Manual page](https://linux.die.net/man/1/base64)





