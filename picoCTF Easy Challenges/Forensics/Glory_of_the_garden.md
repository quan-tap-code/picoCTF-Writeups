# Glory of the garden
Challenge link: https://play.picoctf.org/practice/challenge/44
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
### Download the file given by the challenge
Use `wget { url }` in Terminal to download the file.
```bash
wget https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg
```
### Analyze the file
We could see that we got a `.jpg` file. We try to use `exiftool` on the file to see if there are anything
```bash
exiftool garden.jpg
ExifTool Version Number         : 12.76
File Name                       : garden.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2020:10:27 01:39:31+07:00
File Access Date/Time           : 2024:10:23 02:17:59+07:00
File Inode Change Date/Time     : 2024:10:23 02:17:59+07:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
Profile CMM Type                : Linotronic
Profile Version                 : 2.1.0
Profile Class                   : Display Device Profile
Color Space Data                : RGB
Profile Connection Space        : XYZ
Profile Date Time               : 1998:02:09 06:49:00
Profile File Signature          : acsp
Primary Platform                : Microsoft Corporation
CMM Flags                       : Not Embedded, Independent
Device Manufacturer             : Hewlett-Packard
Device Model                    : sRGB
Device Attributes               : Reflective, Glossy, Positive, Color
Rendering Intent                : Perceptual
Connection Space Illuminant     : 0.9642 1 0.82491
Profile Creator                 : Hewlett-Packard
Profile ID                      : 0
Profile Copyright               : Copyright (c) 1998 Hewlett-Packard Company
Profile Description             : sRGB IEC61966-2.1
Media White Point               : 0.95045 1 1.08905
Media Black Point               : 0 0 0
Red Matrix Column               : 0.43607 0.22249 0.01392
Green Matrix Column             : 0.38515 0.71687 0.09708
Blue Matrix Column              : 0.14307 0.06061 0.7141
Device Mfg Desc                 : IEC http://www.iec.ch
Device Model Desc               : IEC 61966-2.1 Default RGB colour space - sRGB
Viewing Cond Desc               : Reference Viewing Condition in IEC61966-2.1
Viewing Cond Illuminant         : 19.6445 20.3718 16.8089
Viewing Cond Surround           : 3.92889 4.07439 3.36179
Viewing Cond Illuminant Type    : D50
Luminance                       : 76.03647 80 87.12462
Measurement Observer            : CIE 1931
Measurement Backing             : 0 0 0
Measurement Geometry            : Unknown
Measurement Flare               : 0.999%
Measurement Illuminant          : D65
Technology                      : Cathode Ray Tube Display
Red Tone Reproduction Curve     : (Binary data 2060 bytes, use -b option to extract)
Green Tone Reproduction Curve   : (Binary data 2060 bytes, use -b option to extract)
Blue Tone Reproduction Curve    : (Binary data 2060 bytes, use -b option to extract)
Image Width                     : 2999
Image Height                    : 2249
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2999x2249
Megapixels                      : 6.7
```
We could see there isn't anything unusual about the metadata of the file. Let's use the hint. 
`What is a hex editor ?`
From this we could see that they want us to use a hex editor on the image.

You can search online for hex editor but there is a package you can install to use a hex editor on the terminal. `ncurses-hexedit`.
```bash 
sudo apt install ncurses-hexedit
```
Use `hexeditor` after the package is installed.
```bash
hexeditor garden.jpg
```
We all know the flag have the phrase `picoCTF` so we just need to search for in using the pre-built search option of the editor `( Ctrl + W )`.

Search the string `picoCTF` and we could see the flag appear in the editor.
```bash
picoCTF{SPOILER}
```
## Documentation
[wget - Manual page](https://linux.die.net/man/1/wget)

[exiftool - Manual page](https://linux.die.net/man/1/exiftool)

[ncurses-hexedit - Manual page](https://www.kali.org/tools/ncurses-hexedit/)








