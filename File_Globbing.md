## Matching with *
This is the first kind of file globbing. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern
### My solve
**Flag:** `pwn.college{c0Ja_nUXKbsHbrny6nfF4xUXHrE.QXxIDO0wiM5gjNzEzW}`
I was told that i have to cd into the challenge directory but without using more then 4 characters in the argument. So i used the argument as /ch* and got my flag.
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
I had initially misinterpreted the questiona and used /chal*.
### What I learned.
I learned the process to use the * as a file globbing technique in order to reduce the time and efforts that are required in figuring out correct arguments.

## Matching with ?
This teaches about a similar file globbing technique like * but with a twist. It checks only a the particular character in the position you use it in.
### My solve
**Flag:** `pwn.college{cJk1_bTSt3FArciXrLYJ9kKecpP.QXyIDO0wiM5gjNzEzW}`
I was asked to cd into the challenge directory but without using the full command. I used the ? globbing in place of c anf l.
```bash
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{cJk1_bTSt3FArciXrLYJ9kKecpP.QXyIDO0wiM5gjNzEzW}
```
### What I learned
I learned about file globbing using ? and its properties.

## Matching with []
This kind of globbing is essentially a limited form of ? in which instead of the ? searching for all the alphabets, only those mentioned inside the [] are checked. 
### My solve
**Flag:** `pwn.college{gAHXNv52iqf5eTYdIg7xkza_7Kl.QXzIDO0wiM5gjNzEzW}`
I used the [] to search for the alphabets b,a,s,h and used the given commands and arguments accordingly to find the flag.
```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{gAHXNv52iqf5eTYdIg7xkza_7Kl.QXzIDO0wiM5gjNzEzW}
```
### What I learned
I learned about the [] globbing technique and how we can use it to limit our search for characters instead of using the ?.


## Matching paths with []
### My solve
**Flag:** `pwn.college{AICMnSvuXsVX-xLI7CQh0rKpxjA.QX0IDO0wiM5gjNzEzW}`
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{AICMnSvuXsVX-xLI7CQh0rKpxjA.QX0IDO0wiM5gjNzEzW}
```
### What I learned.

## Multiple Globs
### My solve
**Flag:** `pwn.college{ovwH8UdqrntMnLI0gcw1HiE2lZx.0lM3kjNxwiM5gjNzEzW}`
```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{ovwH8UdqrntMnLI0gcw1HiE2lZx.0lM3kjNxwiM5gjNzEzW}
```
### What I learned

## Mixing globs
### My solve
**Flag:** `pwn.college{0vffwLHcH9JQAR3b-zLtOH6Z-cm.QX1IDO0wiM5gjNzEzW}`
```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{0vffwLHcH9JQAR3b-zLtOH6Z-cm.QX1IDO0wiM5gjNzEzW}
```
### What I learned

## Exclusionary globbing
### My solve
**Flag:** `pwn.college{krSozNb8YG6cZgogJPgjkGgjEjv.QX2IDO0wiM5gjNzEzW}`
```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{krSozNb8YG6cZgogJPgjkGgjEjv.QX2IDO0wiM5gjNzEzW}
```
### What I learned

## Tab Completion
### My solve
**Flag:** `pwn.college{sXSnwY3legPOs_4LAaV-U0MC4ox.0FN0EzNxwiM5gjNzEzW}`
```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{sXSnwY3legPOs_4LAaV-U0MC4ox.0FN0EzNxwiM5gjNzEzW}
```
### What I learned

## Multiple Options for Tab completion
### My solve
**Flag:** `pwn.college{IjLAwfmwKInl7hJLhLIKtfLrwOg.0lN0EzNxwiM5gjNzEzW}`
```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag
pwn.college{IjLAwfmwKInl7hJLhLIKtfLrwOg.0lN0EzNxwiM5gjNzEzW}
```
### What I learned

## Tab completion on commands
### My solve
**Flag:** `pwn.college{s9n-V_VkA6juphpSb4inNfiml7Z.0VN0EzNxwiM5gjNzEzW}`
```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-32383
Correct! Here is your flag:
pwn.college{s9n-V_VkA6juphpSb4inNfiml7Z.0VN0EzNxwiM5gjNzEzW}
```
### What I learned


