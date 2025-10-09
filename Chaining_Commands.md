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
This challenge teaches about the && operator which is used to chain multiple commands together and executed the  second only if the first successfully runs.
### My solve
**Flag:** `pwn.college{4BsdByWdr3je9MP2ZEPsGrlQ2EX.0lM0MDOxwiM5gjNzEzW}`
```bash
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{4BsdByWdr3je9MP2ZEPsGrlQ2EX.0lM0MDOxwiM5gjNzEzW}
```
### What I learned
