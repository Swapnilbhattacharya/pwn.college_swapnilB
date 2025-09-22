## The Root
This challenge is about invoking a program by providing its path on the command line

### My solve
**Flag:** `pwn.college{YsYN8hg6srrfh-Spw904DDS9s1a.QX4cTO0wiM5gjNzEzW}`
I was told that a program had been added to / (beginning from the root directory), so I entered the path of the program and invoked it.
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{YsYN8hg6srrfh-Spw904DDS9s1a.QX4cTO0wiM5gjNzEzW}
```
### What I learned
From this challenge, I learnt how to invoke a program by providing its exact path on the CLI.


## Program and absolute paths
This challenge is about invoking a program that is placed inside another directory, which in turn is placed inside the root directory.

### My solve
**Flag:** `pwn.college{4NgegTchVW5FGr8zTlVPpP1V2Qg.QX1QTN0wiM5gjNzEzW}`
I have been given a challenge directory, which is placed inside the root directory, and my "run" program is placed inside the challenge directory. Thus, I invoke the run program using its absolute path beginning with the root directory.
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{4NgegTchVW5FGr8zTlVPpP1V2Qg.QX1QTN0wiM5gjNzEzW}
```

### What I learned
From this challenge, I learnt how to invoke a program in a slightly complex location, i.e, which is placed inside another directory inside the root directory.



## Position thy self
This challenge asks to invoke the run program in the challenge directory but this time not directly from the root. It asks us to change our working directory to a specific directory inside which we have the challenge directory.

### My solve
**Flag:** `pwn.college{Aqb2v2iDhLaI3Es2uuFkyh1o4ay.QX2QTN0wiM5gjNzEzW}`
I tried invoking the run program in the challenge directory directly but it showed me that i am not in the right directory and also mentioned the path to the required file so i used cd to go into that file and then successfully invoked run program in challenge directory.

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/build-essential directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/share/build-essential
hacker@paths~position-thy-self:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Aqb2v2iDhLaI3Es2uuFkyh1o4ay.QX2QTN0wiM5gjNzEzW}
```
### What I learned
We need to always be in the proper location in order to pull out any file which is required. everytime it won't be in the root directory.

## Position Elsewhere
This challenge asks to invoke the run program in the challenge directory but this time not directly from the root. It asks us to change our working directory to a specific directory inside which we have the challenge directory.

### My solve
**Flag:** `pwn.college{YF2vdrsX6DYnqEwOhvIpXaiWQ8v.QX3QTN0wiM5gjNzEzW}`
I tried invoking the run program in the challenge directory directly but it showed me that i am not in the right directory and also mentioned the path to the required file so i used cd to go into that file and then successfully invoked run program in challenge directory.
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{YF2vdrsX6DYnqEwOhvIpXaiWQ8v.QX3QTN0wiM5gjNzEzW}
```
### What I learned
We need to always be in the proper location in order to pull out any file which is required. everytime it won't be in the root directory.

## Position yet elsewhere
### My solve
**Flag:** ``
```
```
### What I learned






