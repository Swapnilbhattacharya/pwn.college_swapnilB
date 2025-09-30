## Printing variables
This challenge teaches us about variables in Linux CLI.
### My solve                                                           
**Flag:** `pwn.college{kkODL42ZK-6GH4seQhC_FVydDWY.QX3UTN0wiM5gjNzEzW}`
I simply use the $ sign to print the given FLAG variable. 
```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{kkODL42ZK-6GH4seQhC_FVydDWY.QX3UTN0wiM5gjNzEzW}
```
### What I learned
I learned about variables and how to print their values and use them.


## Setting Variables
This challenge teaches us to set the values to variables.
### My solve
**Flag:** `pwn.college{ITKe-AT_OnZhRa3UeNIi22v_SaB.QX5UTN0wiM5gjNzEzW}`
I used assigned the value of the variable PWN to COLLEGE by using the = operator.
```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{ITKe-AT_OnZhRa3UeNIi22v_SaB.QX5UTN0wiM5gjNzEzW}
```
### What I learned
I learned the process to assign values to variables.


## Multi-word Variables
This challenge teaches us to set the values to variables but with spaces in between.(multi words)
### My solve
**Flag:** `pwn.college{4Qc71R5mqopXlF8PUM0tJQ8KWAA.QXwYTN0wiM5gjNzEzW}`
I used double quotes to assign a value with a space in between to the PWN variable.
```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4Qc71R5mqopXlF8PUM0tJQ8KWAA.QXwYTN0wiM5gjNzEzW}
```
### What I learned
I learned the process of using double quotes to assign values containing spaces into variables.


## Exporting variables
This teaches us about exporting variables so that they can be used by different shells also.
### My solve
**Flag:** `pwn.college{sYyfk69iNP7AziE1jyjhAW55bqQ.QXyYTN0wiM5gjNzEzW}`
I used the export command and set the value of PWN to COLLEGE and also set COLLEGE=PWN but did not export that. Then, I ran the /challenge/run program and found my flag.
```bash
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{sYyfk69iNP7AziE1jyjhAW55bqQ.QXyYTN0wiM5gjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```
### What I learned
I learned about how we can export variables in CLI so that other shells can also use those.


## Printing exported variables
### My solve
**Flag:** `pwn.college{43t99yX2GhWqodBbZc1prUAEr67.QX4UTN0wiM5gjNzEzW}`
I used the command env to print all environment variables in the shell and one of them was my flag.
```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=9edc31cde706f9a9620b7d6ab8dec3c28915c5cfb0dd1f8063c560c949ed873b
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{43t99yX2GhWqodBbZc1prUAEr67.QX4UTN0wiM5gjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```
### What I learned
I learned about the env commmand used to print all current environment variables and their values.

## Storing command output
This challenge teaches us about how to store command outputs directly into variables.
### My solve
**Flag:** `pwn.college{QWWkBy4Tbv4-if7RTwmtbmY1Yqj.QX1cDN1wiM5gjNzEzW}`
I used the = operator and the $ symbol to directly redirect the output of /challenge/run into the variable PWN.
```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ $PWN
bash: pwn.college{QWWkBy4Tbv4-if7RTwmtbmY1Yqj.QX1cDN1wiM5gjNzEzW}: command not found
```
### What I learned
I learned about how to  store command outputs into variables directly using the = operator. 


## Reading Input
This challenge teaches us how to read inputs to variables from the user.
### My solve
**Flag:** `pwn.college{UC5HLJR4ePq-uhc1cBYsqdKN_fp.QX4cTN0wiM5gjNzEzW}`
I used the read command with the variable name PWN as the argument which enables the user to input the desired value.
```bash
hacker@variables~reading-input:~$ echo $PWN

hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UC5HLJR4ePq-uhc1cBYsqdKN_fp.QX4cTN0wiM5gjNzEzW}
```
### What I learned
I learned about the read command which enables the user to enter a value of their choice into a variable.

## Reading Files
This challenge is about reading the output of a particular file into the stdin of the variable.
### My solve
**Flag:** `pwn.college{Ylkh7zxivDqXdQcSxBQcp23WUiH.QXwIDO0wiM5gjNzEzW}`
I used the read command on the variable PWN and used the < character to redirect the output of /challenge/read_me into the variable.
```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Ylkh7zxivDqXdQcSxBQcp23WUiH.QXwIDO0wiM5gjNzEzW}
```
### What I learned
I learned to apply the concepts of piping while reading values to variables and learnt that we can also read values to a variable not only from the user but also from the output of some program or file.









