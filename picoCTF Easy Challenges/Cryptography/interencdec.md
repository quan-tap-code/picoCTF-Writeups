# interencdec
Challenge link: https://play.picoctf.org/practice/challenge/418
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
Use `wget` to download the file to your directory or download by clicking in the link.

```bash
wget https://artifacts.picoctf.net/c_titan/1/enc_flag
```
Use `cat` to see what inside the file we just downloaded.
```bash
cat enc_flag
```
```bash
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgya3lNRFJvYTJvMmZRPT0nCg==
```
It looks like a `base64` encoded message. Let's decode it using [CyberChef](https://gchq.github.io/CyberChef/) or using terminal 

```bash
echo "YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgya3lNRFJvYTJvMmZRPT0nCg==" | base64 -d
```
```bash
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2kyMDRoa2o2fQ=='
```
Inside the quote still looks like a `base64` encoded message. If we decoded it again we get.
```bash
echo "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2kyMDRoa2o2fQ==" | base64 -d
```
```bash
wpjvJAM{jhlzhy_k3jy9wa3k_i204hkj6} 
```
Now the message looks like a flag but it isn't. It's still encoded, maybe with `Rotation Cipher`. There are many decoder online that we could use to get the flag.
`picoCTF{SPOILER}`
## Documentation
[wget - Manual page](https://linux.die.net/man/1/wget)

[base64 - Manual page](https://linux.die.net/man/1/base64)

[Caesar cipher wikipedia](https://en.wikipedia.org/wiki/Caesar_cipher)
