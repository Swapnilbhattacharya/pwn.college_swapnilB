## Cat: Not the pet, but the command!
This challenge asks to obtain the flag using the cat command from a file named flag in the home directory.
### My solve
**Flag:** `pwn.college{c7XpX-E_r0Pvncc-iMGwmT_XRDR.QXxcTN0wiM5gjNzEzW}`
I simply used the cat command using ~/flag as the argument as it has been given that flag is a directory under home directory.

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat ~/flag
pwn.college{c7XpX-E_r0Pvncc-iMGwmT_XRDR.QXxcTN0wiM5gjNzEzW}
```
### What i learned
I learned about the cat command and its function that it simply prints the contents of the file given to it as an argument. It concatenates contents of multiple files if they are given as arguments.

## Catting absolute paths
This challenge asks to read the flag using the cat command but this time it is not there in my home directory rather it is in a directory called flag.

### My solve
**Flag:** `pwn.college{Y3rAQaA8X2sSosFYASGJSLASKHH.QX5ETO0wiM5gjNzEzW}`
I used the cat command along with the absolute path of the flag directory to reach the flag.
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{Y3rAQaA8X2sSosFYASGJSLASKHH.QX5ETO0wiM5gjNzEzW}
```
### What I learned
I learnt that the cat command can not only be used on files in the home directory but also in those files outside the home directory using their absolute paths.

## More Catting practice
This challenge is about catting out or reading out the contents of the file flag which is placed inside a complex directory without cding to that directory.

### My solve
**Flag:** `pwn.college{EVIIgo0-Ke-QkZ3STXCqoru9M3I.QXwITO0wiM5gjNzEzW}`
I was given the absolute path to my required directory in the challenge. I simply used the cat command on the given path directly to obtain the flag.
```
swapnil@Pavilion15:~/pwn_keys$ ssh -i ./key hacker@dojo.pwn.college
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/lib32/gconv/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /usr/lib32/gconv/flag
pwn.college{EVIIgo0-Ke-QkZ3STXCqoru9M3I.QXwITO0wiM5gjNzEzW}
```
### What I learned
I learnt that I can also use the cat command on any kind of complex or simple absolute paths without even having to use the cd command to get into that directory.

## Grepping for a needle in a Haystack
This challenge teaches us to use the grep command to essentially search for a specific word in a directory.
### My solve
**Flag:** `pwn.college{cMhRLUuB2eGlR2ViLqfg4aZxaUR.QX3EDO0wiM5gjNzEzW}`
I was told that my flag was present in /challenge/data.txt path so i simply used the grep command to search for the flag in this path. I know(also given in hint)
that the flag always begins with "pwn.college". Hence, i used it as the keyword to search for my flag.
```
swapnil@Pavilion15:~/pwn_keys$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{cMhRLUuB2eGlR2ViLqfg4aZxaUR.QX3EDO0wiM5gjNzEzW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$
```
### What I learned
I learned about the grep command which is equivalent to a simple search in a directory in which there might be too much of data and cat command might make things complex. I understood that by using the grep command I could easily print my required line in which "pwn.college" was present and it obviously was my required flag.

## Comparing Files
This challenge is about comparing two files using the diff command and printing whatever changes are there between the two.

### My solve
**Flag:** `pwn.college{cErIFlsKXkz7Dfc1guD0PSqalWQ.01MwMDOxwiM5gjNzEzW}`
Here, I was told that there were 100 decoy flags in the first directory and the real flag along with those 100 flags in my second directory. Since both these files were in the challenge directory I first used cd to get into my challenge directory and then went on to use diff command on both the directories to find my real flag. 
```
hacker@commands~comparing-files:~$ cd /challenge
hacker@commands~comparing-files:/challenge$ diff /decoys_only.txt /decoys_and_real.txt
diff: /decoys_only.txt: No such file or directory
diff: /decoys_and_real.txt: No such file or directory
hacker@commands~comparing-files:/challenge$ diff ./decoys_only.txt ./decoys_and_real.txt
66a67
> pwn.college{cErIFlsKXkz7Dfc1guD0PSqalWQ.01MwMDOxwiM5gjNzEzW}
```

### Mistake I made
Since i had used cd to get into the challenge directory in the beginning, i was supposed to use the . to refer to my cwd before writing the rest of the absolute paths to my required directories but I did not do so which led to an error which said that the two required directories were absent.

### What I learned.
I learned how to use diff command to compare and find out the difference between two files. I learned that I can get the difference in the content as well as if some additional content in the other file than in the first file.

## Listing files 

### My solve

**Flag:** ``

## What I learned













