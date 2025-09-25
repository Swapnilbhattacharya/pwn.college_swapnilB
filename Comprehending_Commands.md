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

## Touching files
This challenge teaches us how to create files by using touch command.

### My solve
**Flag:** `pwn.college{MjelJ-7D9Jk93AdFIbag0dHLn8M.QXwMDO0wiM5gjNzEzW}`
I was asked to create two files pwn and college respectively inside the tmp directory. So i used cd to go into the tmp directory and then used the touch command separately once on pwn and once on college and this created the two files inside my tmp directory.
```bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{MjelJ-7D9Jk93AdFIbag0dHLn8M.QXwMDO0wiM5gjNzEzW}
```

### What I learned
I learnt how to use the touch command to create a file inside the current working directory or even by using an absolute path.

## Removing Files
This challenge is about deleting a file using the new "rm" command.

### my solve
**Flag:** `pwn.college{445ccVKgGz2UOFBzKh0dfqe8fnv.QX2kDM1wiM5gjNzEzW}`
In this challenge i was given a file called "delete_me" in my home directory. I used the rm command on the file name and it got removes and i made sure that my process was correct by using the ls command for listing directories. I then used the /challenge/check command as instructed.
```bash
hacker@commands~removing-files:~$ ls
 delete_me  '~'
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
'~'
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{445ccVKgGz2UOFBzKh0dfqe8fnv.QX2kDM1wiM5gjNzEzW}
```
### What I learned
I learnt the process and syntax of writing the rm command to simply remove a file from the current directory using the rm command.

## Moving files
This challenge is about using the mv command to move files from one to another directory.

### My solve
I had been given a flag file which I had to move into the hack-the-planet directory inside tmp directory so i simply used the mv command on the flag.
**Flag:** `pwn.college{gVEDwCDoHAyqZGR_zKUTLYGss5S.0VOxEzNxwiM5gjNzEzW}`
```bash
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{gVEDwCDoHAyqZGR_zKUTLYGss5S.0VOxEzNxwiM5gjNzEzW}
```
### What I learned
I learned how to use mv command and its syntax to effectively move files from one folder to another using Linuc CLI.

## Hidden files
This challenge teaches us about a certain convention in Linux which is that files beginning with a '.' don't show up by default.

### My solve
**Flag:** `pwn.college{09ietLw4MSLNDjT8w5jiwNw-ZPQ.QXwUDO0wiM5gjNzEzW}`
The challenge taught that in order to list the files that begin with '.' in a directory we have to use the command ls -a so i went into the /(root directory) as instructed and used the ls -la command. It gave me a long list of files with one of them having the flag. I used the cat command to read its contents and there it was- The beautiful flag.
```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -la
total 72
drwxr-xr-x    1 root root 4096 Sep 25 17:42 .
drwxr-xr-x    1 root root 4096 Sep 25 17:42 ..
-rwxr-xr-x    1 root root    0 Sep 25 17:41 .dockerenv
-rw-r--r--    1 root root   60 Sep 25 17:41 .flag-256621546710297
lrwxrwxrwx    1 root root    7 Apr  4 02:03 bin -> usr/bin
drwxr-xr-x    2 root root 4096 Apr 15  2020 boot
drwxr-xr-x    1 root root 4096 Sep 25 17:41 challenge
drwxr-xr-x    6 root root  380 Sep 25 17:41 dev
drwxr-xr-x    1 root root 4096 Sep 25 17:41 etc
drwxr-xr-x    1 root root 4096 Sep  7 01:38 home
lrwxrwxrwx    1 root root    7 Apr  4 02:03 lib -> usr/lib
lrwxrwxrwx    1 root root    9 Apr  4 02:03 lib32 -> usr/lib32
lrwxrwxrwx    1 root root    9 Apr  4 02:03 lib64 -> usr/lib64
lrwxrwxrwx    1 root root   10 Apr  4 02:03 libx32 -> usr/libx32
drwxr-xr-x    2 root root 4096 Apr  4 02:03 media
drwxr-xr-x    2 root root 4096 Apr  4 02:03 mnt
drwxr-xr-x    1 root root   16 Oct 26  2024 nix
drwxr-xr-x    1 root root 4096 Sep  7 01:38 opt
dr-xr-xr-x 3321 root root    0 Sep 25 17:41 proc
drwx------    1 root root 4096 Sep  7 01:38 root
drwxr-xr-x    1 root root 4096 Sep 25 17:41 run
lrwxrwxrwx    1 root root    8 Apr  4 02:03 sbin -> usr/sbin
drwxr-xr-x    2 root root 4096 Apr  4 02:03 srv
dr-xr-xr-x   13 root root    0 Sep 23 22:44 sys
drwxrwxrwt    1 root root 4096 Sep 25 17:41 tmp
drwxr-xr-x    1 root root 4096 Sep  7 01:22 usr
drwxr-xr-x    1 root root 4096 Sep  7 01:22 var
hacker@commands~hidden-files:/$ cat .flag-256621546710297
pwn.college{09ietLw4MSLNDjT8w5jiwNw-ZPQ.QXwUDO0wiM5gjNzEzW}
```
### What I learned
I learned about the default convention of linux about files beginning with '.' don't get listed by default on using the ls command. I learnt how to correct the issue by using the ls -a command. 

## An epic filesystem quest
### My solve
### What I learned










