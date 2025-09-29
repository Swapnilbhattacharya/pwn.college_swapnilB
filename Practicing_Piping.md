## Redirecting output
This challenge teaches us to redirect outputs (stdout) into a file.
### My solve
**Flag:** `pwn.college{g47MVMHDNfjrtCq2sq7xJ8AZRl1.QX0YTN0wiM5gjNzEzW}`
i had to write the word "PWN" to the  filename COLLEGE. So I used the > character and the echo command on PWN to do the required operation.
```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{g47MVMHDNfjrtCq2sq7xJ8AZRl1.QX0YTN0wiM5gjNzEzW}
```
### What I learned
I learnt to use the > character to transfer the stdout into required specific file.

## Redirecting more output
This challenge teaches us that we can also redirect the output of other commands also instead of echo. We can transfer the output of any program into any file of my choice.
### My solve
**Flag:** `pwn.college{40Mz1eJ-QVcnqxXKKGAOhDhRHGA.QX1YTN0wiM5gjNzEzW}`
I had to redirect the output of the /challenge/run program to the myflag file. I used the > character on /challenge/run as command and gave myflag as argument which did my job. 
```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{40Mz1eJ-QVcnqxXKKGAOhDhRHGA.QX1YTN0wiM5gjNzEzW}
```
### What I learned
I gained further understanding of the use of the > character and used it to redirect more complex outputs into other file.

## Appending output
This challenge teaches us to redirect multiple outputs of multiple commands into the same file by using the >> characters.
### My solve
**Flag:** `pwn.college{0lAfW8HEekhrKERraxYJ-HyIj9_.QX3ATO0wiM5gjNzEzW}`
I used the > key first to redirect the first part of the flag into the the-flag file and then again wrote the same commands but this time used the >> characters to transfer rest part of the flag into the file.
```bash
hacker@piping~appending-output:~$ /challenge/run > /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{0lAfW8HEekhrKERraxYJ-HyIj9_.QX3ATO0wiM5gjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```
### What I learned
I learned the use of >> to redirect multiple outputs to the same file without creating a new file for redirecting everytime.

## Redirecting errors
This challenge teaches us how to redirect outputs and errors using the FD numbers(File Description numbers). 
### My solve
**Flag:** `pwn.college{gla4J2NZT2cB9Ktt1dZUIuV0L97.QX3YTN0wiM5gjNzEzW}`
I was required to redirect the flag from /challenge/run into myflag file and the instructions(errors) into the instructions file. I used the normal > character to redirect the output and the 2> command to redirect the errors into the instructions file.
```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{gla4J2NZT2cB9Ktt1dZUIuV0L97.QX3YTN0wiM5gjNzEzW}
```
### What I learned
I learned the concept of File Descriptor numbers. How to use FD numbers to redirect errors and even outputs.

## Redirecting input
This challenge is about redirecting inputs using the < character.
### My solve
**Flag:** `pwn.college{8UqeCnmwRTffkjo5N-IsLyI-H4h.QXwcTN0wiM5gjNzEzW}`
I needed to first assign the value "COLLEGE" into the PWN file and then input the PWN file into the /challenge/run. I first used the output redirection technique to assign "COLLEGE" into PWN and then used the input redirection method to asssgn the PWN file as input to /challenge/run.
```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{8UqeCnmwRTffkjo5N-IsLyI-H4h.QXwcTN0wiM5gjNzEzW}
```
### What I learned
I learned how to use the input redirection technique to assgn files as inputs to other files.

## Grepping stored results
This challenge asks us to redirect the output of /challenge/run to /tmp/data.txt file and then use the grep command to search for the flag.
### My solve
**Flag:** `pwn.college{E4ssCGmAjk7h4HrXSp_6gsVXy1w.QX4EDO0wiM5gjNzEzW}` 
I first used the normal output redirection techniques (>) to redirect the entire output of the run program into the data file and then I used the grep command to search for pwn.college(beginning of each flag) inside the data.txt file.
```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{E4ssCGmAjk7h4HrXSp_6gsVXy1w.QX4EDO0wiM5gjNzEzW}
```
### What I learned
I practised the output redirection technique and revised the concept of using grep to search for something inside a file.

## Grepping live output
This challenge teaches us about the | (pipe character) which can directly link the output of the command on the left of the pipe to the input of the command on the right of the pipe.
### My solve
**Flag:** `pwn.college{8lxC1UVEqGIko81-58sJARjXoSa.QX5EDO0wiM5gjNzEzW}`
I was required to use the pipe operator (|) in order to directly find out the flag from the output of /challenge/run without having to store its output into a separate file directly. I ran the run program on the left of the | character and used the grep command to search for pwn.college on the right hand side of the | . This directly found my flag from the output and printed it.
```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{8lxC1UVEqGIko81-58sJARjXoSa.QX5EDO0wiM5gjNzEzW}
```
### What I learned
I learnt how to use the pipe operator which can directly link the output of the command on the left of the pipe to the input of the command on the right of the pipe.

## Grepping errors
This challenge teaches us about the >& command that redirects one file descriptor to another file descriptor.
### My solve
**Flag:** `pwn.college{QoHV-A3m_bvBhld3GOvwysxcafG.QX1ATO0wiM5gjNzEzW}`
I was required to find the flag from the standard error of the /challenge/run program but for finding the flag I had to use grep in order to search the flag in the error part but it wasn't possible to use the | command as it works only with stdout. So, I used the >& command to convert the stderr into stdout and then used thr pipe operator to grep for pwn.college.
```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{QoHV-A3m_bvBhld3GOvwysxcafG.QX1ATO0wiM5gjNzEzW}
```
### What I learned
I learned about the >& technique of redirecting one FD into another FD and learnt its use.

## Filtering with grep -v
This challenge teaches us about a special argument -v which when used with grep can modify it to search for only those sentenses which don't contain the specific word or phrase.
### My solve
**Flag:** `pwn.college{4jXUPNXI_td1gUlF_JYL0FfXxRS.0FOxEzNxwiM5gjNzEzW}`
I had to filter all decoy flags from the output of /challenge/run so I used th grep -v command to filter out all useless flags and my required flag was printed.
```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{4jXUPNXI_td1gUlF_JYL0FfXxRS.0FOxEzNxwiM5gjNzEzW}
```
### What I learned
I learnt to use the grep -v command which would help me to filter out all useless lines in a file and would print the lines without the mentioned word or phrase.

## Duplicating piped data with tee
### My solve
**Flag:** ``
```bash
```
### What I learned

## Process substitution for input
### My solve
**Flag:** ``
```bash
```
### What I learned

## Writing to multiple programs
### My solve
**Flag:** ``
```bash
```
### What I learned

## Split-piping stderr and stdout
### My solve
**Flag:** ``
```bash
```
### What I learned

## Named pipes
### My solve
**Flag:** ``
```bash
```
### What I learned
