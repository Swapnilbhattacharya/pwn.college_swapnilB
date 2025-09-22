## The Root
This challenge is about invoking a program by providing its path on the command line

## My solve
**Flag:** `pwn.college{YsYN8hg6srrfh-Spw904DDS9s1a.QX4cTO0wiM5gjNzEzW}`
I was told that a program had been added to / (beginning from the root directory), so I entered the path of the program and invoked it.
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{YsYN8hg6srrfh-Spw904DDS9s1a.QX4cTO0wiM5gjNzEzW}
```
## What I learned
From this challenge, I learnt how to invoke a program by providing its exact path on the CLI.


## Program and absolute paths
This challenge is about invoking a program that is placed inside another directory, which in turn is placed inside the root directory.

## My solve
**Flag:** `pwn.college{4NgegTchVW5FGr8zTlVPpP1V2Qg.QX1QTN0wiM5gjNzEzW}`
I have been given a challenge directory, which is placed inside the root directory, and my "run" program is placed inside the challenge directory. Thus, I invoke the run program using its absolute path beginning with the root directory.
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{4NgegTchVW5FGr8zTlVPpP1V2Qg.QX1QTN0wiM5gjNzEzW}
```

## What I learned
From this challenge, I learnt how to invoke a program in a slightly complex location, i.e, which is placed inside another directory inside the root directory.



## Position thy self
## My solve
**Flag:** ``
```
```
## What I learned




