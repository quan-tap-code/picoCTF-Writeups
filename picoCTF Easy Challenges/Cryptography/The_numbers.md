# The Numbers
Challenge link: https://play.picoctf.org/practice/challenge/68
- [Solution](#solution)
- [Documentation](#documentaion)
## Solution
Use `wget` to download the file to your directory or download it straight from the website.
```bash
wget https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
```
Openning the image give us a array of number that looks like the flag.

![image](https://github.com/user-attachments/assets/48acc4f1-eb54-4427-8768-69ca2b75882d)

From this we could guess how to solve it. The number may represent the alphabetical order, after we decode the first 4 letters we know it is the alphabetical order.

`16 is p`

`9 is i`

`3 is c`

`15 is o`

and so on.

After we decoded it, we got the flag.

`picoCTF{SPOILER}`

## Documentation
