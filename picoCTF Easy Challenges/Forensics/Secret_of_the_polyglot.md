# Secret of the Polyglot
Challenge link: https://play.picoctf.org/practice/challenge/423
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
### Download the file given by the challenge
Use `wget { url }` in Terminal to download the file.
```bash
wget https://artifacts.picoctf.net/c_titan/9/flag2of2-final.pdf
```
### Analyze the file
Looking at the file we could see it a pdf file. Use `pdftotext { .pdf file} {.txt file }`.
```bash
pdftotext flag2of2-final.pdf flag2of2-final.txt
```
We could see a portion of the flag appear in the newly created **flag2of2-final.txt file. **

It seems like there aren't anything left but we only got the second half of the flag. 

Looking at the hint, we can see that they suggesting us open the file in another way.

We could use `file { file }`to see the file type of the pdf file.
```bash
file flag2of2-final.pdf 
```
We get the following response
```bash
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
```
So it appears to be a PNG file. We could convert the pdf file to pdf using `mv` or `cp`
```bash
mv flag2of2-final.pdf flag2of2-final.png
```
`or`
```bash
cp flag2of2-final.pdf flag2of2-final.png
```
We get a new file called flag2of2-final.png. Open the file give us the rest of the flag.
## Documentation
[wget - Manual page](https://linux.die.net/man/1/wget)

[pdftotext - Manual page](https://linux.die.net/man/1/pdftotext)

[mv - Manual page](https://linux.die.net/man/1/mv)

[cp - Manual page](https://linux.die.net/man/1/cp)

[file - Manual page](https://linux.die.net/man/1/file)


