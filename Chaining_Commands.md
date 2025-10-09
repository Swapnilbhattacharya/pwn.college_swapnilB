# Chaining with semicolons
This challenge introduces us to the concept of chaining commands together. Previously we used to pipe the output of one command into the input of another command in the same line. Now, we learn about the concept of chaining by which we can run consecutive commands in the same line one after the other.
### My solve
**Flag:** `pwn.college{wUScEZYeS5LcNrH7D7xMXl2g7eX.QX1UDO0wiM5gjNzEzW}`
I had to run /challenge/pwn first and then /challenge/college right after that. Thus, instead of writing the two commands in different lines. I used the ';' to separate the two commands and write them on the same line.
```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{wUScEZYeS5LcNrH7D7xMXl2g7eX.QX1UDO0wiM5gjNzEzW}
```
### What I learned
I learned about the ';' operator in order to separate consecutive commands and write them on the same line.

# Building on Success
This challenge teaches about the && (AND) operator which is used to chain multiple commands together and it executes the  second only if the first successfully runs.
### My solve
**Flag:** `pwn.college{4BsdByWdr3je9MP2ZEPsGrlQ2EX.0lM0MDOxwiM5gjNzEzW}`
I had to run /challenge/first-success first and then /challenge/second. I used the && operator to separate the two and run them one by one in the same line.
```bash
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{4BsdByWdr3je9MP2ZEPsGrlQ2EX.0lM0MDOxwiM5gjNzEzW}
```
### What I learned
I learnt that the && operator can be used to chain commands and execute them in such a way that the second is only executed if the first runs successfully.

# Handling Failure
This challenge introduces the || (OR) operator which is again a similar chaining technique but opposite to AND. It only executes the second command if the first command fails. i.e either the first one will run (OR) the second one.
### My solve
**Flag:** `pwn.college{4tzsMlCqC7pTiiETlR4ShXzVmNb.01M0MDOxwiM5gjNzEzW}`
I used the || command in between the first-failure file and the second file as instructed.
```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{4tzsMlCqC7pTiiETlR4ShXzVmNb.01M0MDOxwiM5gjNzEzW}
```
### What I learned
I learned that the || (OR) operator can be used to chain commands and when it is used, the second command executes only when the first command fails to execute.

# Your First Shell Script
This challenge teaches us to write shell scripts. Basically, store the commands to be ran in order inside a file and simply run the file at the end instead of making things complicated by running them one by one.
### My solve
**Flag:** `pwn.college{gO04M03dPLkHPIezDYSpaKJn7dJ.QXxcDO0wiM5gjNzEzW}`
I used the piping technique i.e transferred the output by using echo on both programs and used the '>' character to transfer the output into the file named x.sh. I then simply ran the file x.sh using the bash command and got my flag. Only things I got wrong was that I forgot to use the '>>' on the seccond program as a result of which I ended up overwriting the first output.
```bash
hacker@chaining~your-first-shell-script:~$ echo /challenge/pwn > x.sh && echo /challenge/college >> x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{gO04M03dPLkHPIezDYSpaKJn7dJ.QXxcDO0wiM5gjNzEzW}
```
### What I learned
I learnt about how to chain commands by creating a shell script and putting together all consecutive commands in order to execute them all at once.

# Redirecting Script Output
This challenge is about redircting the output of multiple commands into a single file using shell script.

### My solve
**Flag:** `pwn.college{gt6m8g2mce1N0rNXjswDupUuE1q.QX4ETO0wiM5gjNzEzW}`
This can be done by writing the shell script. I made a shell script and wrote the two commands into it. I then piped its output (bash x.sh) using | (pipe) into the file called /challenge/solve. 
```bash
hacker@chaining~redirecting-script-output:~$ echo /challenge/pwn > x.sh && echo /challenge/college >> x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{gt6m8g2mce1N0rNXjswDupUuE1q.QX4ETO0wiM5gjNzEzW}
```

### What I learned
I learnt about how we can pipe the output of the shell script into any file and it behaves exactly as a normal file.

