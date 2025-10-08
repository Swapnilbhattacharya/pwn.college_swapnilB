# Perceiving Permissions
This challenge introduces us to the chown command which essentially stands for Change Owner, used for changing ownership rights of users on files.
### My solve
**Flag:** `pwn.college{EaiEcowCSsbwJuUsM3VADpwS8Z7.QXxEjN0wiM5gjNzEzW}`
I used the chown command on the /flag file to transfer its access rights to the hacker user(me) from the root. As, instructed i then read the flag file using cat.
```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{EaiEcowCSsbwJuUsM3VADpwS8Z7.QXxEjN0wiM5gjNzEzW}
```
### What I learned
I learned the chown command which is written as chown [user_name] [file]
I learnt that we can use the chown command while being in the root directory to change the access rights of files to other users.

# Groups and Files
This challenge introduces us to the chgrp command which can change the group whose members can access a particular file.
### My solve
**Flag:** `pwn.college{4YhMmY6uwYIgDhg20KTaUPoYvk-.QXxcjM1wiM5gjNzEzW}`
It was said that I would have to change the group which owns the file (currently root) to hacker so that I can read it. I used the chgrp command along with hacker and /flag as argument in order to change the owner group of the file to hacker and then i used cat to read the file.
```bash
hacker@permissions~groups-and-files:~$ ls -la /flag
-r--r----- 1 root root 60 Oct  8 19:43 /flag
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ /flag
bash: /flag: Permission denied
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{4YhMmY6uwYIgDhg20KTaUPoYvk-.QXxcjM1wiM5gjNzEzW}
```
### What I learned
I learned that only the users belonging to a particular specified group can access files. I learned how to use the chgrp command for changing the group which owns a file. In real cases these operations can only be done while being in the root directory.

# Fun with Groups names
This challenge is about finding out what group I am part of and then changing the owner group to that in order to find the flag.
### My solve
**Flag:** `pwn.college{AncnjvyzLp5xM1lLs1-5KavdX5X.QXycjM1wiM5gjNzEzW}`
I used the id command to list out the owner username and group. I saw that there was a randomly named group which had the rights to the flag file
I used chgrp to change the owner group of the flag file to that group. I then used the cat command to read the flag.
```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp13774) groups=1000(grp13774)
hacker@permissions~fun-with-groups-names:~$ chgrp grp13774 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{AncnjvyzLp5xM1lLs1-5KavdX5X.QXycjM1wiM5gjNzEzW}
```
### What I learned
I practised finding out my own groups using id and then changing the access rights group of a required file to one of my own groups to be able to read the file.



