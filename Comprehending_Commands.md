## Cat: Not the pet, but the command!
This challenge asks to obtain the flag using the cat command from a file named flag in the home directory.
### My solve
**Flag:** `pwn.college{c7XpX-E_r0Pvncc-iMGwmT_XRDR.QXxcTN0wiM5gjNzEzW}`
I simply used the cat command using ~/flag as the argument as it has been given that flag is a directory under home directory.

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat ~/flag
pwn.college{c7XpX-E_r0Pvncc-iMGwmT_XRDR.QXxcTN0wiM5gjNzEzW}
```
### What i learned
I learned about the cat command and its function that it simply prints the contents of the file given to it as an argument. It concatenates contents of multiple files if they are given as arguments.
