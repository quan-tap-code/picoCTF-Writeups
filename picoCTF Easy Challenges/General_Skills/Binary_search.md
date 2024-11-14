# Binary Search
Challenge link: https://play.picoctf.org/practice/challenge/442
- [Solution](#solution)
- [Documentation](#documentation)
## Solution
Download the file given by the challenge using `wget {url}`.
```bash
wget https://artifacts.picoctf.net/c_atlas/18/challenge.zip
```
Unzip the file using `unzip {file}` in terminal.
```bash
unzip challenge.zip
```
After we unzipped the file, we got multiple directories. Openning each directory we got a file called `guessing_game.sh` in `drop-in` folder.

Executing the file give us a guessing game. They allow us to guess up to 10 times. Using basic principle of binary search it comes down to guessing game.

Start guessing from 500, the program will tell us lower or higher. Continue to guess from the middle until you got it right. 
## Documentation 
[wget - Manual page](https://linux.die.net/man/1/wget)

[Binary search - Wiki](https://en.wikipedia.org/wiki/Binary_search)
