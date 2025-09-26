## Matching with *
### My solve
**Flag:** `pwn.college{c0Ja_nUXKbsHbrny6nfF4xUXHrE.QXxIDO0wiM5gjNzEzW}`
```bash
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /chal*
You specified the path to 'cd' to in more than 4 characters. Disallowed!
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{c0Ja_nUXKbsHbrny6nfF4xUXHrE.QXxIDO0wiM5gjNzEzW}
```
### Mistake I made
### What I learned.

## Matching with ?
### My solve
**Flag:** `pwn.college{cJk1_bTSt3FArciXrLYJ9kKecpP.QXyIDO0wiM5gjNzEzW}`
```bash
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{cJk1_bTSt3FArciXrLYJ9kKecpP.QXyIDO0wiM5gjNzEzW}
```
### What I learned

## Matching with []
### My solve
**Flag:** `pwn.college{gAHXNv52iqf5eTYdIg7xkza_7Kl.QXzIDO0wiM5gjNzEzW}`
```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{gAHXNv52iqf5eTYdIg7xkza_7Kl.QXzIDO0wiM5gjNzEzW}
```
### What I learned

