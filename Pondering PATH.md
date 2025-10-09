# The PATH Variable
This challenge teaches us about the PATH variable which stores a bunch of paths in which the shell will search for programs corresponding to commands. It makes us empty out the PATH variable itself so that bash is unable to find the rm command.
### My solve
**Flag:** `pwn.college{IqohM6QyTYxZofVs_ofjqD6nKLl.QX2cDM1wiM5gjNzEzW}`
It's instructed that the /challenge/run program will try to delete the flag using the rm command. Hence, its clear that I cannot run it directly. I must somehow disrupt the bash from using the rm command. So, I set the shell's PATH variable to null so that all the paths that the bash had corresponding to the rm command gets deleted and it never finds out what the rm command is.
```bash
hacker@path~the-path-variable:~$ rm
rm: missing operand
Try 'rm --help' for more information.
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ rm
bash: rm: No such file or directory
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{IqohM6QyTYxZofVs_ofjqD6nKLl.QX2cDM1wiM5gjNzEzW}
```
### What I learned
I learnt about the special shell variable PATH which stores bunch of paths in which the shell will search for  programs corresponding to commands and learnt to remove it by assigning it to "" so that the paths are all lost.

# Setting PATH
This challenge teaches us to use the PATH variable for useful puposes. It makes us add a directory to the PATH variable.
### My solve
**Flag:** `pwn.college{QpLUWCCMvaqW820MN0OsSXhfgIX.QX1cjM1wiM5gjNzEzW}`
Instruction was that /challenge/run would run the win file which contained my flag. BUT, only by using its bare name. So, running /challenge/run directly would not be succesfull since it would never find the win command. We would have to set our PATH variable to the directory that contains the win file for this to be successful. I used the setting paths concept to assign /challenge/more_commands/ (directory containing the win file) to PATH. Thereby, I could use /challenge/run to make it run the win file directly with its bare name.
```bash
hacker@path~setting-path:~$ ls /challenge/more_commands
win
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{QpLUWCCMvaqW820MN0OsSXhfgIX.QX1cjM1wiM5gjNzEzW}
```  
### What I learned
I learned the concept of setting the PATH variable to any required path in order to run our files directly using their names as the commands without having to use their paths again and again.

# Finding Commands
This challenge teaches us about the which command which is used to find the exact path of the file of the various linux commands that we use for example: cat, ls, etc. 
### My solve
**Flag:** `pwn.college{4nymWt9VqHFGrmSIQJEE7o1KDfD.01NzEzNxwiM5gjNzEzW}`
We know, all the commands are also present somewhere or the other and "which" helps us find that. for example if we write which cat, it gives us the path to the cat file.
```bash
swapnil@Pavilion15:~$ which cat
/usr/bin/cat
```
This shows that the cat file is present in the bin directory of my usr directory.
In this challenge I used this which command to find out the path to the win file. It was said the win file was in the same directory as of my flag file which contained the flag. So, after finding the path to the win file I used the same path and changed win to flag in order to access my flag file with cat command.

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/22538/win
hacker@path~finding-commands:~$ cat /challenge/paths/22538/flag
pwn.college{4nymWt9VqHFGrmSIQJEE7o1KDfD.01NzEzNxwiM5gjNzEzW}
```
### What I learned
I learned about the which command which can be used to find the path of any command in linux. All these paths are stored in PATH variable and which helps us find the particular required paths from the PATH variable.

# Adding Commands
### My solve
**Flag:** ``
```bash
```
### What I learned

# Hijacking Commands
### My solve
**Flag:** ``
```bash
```
### What I learned