# Executable Shell scripts
This challenge is about making an executable shell script which will not require running with bash. 
### My solve
**Flag:** `pwn.college{8gGpDMgwIWGfosUWG0YfQgFQCIN.QX0cjM1wiM5gjNzEzW}`
I was told to make a shell script which would invoke the /challenge/solve command and I had to make it executable by the user. Firstly, I used the echo command on the /challenge/solve and redirected the output into the x.sh shell script. I then checked the permissions of the shell script using ls -la command and then used chmod (change mode) command in order to change the user permissions of the file and gave the user execution rights. I then simply used its relative path to run the x.sh file to get the flag.
```bash
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > x.sh
hacker@chaining~executable-shell-scripts:~$ ls -la x.sh
-rw-r--r-- 1 hacker hacker 17 Oct  9 17:22 x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x x.sh
hacker@chaining~executable-shell-scripts:~$ /x.sh
bash: /x.sh: No such file or directory
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{8gGpDMgwIWGfosUWG0YfQgFQCIN.QX0cjM1wiM5gjNzEzW}
```
### What I learned
I learnt that we can simply run the shell script without everytime using the bash command using just its path. This can only be done if the user has execution permissions to the shell script file.

# Understanding Shebangs
This challenge teaches us about shebangs-specific lines which indicate what type of a file that is.
### My solve
**Flag:** `pwn.college{cv9vEgZesymEGEJAij95j7TCuPQ.0VOzMDOxwiM5gjNzEzW}`
I used to nano command to open up my script file in the nano text editor. I wrote the shebang for bash script in the first line and then in the next line wrote the required echo command with proper text "hack the planet" then I saved the file using ctrl+o and pressed enter. Then pressed ctrl+x to come back to the terminal. i then checked whether the file had proper execution permissions or not. It did not. I then used the chmod command to authorise the user with the execution command. Finally i used /challenge/run to check whether the work was correct. That gave me the flag.
```bash
hacker@chaining~understanding-shebangs:~$ nano /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ ls -la /home/hacker/solve.sh
-rw-r--r-- 1 hacker hacker 35 Oct  9 19:17 /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ chmod u+x /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{cv9vEgZesymEGEJAij95j7TCuPQ.0VOzMDOxwiM5gjNzEzW}
```
### What I learned
I learned about shebangs and how they when present on the very first line of the script file and helps the terminal identify it as a shell script file. I learnt to use the nano editor to directly edit the script files without having to use echo and other commands.

# Scripting with arguments
This challenge teaches us to use variables in the scripts. Basically, make the script work with arguments.
### My solve
**Flag:** `pwn.college{gfSQEbSYpKcnpiOEyWu107C4W45.0VNzMDOxwiM5gjNzEzW}`
I again opened the script in nano editor and wrote the required shebang line for a bash script. I then used two variables $1 and $2 which would get assigned to the two arguemnts respectively entered by the user. Then I wrote the echo command on both the variables in reverse order. Then I saved and closed the file editor, checked with the execution permissions and they were in place as I had already given the permission in the previous challenge. Then I directly ran the file to check the answer and used /challenge/flag which checked my work and gave me the flag.
```bash
hacker@chaining~scripting-with-arguments:~$ nano /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ cat /home/hacker/solve.sh
#!/bin/bash
first_argument=$1
second_argument=$2
echo "$2 $1"
hacker@chaining~scripting-with-arguments:~$ ls -la /home/hacker/solve.sh
-rwxr--r-- 1 hacker hacker 69 Oct  9 19:34 /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{gfSQEbSYpKcnpiOEyWu107C4W45.0VNzMDOxwiM5gjNzEzW}
```
### What I learned
I learnt how to use variables to make the bash script work with arguments.

# Scripting with Conditionals
This challenge teaches us to use if conditional statements in our bash scripts.
### My solve
**Flag:** `pwn.college{wyodQdrt2VocIgzsDjdyQnuRLyU.0lNzMDOxwiM5gjNzEzW}`
This challenge required my bash script to print college with pwn as an argument and nothing with any other word as argument. I used the nano editor again for writing down the code. I checked and set the coreect execution permissions for the script file and then tested it with pwn anf it printed college and with other words it printed nothing. Thus, my code was correct. I ran /challenge/run and got my flag.
```bash
hacker@chaining~scripting-with-conditionals:~$ nano /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ cat /home/hacker/solve.sh
#!/bin/bash
arg="$1"

if [ "$arg" = "pwn" ]
then
  echo "college"
fi
hacker@chaining~scripting-with-default-cases:~$ ls -l /home/hacker/solve.sh
-rw-r--r-- 1 hacker hacker 78 Oct  9 20:20 /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ chmod u+x /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /home/hacker/solve.sh random
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{wyodQdrt2VocIgzsDjdyQnuRLyU.0lNzMDOxwiM5gjNzEzW}
```
### What I learned 
I learnt to use if conditions in script files in bash. I learnt about the specific syntax and the required spaces before and after square brackets and how then and fi are used instead of brackets unlike other programming languages.

