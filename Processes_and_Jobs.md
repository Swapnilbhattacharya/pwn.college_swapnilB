## Listing processes
This challenge teaches us about the ps command which lists all the current working processes on the terminal.
### My solve
**Flag:** `pwn.college{QVDtAEoFvWuPB3Aic0e8BjXnQXF.QX4MDO0wiM5gjNzEzW}`
I was told that /challenge/run had been renamed to something else and that had been executed so that it would become a running process. I was required to print the running processes in my terminal and find out the renamed /challenge/run program and run it correctly in order to get the flag. I first directly used the ps command along with -ef as an argument in order to print "every" process and that too in a "full format", i.e it would print all the runnning processes along with all other details such as execution time etc. 
```bash
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 17:29 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep
root           7       1  0 17:29 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 17:29 ?        00:00:00 /challenge/7569-run-21121
root         135     132  0 17:29 ?        00:00:00 sleep 6h
hacker       137       0  0 17:29 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/s
hacker       143     137  0 17:29 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       152     143  0 17:29 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ ./challenge/7569-run-21121
bash: ./challenge/7569-run-21121: No such file or directory
hacker@processes~listing-processes:~$ cat /challenge/7569-run-21121
#!/opt/pwn.college/bash

if [ -z "$DOIT" ]
then
        export DOIT=yes
        exec -a $0 bash < $0
fi

echo "Yahaha, you found me! Here is your flag:"
cat /flag
echo "Now I will sleep for a while (so that you could find me with 'ps')."
sleep 6h
hacker@processes~listing-processes:~$ /challenge/7569-run-21121
Yahaha, you found me! Here is your flag:
pwn.college{QVDtAEoFvWuPB3Aic0e8BjXnQXF.QX4MDO0wiM5gjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```
### What I learned
I learned about the ps command and how we can find out ongoing processes in the shell and also the various arguments that can be passed along with the ps command for example the -e which is used for printing all the processes without any filter and also the -f command which is used for printing in full format. They can also be used together as -ef. Also, we can use 'a' to list processes for all users, 'x' to list processes that aren't running in a terminal, and 'u' for a "user-readable" output. These can be combined into a single argument "aux". Overall we can either use "ps -ef" or "ps -aux".

## Killing Processes
This challenge teaches us to terminate processes in LINUX using the kill command which can terminate a process based on its Process Identifier (PID).
### My solve
**Flag:** `pwn.college{IX9tZFQHlNgLmry64uylhdLgCcA.QXyQDO0wiM5gjNzEzW}`
I first used the ps -ef command in order to have a look at all the currently running processes. I manually found the /challenge/dont_run program running and used the kill command with its PID(137) as argument to terminate it. Now, I was free to run the /challenge/run program and i did that and found my flag. 
```bash
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 18:19 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep
root           8       1  0 18:19 ?        00:00:00 /run/dojo/bin/sleep 6h
root         136       1  0 18:19 ?        00:00:00 su -c /challenge/.launcher hacker
hacker       137     136  0 18:19 ?        00:00:00 /challenge/dont_run
hacker       138     137  0 18:19 ?        00:00:00 sleep 6h
hacker       140       0  0 18:19 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/s
hacker       146     140  0 18:19 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       155       0  0 18:20 pts/1    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/s
hacker       161     155  0 18:20 pts/1    00:00:00 /run/dojo/bin/bash --login
hacker       172     161  0 18:21 pts/1    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 137
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 18:19 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep
root           8       1  0 18:19 ?        00:00:00 /run/dojo/bin/sleep 6h
hacker       138       1  0 18:19 ?        00:00:00 sleep 6h
hacker       140       0  0 18:19 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/s
hacker       146     140  0 18:19 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       155       0  0 18:20 pts/1    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/s
hacker       161     155  0 18:20 pts/1    00:00:00 /run/dojo/bin/bash --login
hacker       173     161  0 18:21 pts/1    00:00:00 ps -ef
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{IX9tZFQHlNgLmry64uylhdLgCcA.QXyQDO0wiM5gjNzEzW}
```
### What I learned
I learned how to terminate programs in LINUX CLI using the kill command and that it is necessary to use it with its PID.

## Interrupting processes
This challenge teaches us to interrupt a process/ application waiting on input from the terminal end using a simple shortcut; ctrl+C.
### My solve
**Flag:** `pwn.college{8oF1GSIGRRVYRdLG5lftJ0_CQKi.QXzQDO0wiM5gjNzEzW}`
I run the /challenge/run program first and it was said that I will have to interrupt it using the shortcut so I did that. I pressed ctrl+C and the process got terminated and I got my flag.
```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{8oF1GSIGRRVYRdLG5lftJ0_CQKi.QXzQDO0wiM5gjNzEzW}
```
### What I learned
I learnt a keyboard shortcut to terminate any process running in the terminal at a time. This can be used to declutter my tarminal and prevent it from lagging or buffering.

## Killing Misbehaving processes
### My solve
### What I learned
