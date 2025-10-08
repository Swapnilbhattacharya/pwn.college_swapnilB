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

# Changing Permissions
This challenge introduces us to the actual permissions given to files. We handle permissions using chmod command.
### My solve
**Flag:** `pwn.college{o1RTa1A1lN3u6emACtwbpaLlEic.QXzcjM1wiM5gjNzEzW}`
I am just a hacker user in the hacker group. The flag file here is only available to the root user belonging to the root group and on checking its permissions with ls -la command it could be seen that only the root user has permissions to read it. Since, I am an "other user", I decided to change the permissions to the file. I changed the other user permission and gave the read access. I used the chmod along with o+r arguemnt to do this. Then I directly used cat on the flag file and read the flag.
```bash
hacker@permissions~changing-permissions:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~changing-permissions:~$ ls -la /flag
-r-------- 1 root root 60 Oct  8 20:34 /flag
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{o1RTa1A1lN3u6emACtwbpaLlEic.QXzcjM1wiM5gjNzEzW}
```
### What I learned
I learned to use the chmod command to change the permissions to files according to our need but this only possible when in the root directory. 

# Executable files
This challenge teaches us to go further and tinker with the execution permissions of a file.
### My solve
**Flag:** `pwn.college{ckEm24L2NVuB9UlF5QHFFRc2sxU.QXyEjN0wiM5gjNzEzW}`
I first checked the permissions that the /chllenge/run file possesses using the ls -l command. I saw that the user hacker(me) is the owner of the file but as owner hacker did not have execution permissions of the file. I solved this by using the chmod command with the argument u+x with the file name which gave execution rights to the user. I then executed /challenge/run and got the flag.
```bash
hacker@permissions~executable-files:~$ ls -la /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{ckEm24L2NVuB9UlF5QHFFRc2sxU.QXyEjN0wiM5gjNzEzW}
```
### What I learned
I learned how to change the execution permissions of a file and read the flag.

# Permission Tweaking Practice
This challenge makes us practice all sorts of tweaks with file permissiong using chmod.
### My solve
**Flag:** `pwn.college{cYcTCV06O-1-xM6OxdhMuiw53h1.QXwEjN0wiM5gjNzEzW}`
This challenge gave me 8 levels in which I had to play around with the file permissions according to the instructions. I simply kept on using the chmod command on the /challenge/pwn file and kept on changing the arguments in between according to the requirements.
```bash
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrwxr--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+x,g+wx /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rwxrwxr--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrwxrwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+wx /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": rwxrwxrwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwxrwxr--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o-wx /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": rwxrwxr--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rw-r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-x,g-x /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": rw-rw-r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rwxr--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+x /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": rw-rwxr--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rwx---
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o-r /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": rw-rwx---
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rwx-wx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+wx /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": rw-rwx-wx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwxrwx-wx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+x /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{cYcTCV06O-1-xM6OxdhMuiw53h1.QXwEjN0wiM5gjNzEzW}
```
### What I learned
I practised various kinds of tweaks with the file permissions and tried to remember the commands thoroughly.

# Permissions Setting Practice
This challenge continues the previous challenge with a slight difference that we have to use = to directly set the permissions for user, group and other as per requirements.
### My solve
**Flag:** `pwn.college{on25Mv1pILtMT6pNiXtR_Db674j.QXzETO0wiM5gjNzEzW}`
This challenge gave me 8 levels in which I had to play around with the file permissions according to the instructions. I simply kept on using the chmod command on the /challenge/pwn file and kept on changing the arguments in between according to the requirements just by writing down the required combination using '='.
```bash
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwx---r--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=--- /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rwx---r--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w---xrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=x,o=rw /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": -w---xrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --x-wxrw-
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=wx,o=rw /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": --x-wxrw-
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxr----x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=r,o=x /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": rwxr----x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w----rwx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=-,o=rwx /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": -w----rwx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w-rw---x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rw,o=x /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": -w-rw---x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--r-x-w-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=rx,o=w /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": r--r-x-w-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w------x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=-,o=x /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{on25Mv1pILtMT6pNiXtR_Db674j.QXzETO0wiM5gjNzEzW}
```
### What I learned
I gained more practice on permissions of files and learnt to directly set the value of the permissions as per requirements using =.

# The SUID Bit
This challenge teaches us about the SUID bit and how it functions and how we can give that access to our files and how that helps.
### My solve
**Flag:** `pwn.college{sx4ISyjIua0URAGjsro1Ws89GIo.QXzEjN0wiM5gjNzEzW}`
I first checked what were the permissions that were available with /challenge/getroot. I then gave /challenge/getroot the SUID Bit access so that it could be run by any user on the system. I then ran the program and a root shell opened up. I then used cat to directly read the flag. To give the SUID Bit permission to /challenge/getroot I used the u+s argument with chmod so that it would give the user the SUID bit control to access the file.
```bash
hacker@permissions~the-suid-bit:~$ ls -la /challenge/getroot
-rwxr-xr-x 1 root root 155 Jan 14  2025 /challenge/getroot
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{sx4ISyjIua0URAGjsro1Ws89GIo.QXzEjN0wiM5gjNzEzW}
```
### What I learnt
I learnt about the SUID bit. I learnt that the s part in place of the executable bit means that the program is executable with SUID.
as in this example - `-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/sudo`
It means that, regardless of what user runs the program the program will execute as the owner user (in this case, the root user).




