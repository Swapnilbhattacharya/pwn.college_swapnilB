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
This is a challenge which wants /challenge/run to run a bash script called win which would have the code to read the flag.
### My solve
**Flag:** `pwn.college{wz71UYX8Nl6h8OsD-LzihW3lg2T.QX2cjM1wiM5gjNzEzW}`
This challenge wanted me to create a script which reads the flag file. I had to use cat /flag inside the win bash script. I did that first. Now I had to give the user execution rights of win since /challenge/run would call win and run it to find the flag. I did that and then the only thing was to set the correct PATH variable for run command to find my script. I had to add the absolute path to my win script into the PATH variable to do this. I used export command in order to make PATH an environment variable and so that I am able to read or write to it. I then prepended my win's path to the PATH variable and then ran the /challenge/run and got the flag.
```bash
hacker@path~adding-commands:~$ nano /home/hacker/win
hacker@path~adding-commands:~$ cat /home/hacker/win
#!/bin/bash
cat /flag
hacker@path~adding-commands:~$ ls -la /home/hacker/win
-rw-r--r-- 1 hacker hacker 36 Oct  9 21:16 /home/hacker/win
hacker@path~adding-commands:~$ chmod u+x /home/hacker/win
hacker@path~adding-commands:~$ export PATH="/home/hacker:$PATH"
hacker@path~adding-commands:~$ which win
/home/hacker/win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{wz71UYX8Nl6h8OsD-LzihW3lg2T.QX2cjM1wiM5gjNzEzW}
```
### What I learned
I learned and practiced the concept of scipts. Also, I added my own path to the PATH variable in order to keep the rest of the PATH intact so that the other commands like cat keep running.

# Hijacking Commands
This challenge gives more practice with bash scripts along with tinkering with the PATH variable.
### My solve
**Flag:** `pwn.college{gyaLI0lBJ0mRUXKgOCK8Qksv_WS.QX3cjM1wiM5gjNzEzW}`
Just like in the first the challenge, the /challenge/run command will try to delete the flag using rm. Howeever, unlike the first one, this one will not print the flag automatically. Hence, clearly I need to create a bash script which reads my file and at the same time I have to fool /challenge/run to execute my bash script instead of the real rm command. I began with creating a bash script named rm. Of course, I need to fool the system into thinking that it is the real rm. I wrote the bash script and designed it to cat the flag out from the /flag variable and I edited the script using the nano editor. I then came to my main terminal where I first checked the permissions of the rm file I created as I had to make sure it was executable by me. I saw that It was already executable as I had used chmod in my previous attempt. I then went on to change the PATH variable(main portion). I exported the path variable and appended my own rm's absolute path into the variable as I had to make sure the system took my fake rm file as the real rm. I then confirmed my job was done with the which command which showed that my rm had been properly linked. I then ran /challenge/run and finally it gave me my flag.
```bash
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ ls -la rm
-rwxr--r-- 1 hacker hacker 22 Oct 10 13:53 rm
hacker@path~hijacking-commands:~$ cat rm
#!/bin/bash
cat /flag
hacker@path~hijacking-commands:~$ export PATH="/home/hacker:$PATH"
hacker@path~hijacking-commands:~$ which rm
/home/hacker/rm
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{gyaLI0lBJ0mRUXKgOCK8Qksv_WS.QX3cjM1wiM5gjNzEzW}
```
### What I learned
I practised more of bash scripts and also a little more of tinkering with PATH varibles.
