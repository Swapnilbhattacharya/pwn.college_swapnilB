## Learning from documentation
This challenge teaches us how to properly read the documentation and to figure out how to use various programs
### My solve
**Flag:** `pwn.college{QIkK7AusHQNLy1mZoPckHCto-v2.QX0ITO0wiM5gjNzEzW}`
I was given a program called challenge in the challenge directory and i was supposed to pass it a specific argument called "--giveflag". 
So I simply used the common documentation style to pass the argument and found the flag
```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{QIkK7AusHQNLy1mZoPckHCto-v2.QX0ITO0wiM5gjNzEzW}
```
### What I learned
I learnt the proper documentation and passed an argument into a given program.

## Learning complex usage
This challenge introduces us to a slightly complicated form of the documentation where we have 2 arguments. 
### My solve
**Flag:** `pwn.college{AKA7nRHBE52bvT2fASk1ul1bFcd.QX1ITO0wiM5gjNzEzW}`
It was asked that we have to use the --printfile argument on the challenge program in the /challenge directory. 
The argument of the --printfile argument would be my path to the flag which is obviously /flag
Following the documentation I wrote the command and found the flag.
```bash
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{AKA7nRHBE52bvT2fASk1ul1bFcd.QX1ITO0wiM5gjNzEzW}
```
### What I learned 
I learned to use little complex commands and used two arguments on a program to find out my flag file.

## Reading Manuals
This introduces us to manuals for various commands that we pass as arguements to the man command(if available)

### My solve
**Flag:** `pwn.college{Q--MnWZ3d_xDjYGV3Yj31x_-J2n.QX0EDO0wiM5gjNzEzW}`
I have been given the program called challenge anf I have to use the proper argument with it to print my flag. On reading the manual i found an argument
called "--ndxjjx NUM" and it was written that the flag will be printed if NUM=333. So i used the very same command but replaced NUM with 333 and my flag got printed.
```bash
hacker@man~reading-manuals:~$ /challenge/challenge --ndxjjx 333
Correct usage! Your flag: pwn.college{Q--MnWZ3d_xDjYGV3Yj31x_-J2n.QX0EDO0wiM5gjNzEzW}
```
### What I learnt
I learnt to read manuals of the commands and also infer data from it. I used a proper argument mentioned in the manual's description part, 
wrote the proper documentation and got my flag printed.

## Searching manuals
This challenge teaches us the various processes of searching a manual.
### My solve
**Flag:** `pwn.college{Yw6RYgBioFijGQXTvc64Vh2keaN.QX1EDO0wiM5gjNzEzW}`
In this challenge i was asked to search for the correct argument which which on passing on challenge program it would give me the flag. 
I searched for the word flag in the manual for challenge and found the required argument and then used the same argument to get the flag.
```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge  --wvlol
Initializing...
Correct usage! Your flag: pwn.college{Yw6RYgBioFijGQXTvc64Vh2keaN.QX1EDO0wiM5gjNzEzW}
```
### What I learned
I learned the procedure for searching for a specific word in the manual of a command.

## Searching for Manuals
This challenge gives us a searchable database where a huge number of manpages are hidden with random names. I have to search for my required manpage,
study it to find my required argument and then execute it to get the flag.
### My solve
**Flag:** `pwn.college{Iej2MazV8NrA4DZ-8dXxCwj4jcK.QX2EDO0wiM5gjNzEzW}`
I first used the man man command to get into the searchable data base. Studying it, I found that there is a command which i could use to search for man pages which
contain some specific word in them. I used that for searching related to flag and found a manpage which had the argument for printing the flag. I opened up the man page
and checked and found an argument --ejazrd NUM which would print the flag if NUM=284 so i simply went outside the man and write the argument changing NUM to 284 and 
the flag got printed.
```bash
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$  man -k flag
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
ejazrdxwjj (1)       - print the flag!
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking a...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity check...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking ...
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
hacker@man~searching-for-manuals:~$ man ejazrdxwjj
hacker@man~searching-for-manuals:~$ /challenge/challenge --ejazrd 284
Correct usage! Your flag: pwn.college{Iej2MazV8NrA4DZ-8dXxCwj4jcK.QX2EDO0wiM5gjNzEzW}
```
### What I learned
I learnt advanced usage of man command. I learnt and applied the use of the man command to search for specific manpage and then again searched for a specific argument
in a manpage to print my flag.

## Helpful programs
This challenge is about using the help argument in some programs which do nat have a man page. In this way they tell us how to perform a particular task using them.
### My solve
**Flag:** `pwn.college{oHCV6xtY8DTPi_gihEpc-SoiSwZ.QX3IDO0wiM5gjNzEzW}`
I was supposed to use the help argument on the challenge program. I did so and i got a list of arguments to pass for various functions. I saw a -p argument which would print some value to make the -g option print my flag i did so and found my required value i then passed the value into the -g argument to get the flag.
```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
-h, --help            show this help message and exit
--fortune             read your fortune
-v, --version         get the version number
-g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
-p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 683
hacker@man~helpful-programs:~$ /challenge/challenge -g 683
Correct usage! Your flag: pwn.college{oHCV6xtY8DTPi_gihEpc-SoiSwZ.QX3IDO0wiM5gjNzEzW}
```
### What I learned
I learned how to use the help argument in programs without the man page to get to know what to pass to get the job done.

## Help for Builtins
This  challenge tells us about Builtins which are essentially programs but instead of them having man pages or help options, they are built directly into the shell itself.
### My solve
**Flag:** `pwn.college{o-uZLGefWuaFPZIipNaFiCTgsd7.QX0ETO0wiM5gjNzEzW}`
I was told about the help argument which I could pass to the challenge command which was a builtin, rather than a program. I did so and found the value to pass into my required secret argument to print the flag.
```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "o-uZLGef".
hacker@man~help-for-builtins:~$ challenge --secret o-uZLGef
Correct! Here is your flag!
pwn.college{o-uZLGefWuaFPZIipNaFiCTgsd7.QX0ETO0wiM5gjNzEzW}
```
### What I learned
I learned about builtins and how to use help argument on builtins and used it to find the help options and print the flag by following the steps.











