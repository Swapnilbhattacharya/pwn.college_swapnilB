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
### 
