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
### My solve
### What I learned
