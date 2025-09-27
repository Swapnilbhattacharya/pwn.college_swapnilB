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
This challenge teaches us to complete paths using globbed arguments.
### My solve
**Flag:** `pwn.college{AICMnSvuXsVX-xLI7CQh0rKpxjA.QX0IDO0wiM5gjNzEzW}`
I had been given a  bunch of files in /challenge/files and i was required to run the given command by writing the correct path to the files file_b, file_a, file_s, file_h but without writing the full file names and by using globbing techniques.
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{AICMnSvuXsVX-xLI7CQh0rKpxjA.QX0IDO0wiM5gjNzEzW}
```
### What I learned.
I learned how to use globbing for writing paths to files.

## Multiple Globs
This challenge teaches us to write multiple globs together to search for required files.
### My solve
**Flag:** `pwn.college{ovwH8UdqrntMnLI0gcw1HiE2lZx.0lM3kjNxwiM5gjNzEzW}`
I was given another bunch of files in the files directory and i was required to run the given command using a proper argument which would cover all files containing p. I used the * globbing tool to write the following bash command to find the flag.
```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{ovwH8UdqrntMnLI0gcw1HiE2lZx.0lM3kjNxwiM5gjNzEzW}
```
### What I learned
I learnt and practised how to write multiple globbing tools in the same argument and effectively searching for my required files.

## Mixing globs
This challenge brings together all globbing concepts and asks me to search for 3 specific files out of many in the files directory.
### My solve
**Flag:** `pwn.college{0vffwLHcH9JQAR3b-zLtOH6Z-cm.QX1IDO0wiM5gjNzEzW}`
I was required to search for file names "challenging","educational","pwning".  Thus I used the [] glob to ensure that the files i search for only begin with c,e or p and they can be followed by any alphabet. I could be sure that other files don't start with the same alphabets since I had checked all other file names prior to this by using the cd command.
```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{0vffwLHcH9JQAR3b-zLtOH6Z-cm.QX1IDO0wiM5gjNzEzW}
```
### What I learned
I learned how to use all kinds of globbing together to search for multiple file names.

## Exclusionary globbing
This challenge teaches us that globbing can not only be used to filter files out but can also be used to filter out files that we don't want.
### My solve
**Flag:** `pwn.college{krSozNb8YG6cZgogJPgjkGgjEjv.QX2IDO0wiM5gjNzEzW}`
I have been given a lot of files and i have to access those which don't start with p/w/n. I used ^ before the alphabets in the square brackets and excluded the characters.
```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{krSozNb8YG6cZgogJPgjkGgjEjv.QX2IDO0wiM5gjNzEzW}
```
### What I learned
I learned how to exclude unimportant alphabets and find the required files which don't contain those alphabets.

## Tab Completion
This teaches us that instead of using * or ? a better alternative is the <tab> key which specifies a target . It figures out what I am trying to type and self completes it.
### My solve
**Flag:** `pwn.college{sXSnwY3legPOs_4LAaV-U0MC4ox.0FN0EzNxwiM5gjNzEzW}`
I had been asked to print the flag which was there in /challenge/pwncollege. I can cat the file but not type the file name. So i wrote 'p' and used tab key to complete the file name and pressd enter.
```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{sXSnwY3legPOs_4LAaV-U0MC4ox.0FN0EzNxwiM5gjNzEzW}
```
### What I learned
I can easily make use of the <tab> key to enable automatic completion of the filename in a specific directory wthout having to use globbing tools.

## Multiple Options for Tab completion
This teaches us how to use tab globbing when there are more than one file beginning or having almost the same name.
By default bash auto-expands until the first point when there are multiple options.
### My solve
**Flag:** `pwn.college{IjLAwfmwKInl7hJLhLIKtfLrwOg.0lN0EzNxwiM5gjNzEzW}`
I used cd to get into the files directory and then used the cat command and used the tab key on 'p'. This printed pwn and on hitting enter I got a list of the files contained in files directory. Then i write the name of the required file and used the cat command to get the flag.
```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag
pwn.college{IjLAwfmwKInl7hJLhLIKtfLrwOg.0lN0EzNxwiM5gjNzEzW}
```
### What I learned
I learned how to use the tab globbing technique when there are multiple files of the same name.

## Tab completion on commands
This teaches us that we can use tab to even complete commands.
### My solve
**Flag:** `pwn.college{s9n-V_VkA6juphpSb4inNfiml7Z.0VN0EzNxwiM5gjNzEzW}`
I wrote the pwncollege command and pressed enter; the command completed itself. I pressed enter and the flag was printed
```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-32383
Correct! Here is your flag:
pwn.college{s9n-V_VkA6juphpSb4inNfiml7Z.0VN0EzNxwiM5gjNzEzW}
```
### What I learned
I learned that not only files but also commmands can be completed using the tab globbing.

