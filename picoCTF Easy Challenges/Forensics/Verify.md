# Verify 
Challenge link: https://play.picoctf.org/practice/challenge/450

- [Solution](#solution) 
- [Documentation](#documentation)

## Solution
### Download the file given by the challenge
Use **wget { url }** in Terminal to download the file.
```bash
wget https://artifacts.picoctf.net/c_rhea/21/challenge.zip
```
### Unpack the file and do some analysis
Unpack the file by using **unzip { file }** in Terminal.
```bash
unzip challenge.zip
```
As the Terminal unzip the file we notice we handling with a lot of files. We can use **cd** to jump in the folder which has the file called **checksum.txt**.    

Use **cat { file }** to print out the txt in Terminal.
```bash
cat checksum.txt
```
It should print out the hash they asking us to look for.

Alternatively, you can use the following in Terminal if you don't want to use **cd** ( {.} respresent the folder you downloaded the original zip file ).
```bash
cat ./home/ctf-player/drop-in/checksum.txt
```
The challenge ask us to find the file which has the right hash. Using **sha256sum { file } or sha256sum {directory}/*** to check the hash of a file or a directory.
```bash
sha256sum home/ctf-player/drop-in/files/*
```
Hmm, there are too many file thus there are lots of hashes. We could use **grep** to find our file.
```bash
sha256sum home/ctf-player/drop-in/files/* | grep { hash }
```
The Terminal should return us with the file which has the hash we need to find ( change { hash } to the hash in checksum.txt before ).

We can try to read the file using **cat** again.
```bash
cat ./files/{ file }
```
The Terminal print out a bunch of weird characters. It appears the flag is encrypted.

Notice there is another file in drop-in folder alongside with checksum.txt called **decrypt.sh**. After reading it with **cat** we could see that it is a decrypting script which required a file path. 

Combine with the file we just found we could use the following to get the flag.
```bash
./decrypt.sh ./files/{ file }
```
If the script fails to run. We can manually run it by looking at the scipt decode method we just print out in the Terminal. 
```bash
openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in files/{file} -k picoCTF
```
It should print out our flag which should look like this.
```
picoCTF{SPOILER}
```

# Documentation
[grep - Manual page](https://linux.die.net/man/1/grep)

[sha256sum - Manual page](https://linux.die.net/man/1/sha256sum)

[openssl - Manual page](https://linux.die.net/man/1/openssl)

[cat - Manual page](https://linux.die.net/man/1/cat)

[wget - Manual page](https://linux.die.net/man/1/wget)