# Scripting with default cases
This challenge teaches us to use else conditions along with if conditions in out script files.
### My solve
**Flag:** `pwn.college{EkfuiLowFC0iE3vz_-A58k91SP6.01NzMDOxwiM5gjNzEzW}`
This challenge required my bash script to print college with pwn as an argument and the word nope with any other word as argument. I used the nano editor again for writing down the code. I checked and set the coreect execution permissions for the script file and then tested it with pwn and it printed college and with other words it printed nope. Thus, my code was correct. I ran /challenge/run and got my flag.
```bash
hacker@chaining~scripting-with-default-cases:~$ nano /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ cat /home/hacker/solve.sh
#!/bin/bash
arg="$1"

if [ "$arg" = "pwn" ]
then
  echo "college"
else
  echo "nope"
fi
hacker@chaining~scripting-with-default-cases:~$ ls -l /home/hacker/solve.sh
-rw-r--r-- 1 hacker hacker 78 Oct  9 20:20 /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ chmod u+x /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ ls -la /home/hacker/solve.sh
-rwxr--r-- 1 hacker hacker 78 Oct  9 20:20 /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ /home/hacker/solve.sh random
nope
hacker@chaining~scripting-with-default-cases:~$ /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{EkfuiLowFC0iE3vz_-A58k91SP6.01NzMDOxwiM5gjNzEzW}
```
### What I learned
I practised to use if conditions in script files in bash along with else condition. I learnt about the specific syntax and the required spaces before and after square brackets and how then and fi are used instead of brackets unlike other programming languages.

# Scripting with multiple conditions
This challenge teaches us to use else if ladder in out script files.
### My solve
**Flag:** `pwn.college{8FdooU_Q9mMolPGHE6RsZLgOrnz.0FOzMDOxwiM5gjNzEzW}`
This challenge required my bash script to print college with pwn as an argument, the planet with hack and linux with learn and the word unknown with any other word as argument. I used the nano editor again for writing down the code. I used if else ladder in correct syntax. I checked and set the coreect execution permissions for the script file and then tested it with pwn and it printed college and with other words it printed nope. Thus, my code was correct. I ran /challenge/run and got my flag.
```bash
hacker@chaining~scripting-with-multiple-conditions:~$ nano /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ cat /home/hacker/solve.sh
#!/bin/bash
arg="$1"

if [ "$arg" = "hack" ]
then
  echo "the planet"
elif [ "$arg" = "pwn" ]
then
  echo "college"
elif [ "$arg" = "learn" ]
then
  echo "linux"
else
  echo "unknown"
fi
hacker@chaining~scripting-with-multiple-conditions:~$ /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-multiple-conditions:~$ /home/hacker/solve.sh learn
linux
hacker@chaining~scripting-with-multiple-conditions:~$ /home/hacker/solve.sh hack
the planet
hacker@chaining~scripting-with-multiple-conditions:~$ /home/hacker/solve.sh hello
unknown
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{8FdooU_Q9mMolPGHE6RsZLgOrnz.0FOzMDOxwiM5gjNzEzW}
```
### What I learned
I learned the if else ladder with multiple conditions using the elif then statements in bash scripts and used it.

# Reading shell scripts
This challenge just tells us that we can use the cat command to read script files.
### My solve
**Flag:** `pwn.college{AnhqzuOoWrt5Vz2tXeQqVZka-vT.0lMwgDOxwiM5gjNzEzW}`
I used cat on /challenge/run and found an if-else condition there and it said if the input is "hack the PLANET" it would print the flag. That was the password!!!
I just ran the /challenge/run program and entered the password and got the flag.
```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{AnhqzuOoWrt5Vz2tXeQqVZka-vT.0lMwgDOxwiM5gjNzEzW}
```
### What I learned
I used cat to read out the /challenge/run file and learnt that we can do this reading process with all other scripts.





























