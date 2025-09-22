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
This challenge asks to invoke the run program in the challenge directory but this time not directly from the root. It asks us to change our working directory to a specific directory inside which we have the challenge directory.

**Flag:** `pwn.college{IKZCamGb5V-fPwjhGg2GytG6D-Z.QX4QTN0wiM5gjNzEzW}`
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-yet-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{IKZCamGb5V-fPwjhGg2GytG6D-Z.QX4QTN0wiM5gjNzEzW}
```
### What I learned
We need to always be in the proper location in order to pull out any file which is required. everytime it won't be in the root directory.

## Implicit relative paths, from /
In this challenge it is asked to use relative path to invoke a program.
### My solve
I had to use a relative path so i first used cd and made my cwd as / (root) then i used relative path i.e challenge/run to invoke the run program.
**Flag:** `pwn.college{AWonsp6OFhPkmWARXic41YcH_pp.QX5QTN0wiM5gjNzEzW}`
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{AWonsp6OFhPkmWARXic41YcH_pp.QX5QTN0wiM5gjNzEzW}
```
### What I learned
I learned about relative paths and how to implement them.

## explicit relative paths, from /
This challenge asks to use a relative path to run program from root directory but by using an explicit relative path which uses a '.' in order to refer to the current working directory.

### My solve
I was required to use an explicit relative path to arrive at challenge/run so i set the current directory to / (root) and then used . to refer to the cwd and wrote the rest of the path as a relative path to run program present inside the challenge directory.
**Flag:** `pwn.college{o53ZG7eFEk1KqH7D-9EKpJB0zSz.QXwUTN0wiM5gjNzEzW}`
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{o53ZG7eFEk1KqH7D-9EKpJB0zSz.QXwUTN0wiM5gjNzEzW}
```
### What I learned
I learned about explicit relative paths and how to invoke a program or directory using relative path while referrring to the cwd using '.'

## implicit relative path
This challenge we invoke the run program from the challenge directory. We use . to refer to the cwd i.e the challenge directory
### My solve
I used cd command to go to the challenge directory as was instructed in the problem. After that I used the . to refer to the cwd and write the relative path to invoke run.
**Flag:** `pwn.college{s3L5AZAWtUyL4evcpfyI8ACcjh-.QXxUTN0wiM5gjNzEzW}`
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{s3L5AZAWtUyL4evcpfyI8ACcjh-.QXxUTN0wiM5gjNzEzW}
```
### What I learned
I learned that I can also invoke a program or directory from its parent directory by using '.' to refer to it.


## home sweet home
This challenge tells us that the flag will be written into any file we mention as an argument to /challenge/run and the argument must be 3 characters long.
### My solve
I used ~ to refer to home/swapnil directory (my home directory) and used /~ as my destination.
**Flag:** `pwn.college{c_pp7SRz1V5MkvSvBMXqtOsj2SC.QXzMDO0wiM5gjNzEzW}`
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/~
Writing the file to /home/hacker/~!
... and reading it back to you:
pwn.college{c_pp7SRz1V5MkvSvBMXqtOsj2SC.QXzMDO0wiM5gjNzEzW}
```
### What I learned
I learnt about the '~' short form and that it stands for my home directory. It makes it easier to refer again and again to my home directory.






