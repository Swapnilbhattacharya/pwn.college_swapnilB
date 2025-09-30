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
**Flag:** ``
I read the output of /challenge/run into the PWN variable using the $ sign.
```bash

```
### What I learned
I learned about how we can read the output of other files into a variable.


## Printing exported variables
### My solve
**Flag:** `pwn.college{43t99yX2GhWqodBbZc1prUAEr67.QX4UTN0wiM5gjNzEzW}`
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

## Storing command output
### My solve
**Flag:** `pwn.college{QWWkBy4Tbv4-if7RTwmtbmY1Yqj.QX1cDN1wiM5gjNzEzW}`
```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ $PWN
bash: pwn.college{QWWkBy4Tbv4-if7RTwmtbmY1Yqj.QX1cDN1wiM5gjNzEzW}: command not found
```
### What I learned



## Reading Input
### My solve
**Flag:** `pwn.college{UC5HLJR4ePq-uhc1cBYsqdKN_fp.QX4cTN0wiM5gjNzEzW}`
```bash
hacker@variables~reading-input:~$ echo $PWN

hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UC5HLJR4ePq-uhc1cBYsqdKN_fp.QX4cTN0wiM5gjNzEzW}
```
### What I learned

## Reading Files
### My solve
**Flag:** `pwn.college{Ylkh7zxivDqXdQcSxBQcp23WUiH.QXwIDO0wiM5gjNzEzW}`
```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Ylkh7zxivDqXdQcSxBQcp23WUiH.QXwIDO0wiM5gjNzEzW}
```
### What I learned









