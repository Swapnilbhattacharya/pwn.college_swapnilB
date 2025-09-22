## Intro to Commands
The challenge asks to invoke my first command "hello" on Linux CLI.

## My solve
**Flag** `pwn.college{c-FG21u3EE9ZP0mE5z81sHAPNhT.QX3YjM1wiM5gjNzEzW}`

Here, the challenge gives an example to run the whoami command on the CLI, which prints my name. It asks me to run a command called "hello" based on the given example.

```
 hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{c-FG21u3EE9ZP0mE5z81sHAPNhT.QX3YjM1wiM5gjNzEzW}
```
## What I learned
I learnt the syntax to write basic commands on CLI.


##Intro to arguments
The challenge asks to run a command with a single argument.
## My solve
**flag** `pwn.college{4Ha7xfgasuJ3ELdRGjkqARexd4G.QX4YjM1wiM5gjNzEzW}`

Here, based on the example of the echo command used on 2 arguments "Hello"and"Hackers", I have used hello as a command on hackers as an argument.

```
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{4Ha7xfgasuJ3ELdRGjkqARexd4G.QX4YjM1wiM5gjNzEzW}
```
##What I learned
This taught me how to identify commands and arguments and how to use commands and arguments together on the Linux CLI.


##Command History
This challenge is about going through the saved log of previous commands on the CLI and using previously used saved commands to speed up work.

## My solve
**Flag:** `1hacker@hello~command-history:~$ the flag is pwn.college{8W-D5lg2QKdjXl_BtYQifn4DZfi.0lNzEzNxwiM5gjNzEzW}`

In this challenge the flag was hidden among some previously saved commands and I used the up arrow key to move up and find out the hidden flag from the history.
```
hacker@hello~command-history:~$ the flag is pwn.college{8W-D5lg2QKdjXl_BtYQifn4DZfi.0lNzEzNxwiM5gjNzEzW}
```
##What i learned
This challenge taught me to use up arrow key to navigate among previously used commands which would help me save time and effort by reusing already written command lines.

