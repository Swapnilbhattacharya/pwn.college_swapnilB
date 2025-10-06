## Translating_characters
This challenge teaches us to use the translate or tr command to exchange alphabets.
### My solve
**Flag:** `pwn.college{0WESyWMH-3-lHzEcoa9jYTgpdPi.01MxEzNxwiM5gjNzEzW}` 
According to the example provided I used the tr command in order to convert every alphabet into its opposite case by writing them sequencially as in the flag. 
I used the echo command along with piping in order to have the corrected flag printed in my terminal.
```bash
hacker@data~translating-characters:~$ /challenge/run
Your case-swapped flag:
PWN.COLLEGE{0wesYwmh-3-LhZeCOA9JytGPDpI.01mXeZnXWIm5GJnZeZw}
hacker@data~translating-characters:~$ echo PWN.COLLEGE{0wesYwmh-3-LhZeCOA9JytGPDpI.01mXeZnXWIm5GJnZeZw} | tr PWNCOLLEGEwesYwmhLhZeCAJytGPDpImXeZnXWImGJnZeZw pwncollegeWESyWMHlHzEcajYTgpdPiMxEzNxwiMgjNzEzW
pwn.college{0WESyWMH-3-lHzEcoa9jYTgpdPi.01MxEzNxwiM5gjNzEzW}
```
### What I learned
I learned about tr command which can be used to exchange alphabets in a particular output statement with the mentioned alphabets in the corresponding positions
in the given argument.

## Deleting characters
This challenge is about teaching us another use of tr(translate) command i.e it can also be used for deleting characters in a particular sentence.
### My solve
**Flag:** `pwn.college{w9MPCUHoKOvOLISgj-WJdYrrQ7N.0FNxEzNxwiM5gjNzEzW}`
I used the /challenge/run to print the flag but the flag had a lot of dummy characters specifically ^ and % so I used the echo command on the flag and piped it.
I then used the tr command along with -d as an argument in order to delete the specified characters (^ & %) written after it. 
```bash
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p^%w^n^%.^c%o^%l^l^%eg^e^%{%w^%9^%M^P%C^%U^%H%o^K%O^%vO%L%I^S^%g^j%-%W^%J%dY^%r^%r^Q^%7^N%.0%F%Nx%Ez^%Nx^%wi^%M5^g^jN^%z^%E^%z^W^%}
hacker@data~deleting-characters:~$ echo p^%w^n^%.^c%o^%l^l^%eg^e^%{%w^%9^%M^P%C^%U^%H%o^K%O^%vO%L%I^S^%g^j%-%W^%J%dY^%r^%r^Q^%7^N%.0%F%Nx%Ez^%Nx^%wi^%M5^g^jN^%z^%E^%z^W^%} | tr -d ^%
pwn.college{w9MPCUHoKOvOLISgj-WJdYrrQ7N.0FNxEzNxwiM5gjNzEzW}
```
### What I learned
I learned how to use the tr (translation) command in order to delete specific characters from a sentence.

## Deleting newlines
This challenge teaches us about how to use escape sequences in bash along with tr(translate) command. 
### My solve
**Flag:** `pwn.college{wSNRuP42853eDM1u7xt5g6qy7Dm.0VNxEzNxwiM5gjNzEzW}`
Here, if we want to add a newline or tab-space or any other escape sequence we can add it at the desired place by writing the command in the format:
tr <place at which newline is required> "\n" 
This will remove the specific character mentioned and transfer the rest of the sentence on the right hand side of it to the next line.
Similar we can also delete such escape sequences from our outputs by using the previously used -d argument. I did something similar to pipe the output of /challenge/run into tr command's input and used -d along with "\n" so that all the escaped newline characters get deleted.
```bash
hacker@data~deleting-newlines:~$ /challenge/run
Your line-split flag:
pwn
.co
ll
ege{
w
S
NR
u
P
42
853
e
D
M1u
7
xt5
g
6
q
y
7
D
m.0
V
N
x
E
zNxw
i
M5
g
jN
zEzW}

hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{wSNRuP42853eDM1u7xt5g6qy7Dm.0VNxEzNxwiM5gjNzEzW}
```
### What I learned
I learnt more variations of using tr command on my outputs. This time to add or delete escape sequences like \n or \t. Also, \\ is read as actual backslash.

I also tried out a self-experiment by writing the following command and got this output.
```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr { "\n"
Your line-split flag:
p
wn
.c
ol
l
e
ge

w
S
NRu
P
42853
e
DM
1
u
7
x
t5
g
6qy7D
m.0V
N
xE
zN
xw
i
M
5
g
jN
z
E
z
W
}
```
The output that it gave me confirmed my assertion mentioned above about inserting newline character in a sentence that the mentioned delimeter gets removed and a newline character is added after it.

## Extracting the first lines with Head
This challenge teaches about the head command which prints the first few lines of our output file.
### My solve
**Flag:** `pwn.college{w-T0uAHNd2Rm-dTp22JG2wg9vKr.0lNxEzNxwiM5gjNzEzW}`
I first learnt about how to read specific number of lines using the head command using the -n argument and then did the first pipe from /challenge/pwn and used head on the output to read 7 lines. I was further asked to pipe it into the input to /challenge/college and I used the pipe character once again to redirect into the /challenge/collge directory. 
```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{w-T0uAHNd2Rm-dTp22JG2wg9vKr.0lNxEzNxwiM5gjNzEzW}
```
### What I learned
I learnt about the head command used to read first few lines of the output and that it reads 10 lines by default. I also learnt how to read specific number of lines by using the -n as an argument along with head.

## Extracting specific sections of text

### My solve
### What I learned
