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
This challenge teaches us to use the cut command for grabbing specific columns of data.
### My solve
**Flag:** `pwn.college{opCbdzOCcm_K56PdtK2SbmTv0CG.01NxEzNxwiM5gjNzEzW}`
This challenge tells us to use the cut command on the output of the /challenge/run program and find out the flag. I followed the instructions and normally used the piping technique and then used the cut command with the delimeter(-d) set to " "(space) and then the -f(field number) set to 2 since according to the output of the /challenge/run we need to cut out the second column. We, further redirect this output into the input of tr -d "\n" in order to remove the newline characters from it to get the proper complete flag.
```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{opCbdzOCcm_K56PdtK2SbmTv0CG.01NxEzNxwiM5gjNzEzW}
```
### What I learned
i learned about the cut command and how to use it to cut out a specific column from any output. 

## Sorting data
This challenge teaches us about the sort command which helps to sort and organize data as per our requirement.
### My solve 
**Flag:** `pwn.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzEzW}`
This challenge wanted me to sort the contents of flag.txt kept in the challenge directory alphabetically so that the last flag in the list turns out to be the correct one. I followed instructions and wrote the sort command on /challenge/flags.txt as the argument. It gave me a huge list of flags out of which last one is the real flag.(as instructed).
```bash
hacker@data~sorting-data:~$ sort /challenge/flags.txt
ovm.colldge{Uecmcbf8j9wq9HAiMnV8Y6knS6A.0FM0LDOxwiL4gjMzEyW}
ovn.bnlkdge{Tedmcbf9j9wq9IAjLnV8Z5knS6A.0FL0MDOxwiM4fjNzEzV}
ovn.boklege{Uecmbcf9k8wp9IAjMoU8Y6joT6A.0FM0MDOxwiL5gjMzDzW}
ovn.bollege{Tdcmccf9k9wq9IAiLoU7Y5koT5A.0EM0LDOxviM5gjNyDzW}
ovn.cnllege{Tecmccf9k9wp9HAiMnV7Z6koT6A.0FL0MDOxviL5fjNyEyV}
ovn.coklefe{Uddmcbf9k9vq9IAjMoU8Z5joS6A.0EM0MCNxwiM5giNyEzV}
ovn.collefe{Tedmccf8k9wq9IAjLnV8Z6joS5A.0FM0MCNxviM5gjNzDzV}
owm.bollege{Uddlccf9k9wp9IAjLoU8Z5knT6A.0EM0MDOxwiM5giNyEyW}
owm.cokldfe{Uddmccf9j9wq9HAjLnV8Z6koS6A.0EM0LDOwwhL4gjNzDyW}
owm.coklegd{Uddmccf9j9wq9IAjMoV8Z6koT6A.0FM0MDOxwhL4fjNzEzV}
own.bnllefd{Uedlbbf9k9vp8IAiMnU7Z6knS6A.0FM0MDOxwiM4giNyEzW}
own.bollege{Uedmcbe8k9wq8IAjMnV8Z6joS6A.0FM0MDOxwiM5fiNzDzW}
own.cnllefd{Uddmccf9j9wp9IAjMoU8Z5koT6A.0FM0MCOxwiL4gjNzEyV}
own.cnllege{Tecmbcf9k9wq9IAiMoV7Z6koT6A.0EL0MDNxwiL5gjNzEzW}
own.colkege{Uedmbcf8k9wq9IAjMoV8Z6koT6A.0FM0MCOxwiM5gjNzEzW}
own.collegd{Tdclbcf9j9wq9IAiMoV8Z5joT6A.0EL0LDNwwiL4gjNzEzV}
own.college{Tddmcce9j9wq9HAiMoU8Z6koT6A.0FL0MDOxwiM5gjNzDyW}
own.college{Uddmcbf8k9wp9IAjMoV8Z6koS6A.0FM0MCOxviM5gjNzEzV}
own.college{Uddmcbf9j9wq8HAjMnV7Z6joS6A.0FL0MDOxwiM4fiMzEzW}
own.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzEzW}
pvm.boklege{Tddmccf9k8wq8IAiLnV8Z6jnT6A.0EM0MDOwwhM5fjNzEzW}
pvm.bollege{Uedmcbf8k9wq9IAjMoV7Z6knT5A.0FM0MDOxwiM5gjNzEzW}
pvm.cokkege{Tedmbbe9k9vq9HAjMnV8Z6koS5A.0FL0MDNxviM4fjNyEyV}
pvm.cokkege{Uddlbcf8k9vq9IAjMoV8Z6koT6A.0FL0MDOxwhL5fjNzEzW}
pvm.colldge{Tedlbcf9k8wq8HAjMoV8Z6joS5A.0EM0MDOwvhL4gjMzEyW}
pvn.bnkkdgd{Tedmcbe8k8wq9IAiLoU7Z6koT6A.0EM0LDNwwhM5giMzDzW}
pvn.bollefe{Tecmccf9k9wq9HAjMoV7Y5koS6A.0FM0MDOxwiM5gjNyEzW}
pvn.cokkdfe{Tedmbbf9k8wq9IAiMoU8Y5koS6A.0FM0LDNxwiL5gjNzEzW}
pvn.cokkdge{Uedmcce9k9wq9IAiMnV7Y5knT6A.0EM0MDNxviL4giNyDzW}
pvn.cokkege{Uedmccf9k9vq9IAjMoV7Z6koT5A.0EM0MDOxwiM5gjNzEzW}
pvn.cokldge{Uedmccf9k9wq9IAjMoV7Z6knT6A.0FM0MDOxviM5gjNyEzV}
pvn.coklegd{Uecmbbe9k8vq9HAjLoV8Y6koT6A.0FM0MDOwwhL4giNzDzW}
pvn.colkdge{Uedmcce9k8wq9IAjMoV8Y6koT6A.0FM0MCOxwiM5fjNyEzW}
pvn.colkefd{Uedmbbe9k8wq9HAiMoV8Z6koT6A.0EL0LDOxwhM5gjNzEzW}
pvn.colldgd{Uedlbbf9j9wp9IAjMoV8Y6knT5A.0EM0LDOxwiM5gjNzEzV}
pvn.collefe{Uedmccf9k9wq9IAjMoU8Y6koT6A.0FM0MDOxwiL5gjNzEzW}
pvn.collegd{Uedmccf9j8vq9HAiLnU8Z6koT6A.0EM0MDNxwiM5gjMzDzW}
pvn.college{Uedlbcf9k8wq9HAjLoV8Z6knT6A.0FM0MDOwwhM5gjNzEzV}
pwm.boklefe{Ueclcbf9j9wp9HAiLnV7Y5koS6A.0FL0MCNxwiM5gjNzDzV}
pwm.boklegd{Uecmcbf8j9wq9IAjMoU8Z6jnT5A.0FM0MDOwwiL5gjNyEzV}
pwm.boklege{Udclbcf8k9wq9HAjLnV8Y5jnT6A.0EM0LCOxviM5gjMyEzW}
pwm.bolldfd{Uedmbcf9k9wq9HAiLoV7Z5jnT6A.0EM0MDOxwhM5giNyEzV}
pwm.bollege{Uedlccf9k8wq9IAiMoU8Z6joT5A.0EM0MDOxvhL5fjNzEzW}
pwm.cnklegd{Tecmccf8k9wq8IAiMoU8Z6koT6A.0EM0MDOxviL5gjNzEyV}
pwm.cnklege{Tddmccf9k8wp8IAjMoU7Z5knT5A.0EM0LDNxwiL5gjMzEzW}
pwm.cnklege{Uedmcce9k8vq8IAjMoV7Y6koS5A.0FM0MDOxviL5gjNyDyW}
pwm.cnlkege{Uedlbbe9k9wq9HAiLoV8Y5knT6A.0EM0LDOxwiM5fjNzDzW}
pwm.colkdgd{Uddlccf9k8wp9IAjMoV8Z6koT5A.0EM0LCOwwiM5gjNyEzV}
pwm.colldfd{Tdcmcce9k8vq9IAjLnV8Z6jnS6A.0FL0LCNxviM5gjNzDyW}
pwm.college{Tedmccf9k9wq9IAjMoV8Y6koS6A.0FM0MDOxwiM5gjNzEzW}
pwm.college{Uddmcbe9k9vp9HAiMnV8Z6koS6A.0FM0MCOxwiL5gjNzEzV}
pwm.college{Uedmcbf9k8wq9IAjMoV8Z6koS6A.0FM0MDOxwiM5gjNzEzW}
pwm.college{Uedmccf9k9wq9IAjMnU8Z6koT6A.0FL0MDOxwiM5gjNzDzW}
pwm.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxviM5gjNzEzW}
pwn.bnkldge{Tedmcbf8k9wq8IAjMnU8Y6koS6A.0EM0MDOxvhM5fiNzDzW}
pwn.bnlkefe{Uddlcbe9j9wq9IAjMoU8Z5knS6A.0EM0MCOxwiM4gjNyEzV}
pwn.bnlkege{Uedmbbf8k8wp9IAjMoV7Y5joT5A.0FL0MDOxwiM4fjNzDzV}
pwn.bokldfd{Uedmbbe8j9vq9IAjLoV8Z5jnT6A.0FL0LDOxwiM5fjMzEzW}
pwn.bolkdge{Uddmbbf9k9wq8IAiMoV8Y6knT6A.0EM0MCNwwiL4gjMyEzW}
pwn.bolkefe{Uedmccf9k9wq9IAjMnV8Z6koT6A.0EM0MDOxwhM5gjMzEzW}
pwn.bolkege{Uedlbbf9j8wq9IAiLoV7Z6koS6A.0FM0MDOxwiM4giMzEzV}
pwn.bolldfe{Uecmbcf8k8wq8IAjMnU7Z6koS5A.0FM0MDNwwhM4fiNzDzW}
pwn.bolldgd{Uedmcbe9k9vp9IAjMoV8Y5koT6A.0FL0MDOxwiM4gjNzEzV}
pwn.bolldge{Uedmcce9k8wq9IAjMnV8Z6koT6A.0FM0MDOxwiM5gjNzDzV}
pwn.bollege{Uecmcce9k9wq8HAjMoV8Z6koT6A.0FM0LDOwwiM5giNzEzV}
pwn.bollege{Uedmbce9k9wp8IAjMoV7Z5knT6A.0FM0MDOxwiM5gjNyEzW}
pwn.cnkkegd{Uddlcbf8k9wq9IAjMnU8Z6joT6A.0FL0MDOxwiM5gjMzEyV}
pwn.cnklefd{Tedmccf9k9wq9IAjMnV8Z6koT6A.0EM0MDOxwhM4gjNyEyW}
pwn.cnklege{Uedmccf8k9wq9IAjMoV8Z6jnT6A.0EL0MDOxviM5giNzDzW}
pwn.cnlkegd{Uddmccf9k8wq8HAjMoV8Y6joT6A.0FM0MDOxwiM5gjNzEzW}
pwn.cnlkege{Tddmccf8k9wp9HAjLnV7Z6joS5A.0FM0LCOxwiL5gjNyEzW}
pwn.cnlldge{Tedmccf9j8wq9HAiMoV7Y6knT5A.0FL0MDOxviM5giNzDzV}
pwn.cnlldge{Uedlccf9k9wq9IAjLoV7Z6joS5A.0EM0MDOxviM5gjNyEzW}
pwn.cnllegd{Udcmcbf8k8vq8IAiLnU7Y5joS6A.0EM0LCOxwiM5fjNzEzV}
pwn.cnllege{Uecmccf9k8wq8IAjMoV8Y6knT6A.0FM0MCOxwhL4gjMzEzW}
pwn.cnllege{Uedmccf9k9wq9IAjLoU7Z6koS5A.0FM0MDOwwhM5fjNzEzW}
pwn.cokkdge{Tecmcbf9k8vq9IAjMoV8Z6koS6A.0FM0MCOxwhM4giNzEzW}
pwn.cokldfd{Tecmcce9k8vp9HAiMoV8Z6joT6A.0FL0MCOxviM5fjNyDyW}
pwn.cokldge{Uedmcbf8j9wq9IAiMoU8Z6koT6A.0FL0MDNxwiL5giNzEzV}
pwn.colkege{Uedmccf9k9wq9IAjMoV8Y6koT6A.0FM0MDOxwiM5gjNzEzW}
pwn.colldge{Uedmccf9k9wq9IAjMoV8Y6koT5A.0FM0MDOxwiM5fiNzEzV}
pwn.collefd{Uedlbcf8k8wq8HAjMnV8Z6koT6A.0FL0MCOxwiM5gjNyEzW}
pwn.collefe{Tedmbcf9k9wp9IAjMoV7Z6koT6A.0EM0MDOxviM5gjNzDzW}
pwn.collefe{Uedmcbf9k9vq9IAiMoV8Z6knT6A.0FL0MDOxviM4gjNyEyW}
pwn.collefe{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzDzW}
pwn.collegd{Uddmbcf8k9wq8HAjLoV8Z6koT6A.0EM0LDOxwiM4gjNyEzW}
pwn.college{Tedlccf8k9wp8IAjMoV7Z6koT6A.0EM0MDNxwhM5gjNzEzW}
pwn.college{Tedmbcf9k8wq9IAjMoV8Z6koS6A.0FM0MDOxviL5giNzEzV}
pwn.college{Uddlbbe9j9vp9HAiMoV8Y6koT6A.0EL0LCNwwhM5fjMzEzW}
pwn.college{Uedmbcf8k9wq9IAjMoV8Z6koT6A.0FM0MCNxwiM5gjNzEzW}
pwn.college{Uedmcbf9k8wq9HAiMoU8Z5koT6A.0FM0MDOxviM5gjNzEyW}
pwn.college{Uedmcbf9k9wq9HAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzEzW}
pwn.college{Uedmcce9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwhM5gjNzEzW}
pwn.college{Uedmccf9k9wq9IAjMnV8Z6koT6A.0FM0MDOxwhM5gjNzEzW}
pwn.college{Uedmccf9k9wq9IAjMoV7Z6koT6A.0FM0MDOxwiM5gjNzEzW}
pwn.college{Uedmccf9k9wq9IAjMoV8Y6koT6A.0FM0MDOxwiM5fjMzEzW}
pwn.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzDzW}
pwn.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzEzW}
pwn.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzEzW}
pwn.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzEzW}
pwn.college{Uedmccf9k9wq9IAjMoV8Z6koT6A.0FM0MDOxwiM5gjNzEzW}
```
### What I learned
I learned about the sort command which can alphabetically sort the contents of a file. It can also take in various arguments like -r for reverse order and -n for numeric sort -R for random order -u for unique lines only i.e to remove duplicates.
