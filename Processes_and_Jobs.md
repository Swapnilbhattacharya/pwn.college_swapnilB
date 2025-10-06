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
**Flag:** `pwn.college{Mq3Ihpvnz_70gEbrVjBiLS1e909.0FNzMDOxwiM5gjNzEzW}`
I first used ps -ef to print every process going on in my terminal and then found out the PID decoy challenge process and killed it. Thereafter I had to read the fifo file but since i know that fifo files can only be read when both read and write to it are simultaneously going on. So, i used the cat command on the final fifo file and in another terminal ran the /challenge/run program to read the file into the fifo and my flag got printed.
```bash
hacker@processes~killing-misbehaving-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  1 20:35 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 20:35 ?        00:00:00 /run/dojo/bin/sleep 6h
root         137       1  0 20:35 ?        00:00:00 /bin/bash /challenge/.init
root         138       1  0 20:35 ?        00:00:00 /bin/bash /challenge/.init
root         139       1  0 20:35 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140     138  0 20:35 ?        00:00:00 sleep 6h
root         141     137  0 20:35 ?        00:00:00 sleep 6h
hacker       142     139  1 20:35 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       144       0  1 20:35 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoin
hacker       150     144  0 20:35 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       159     150  0 20:35 pts/0    00:00:00 ps -ef
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{0vCG5PEYN2ZZc6L9dSAy-SqjdzsrAvz0pTm.BbqNbAYMtn2}
pwn.college{-Nq3go8RmZBaFQZGt5BhuDFERLvu7Sywa-aYL017PZggW36}
pwn.college{fDbWq4FVF3gFbhZ7l22bbeWZlhM71bgkyITDVScFwa.iy2J}
pwn.college{0NbndaC1WJ-r0PSgNHF7ChStxCyMeaA8rK4A6NPyFi17q8G}
pwn.college{gjAgQ4CobBjwQ1Ohohk-65PcI9JukG.GfL5VXO4K-BdNVEs}
pwn.college{0zijLNRDRJW-qRUfDKu09Nyb.AsXnaXRdax53oTYm96Ayfs}
pwn.college{IciRSgKK.jODXMSuC33l.cfdgP6ZNz4co9cmUXcoghsfQ42}
pwn.college{FNAkmt7gd-j67QjctPKz2ElQfcb6CMIdSm9QAJ3PRmFHwj9}
pwn.college{-.eYR7rdctEbyNxiDMe7L6wgHsmHTHOLtnx43EzWGKBBjzt}
pwn.college{q35cXcb-0OFG88cKQ.LWn7OZuWpazI4nEeX.8mFMr18IlDM}
pwn.college{zfD6M1cTIKPa0i0mFsNz2Z.Hbu9xsdXuE7kyZhfna5vaJ6R}
pwn.college{TQwvsoblaP9KXUrU2QkNFO-vvoZRDs-fMVC7ybhvf8-PDtm}
pwn.college{0tE2cS.AOIDLNXC3YR8UjAxgvRw1CAtJivGYa6lmPU1EnVv}
pwn.college{h6qeyECc552nhOE8CMMpDvwGXXKzaoM0NQayA532bjcrGNB}
pwn.college{vBQMfSZ8GAtxno0BRxy41RFJrTXGIqdmaf6vbkrA9O23yta}
pwn.college{ga1NVDLC0zb2qzld2tGuKRe3OJn92AqMS4K6wBiVhOTT6f.}
pwn.college{kTgSz1Rqn3hHEONDovC8eGNbRZoFG1Q-L8p2FOslAvKre2c}
pwn.college{XU3mCIKor2-sTwwZlJ9N7qCDGPRTP1564JZC2me3IgkTofr}
pwn.college{7aYeVjBZz6gD5ePgJ1Tht.Jv9DoQ-af8NYjPgVzuifbKCfy}
pwn.college{yGYxZHQbGBw6apeNrcfZkpf2Hajb11wOkKTyKwBvsq6r.Y-}
pwn.college{a.zLaLPuv102yc46yssYMF470FwZFyKoVTCsr92-dnRJrxe}
pwn.college{INY5DV5wHjaQ2NjuB-VJ6J89uBcrQiaYT7i29cTbI4hDIQ-}
pwn.college{pPOiuwfvnhExx88d7Wy7xZ2S29pa7oqiq5vysIN3HgDM2Ss}
pwn.college{0TqmI2IblN6OpLKn4nZBBb0w4mljE513stI8u8JsXveqkqs}
pwn.college{jW7UCFBBTslNc7izvv5vHzyXR8LzWKi13DJh50fsnJ5fet1}
pwn.college{3jDAogADU3KfrPw5Eqvd3AhOt3R5d.r7br7Xb-xYDF4JlW4}
pwn.college{QYWTEyxDMbzQRKkHp0ODVcAvfelqhIk6akqNOIldxJ5tlGv}
pwn.college{S4IaROcDFNBctYSOHztAWRYSgGRIyxQKMq1csswYOn7Vixc}
pwn.college{rMuXBWk5DDIuIPr6L-A-XFiZ--cLTZUEFZx9YWuPYn9t.Sv}
pwn.college{EcfQA1S34LpcvKto7KmSybgKVYDwUH0871IQeOqvPikYPzt}
pwn.college{6jpqP5Q-8zO3dspDko7LeDrA3Dv3tLye00kvRlM65BmTb0n}
pwn.college{397HVINfp2.zk7zPx3Jdl28GJceQiKHdRntUjCK4ICAopwD}
pwn.college{ZVpkUnXT.U0l.i0pE70gBvIoDrr5vtpnzSenM0GlTBZDBr4}
pwn.college{PrQbd8t6ePerY2YllqI5o5MsSgSBMIMi7wPGakancj11Ou4}
pwn.college{8tXN-M.aW6y8AX1sbrQZkHqMce7Ot75mTBESAHK9JCxyILh}
pwn.college{cNjbVWO9.nzyqs-en2O3O3fVGOa3d6E3s2tZqhLTSNq5F6-}
pwn.college{k00fBAnukIGUDvxG38l8PKCCNvYkZncS8X2VZbYl.ikDPz5}
pwn.college{8R-tWX4I3FNinvWsfLz.4J956Y.SjHo30kemmgOkOUfNy5g}
pwn.college{TtfOUcz.TR1hrnIOvCPvvkjrVK0H2k1aRRf-AGlHAi9ZvTA}
pwn.college{G62F02CvlWI1GHeis7oEZHiFARBXb5Op--UImohBK4VddDG}
pwn.college{qEwLvvT1zjwGOp6BPVAO9qO4te-.7L1ErFT1xgm-sYNUBTe}
pwn.college{4SRBAx.gZn5PPMiBL-5eSXvyflWgB80kHHqBgY7GNuOxkSS}
pwn.college{zuF8G4yVATRFLm8YcJBb2C-r5v7RbvqXeVtULVfLU5Aps4S}
pwn.college{LHFCbwe-YWfW4cq8GD7rK8kV0yDpwzeZOQVtXGBIghFu.Vm}
pwn.college{u4gbMp9A2ZHU7u1Y3Q-D5PvpMJZ1aJC0DlE0ohR.6EfVgio}
pwn.college{WX7lAapPDWzMptwOVp1JXXWp8j-nyFaOJ2hGhJk2AVh14bk}
pwn.college{fmrwLxx4jQNILmiow-4n3cP.BVLBrIMIWYZ4JPsyQmrGLSq}
pwn.college{WabD0JXm7X6azwGc28Od6qLpr1LmUtbIMOGop1xxhyKuIqn}
pwn.college{QUkuLohPjy9hKYSn7E4GogdCyxpmMcYXg8ygXxUJNjd-bxt}
pwn.college{gZpkihzvpW1meRmrlfwkQRb1Vc7hkN04rH6FOsPO.Z5SaJ0}
pwn.college{31xN81ovYm3tUelBXuQajW5MlFj7BCQgvMuEal4GI-qvJBw}
pwn.college{FCa62ZuI0khHaAxa0V29x0Qz0LwnzsRh8nngkRq8yzuUJa0}
pwn.college{xkr.qNDlaSnrmfNuGBj.rmZv3m4f2HAHcKseNND-nVdIAMS}
pwn.college{Abznop7vM2I9i5RBIIt5m44dUCS95ZpYGwN4Q6Mub2TAfau}
pwn.college{w7VLZhNLffD0oZirNvX-NY4yy2nLA4XmXtNIpGFKMsr5iuF}
pwn.college{I-yd71LUAbkCfbODK65t.uI0S2oxK.Fv9TSouqDUy8iGB-m}
pwn.college{fDHdO1-8chGTol9d9agqXGnqMYEI2nrOYghOEqWITDATs.K}
pwn.college{Wk59C8q8MjsZMkPF-WNvR.EzrGD.UweWMnenr09vQk7cBzt}
pwn.college{GoosNyQCq93CwB.bjgTsjF.OvEtIV9JARUpIudJpxcKOz5Q}
pwn.college{8epOyQRqfAbGGWFc8u5pE8aOG9oEYc9KPNrzAcbibBadfWC}
pwn.college{mjVLQIJAg0vwWw9v0Cw-fKxRgu.CgSr8hRLS-JTGuY0xy9p}
pwn.college{IrudCjHuo4E-00Q3LIGjL27C1nn1NMsDvfOqwOJXr2HjCwN}
pwn.college{JmYL9TKv.j1OEEnli-ZJ1XfwtFsxzBcSU2v2d2EKlnZP33M}
pwn.college{2LziyI4ZwYYaGf5n3Gnq2B9QGykFA7GmSIjvQ.HFiocAw6.}
pwn.college{buaNTGVs6RaNvISc1zR8IElJtwjlEAPSikT2D4MaiSJVpmO}
pwn.college{aMqRz.YofE1PV4GlMbI6KuyspO5azzErJfKh9gZJkrMvsyt}
pwn.college{3x6OszxU68Uadk77lP7wUmhD9lJnZURrTjUm3MuYlLGUvnG}
pwn.college{1xYRG4jw8H.gBzcGDlIr5b8C3DDh9abXfsd.mhzT0OXAlVf}
pwn.college{7b2Oc.e09yUxyJuGH8yL9wTiRQlonBrEpTgpeIiTodwMN8U}
pwn.college{uqIUdc86mXu249pQH04G1MTE3ZxdJ6VxNA7ePa4bSK7exDy}
pwn.college{9in-fPfq3j2CL9Y7tNdVMYNWKm7R064Z.XM-mVh9MFstCRF}
pwn.college{j5OBLvWFrVxwjqmn7pUTCFMcVVDe-BXT98zL6sJPjWS3x4z}
pwn.college{dvAI74d.ZdEbTTB2ZtkSpLiVjEUEzAU-CfQOoIT8E3mhK8f}
pwn.college{Ju.mKnwU1zgpGBSJyUX3Mfsqppq5eVutzbmZX90zsZraZrT}
pwn.college{-cICPH5KqehW75jnha-KP.L6a.KLSX8-UU0bwm0v21jM3.C}
pwn.college{7xMUtxoe176xPRWAo3k-XlpwPDpQeX8.OKnZ6T8lrZiZjIL}
pwn.college{SOdpF5uyR5FwRUXj0Cqpdllh9aHAqpwnZXtE4m51Kkcg10M}
pwn.college{Un45UKYMAkoFjwRlDczJhLdEG.MESK27.mqR-GX2TekMPJ4}
pwn.college{LTBIhIGI4IuUXNnuqEZcpVgCG-YeH5B2SfNorACuuvdSY1H}
pwn.college{ZEELkYhgOzuHJ7MZng51uXwNa5rpasBHjlz95kUrwczqmC4}
pwn.college{gg0qUf0oN1UAhURQ.MtuP8EOWkZ.-orBObZRUm.BFwVY.7F}
pwn.college{DZPjfCf9eIyrGYZvLeWR9KSiATy5xo-5fPLnVrWJlPFzYKm}
pwn.college{KvyWVW5b.XOxby73SucNn3ojtiuc5JVOcSfp51PC7whDY3Z}
pwn.college{91cWQH9rpRR4XZfE77gm9U5jDw6NhtL2foqXQJQ8vsKoJee}
pwn.college{kX9mtmK9kQ2DTuhuGrfHoBJLUu1g2gsPWKyx3TxgsPdjDHG}
pwn.college{u-TZLLQs9YfXogx7u6Mc803Ft14Lk0eMvxy83gUm5a2SNGE}
pwn.college{08OPEhlppUw.SFKL3WBBRNgFts2uDyczP-v6RaNOYRKCjXO}
pwn.college{1Rnq3f8DUZmRgmyGKu7xq.cG7rYdrVBwHR1kNFnzJs6dq0Z}
pwn.college{odGn.GOiL-JFyTbAQN0GuzjMkdYsq2K4d-3dpBDkTVNwmyg}
pwn.college{vFTZCv8QprsFR5UHtZHEDkf9QsDr4-F8tQ29HCfcs2z-qad}
pwn.college{UE4uT.AEIyZL5iCGUKudexPxminwCeSqcggz-iGzWBzuWmA}
pwn.college{XC6wQE5SFHYN7IdUctcLhlzX0yn4IGcLJ43W9z.g3QWMlyg}
pwn.college{YNl4kw9nEJMIBSbejwpmsE7IegzaDkNIAHl9oZGlvKNo8Lg}
pwn.college{RW62knQhLu4.ksv.Vt.IPNP2ChzxQDP0XUsDk.RIdFnsnMv}
pwn.college{SwdCE6DMJdKuPfdMuPw.5jkI5w2QqbXoyza5gB7OLR9eG7b}
pwn.college{zUorlBy.4aG9N2Iu1rc5jw3tiiVZFCsBrBxxB4yBDtAemGI}
pwn.college{.l9c-V.Qb5Oiq8FC1BoA9kPrH8oOgVaD7qtCb3fDb-daQka}
pwn.college{PBQ5UkmaPQF-0TPmUnVVn2Z--xZSl50c40CbEBucs6cAa3Z}
pwn.college{sfKC1y2oFve90xpZoUSEnR4gxOHPlPW1fqXehds4BNRQy8z}
pwn.college{3IETYktjzR2YMZwqB2BzuFxd8sEfG4eO3nJ6M3lHcKm2jwq}
pwn.college{.z1JaSqbqgfONuBmfPGI1CSb9GnyTZMTB2R1tpm8PXr5a0z}
pwn.college{lMUr1clM2Cy2bWXKiJLoOw5o3mxzdE0qW1ka4HpR-CRGEbs}
pwn.college{ugKtMFaDeqwFFdXWTGWvzQyscte8wqXL1snKN-CF1CkhRFA}
pwn.college{0TO3vEHExpNU2vsmgypsdiLpRSLT5fPzr-Wg26rvaRb4c5w}
pwn.college{Kgs9g5yUvdPDW6v0wpwKcnQ3V9tZ-VBahidLPjEO-c.9kP2}
pwn.college{wCqGQraRDd2tjuEnH1xvCjPRHdoGMCMky49detiCOx8yMyY}
pwn.college{7HRrt6PmwVn-dAK8a-yg2b5Qubr4xkK2GcPuD9zMtc-Xm.L}
pwn.college{VLaJT-NKE0nFBJiw9OjU6p1MgMsokNvW-509kNiSIXzoJj.}
pwn.college{wpAOE6N9YZ7mCAhmpkQmPzZVpM-BcUDyGDZzrtjJB00oK5O}
pwn.college{zWxXi3A.hyshuaws8MH4fG1CijMMkUHReG-2aUkZkGLTlxD}
pwn.college{UwgfXMUPjjZ85HlUMkYoYPOnyF9JHxgs5NvI-Tx5LlX5yHF}
pwn.college{yX.pft7o14qQOquEH4-i7VO3A98z.w2P9lhfCXIiZSTOGAl}
pwn.college{hnTJ.nt0F5SFotgW0FbkauRzWTAZgkCRMtc4IRIBp7HUt47}
pwn.college{YEO-ZMQfnjuZX4KbLTFlT4EWBFYUcxkj-qROYaEZczeyizQ}
pwn.college{RhaPfALiermIW-xhnoCzuAuwKND9EBOj1XA-4f0lxw.5Kjd}
pwn.college{qc4snQzhieMtiZilklFeGI1LpjM7D7AqfdkYcKG2GbrOZhk}
pwn.college{liVW7BDBCeCPKpVZxKdBeTwLIf56E.K.c26znhdZdAD.J0r}
pwn.college{J5W6XZtKtmEe9bBRsEYd4UqTqfj1sSbo2i9oiAg69meqnay}
pwn.college{UI4UydqwDaix307dGL8aaTx802dCfLfcE4Xc2BvH7q0zDHv}
pwn.college{aOScBcPlOkaamPHoHZ6XQvOomuIjx.Ak3PVx8xuBMOoZwwg}
pwn.college{RvaYrOMyDVd-.3sFaKs6vTKYakBpZWGow5AUD4iAkCteUkB}
pwn.college{Oj6x.nGRIWLMxVcbMkBPkeOZjaWjKQ.sz4TFYHT2NWhWwah}
pwn.college{nIuV7hjVMjq-aCCaXLvMrQJwQrUFLXqA7gIqRsAUw3Rtxgr}
pwn.college{0.95Yp.3q.Q-SexQskwkLyx5seAzG2cI.WHbkyG5aCEJo7t}
pwn.college{gjdBUXrpQU-udH3lKE45fb0mSDOVkaheCA05tS1-wxnzZmv}
pwn.college{X6ZdQKtlRAyAAHK27hRUF4AcmSQHFYhHfXyCViAEBtujOMy}
pwn.college{P.qyqe3zkxUNFHhoSQnlVjK.iKfuMTy37LBw7RY6nXpdK83}
pwn.college{emTtPRFqWiIdTlqVr17JcrP4GHA2P5Rg3Ok0ujfGlt9CxOS}
pwn.college{jQ8gcOoHcF2gMrBSRX5wqjSQgH0sNQtAIKpCJoGE8vbUIji}
pwn.college{fyT4dofGUctmTPobZH.8OkaSO-ui8EP3Gp1VolUpjQsAMZy}
pwn.college{2HZREg1YI0..hXG42WFp98Ozzlmfvyx0SYEPJQdm88kzb6r}
pwn.college{5QKP5Wsl-xsUZwSEBxJoZLbRBhc.cL3qyzpAM5wnbV26tcJ}
pwn.college{PnW7RLhXkVoT90RvlixmFnXcqxeXFhpIQE8pRdWdjuW3GpO}
pwn.college{WTYPRTerkh7J9Aacyz5tEVcBhFsJ5V9HkEfnzrMdr7CRgyi}
pwn.college{Mq3Ihpvnz_70gEbrVjBiLS1e909.0FNzMDOxwiM5gjNzEzW}
```
```bash
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
```
### What I learned
I learnt or rather practised and revised the concept of reading fifo files and also used the kill command along with the printing the process command ps -ef.

## Suspending Processes
This challenge is about teaching us the CTRL+Z shortcut to suspend processes to the background.
### My solve
**Flag:** `pwn.college{cZ0sbC4ZEYKcIfwO1r8o8zJ9sf1.QX1QDO0wiM5gjNzEzW}`
The challenge asked me to first launch my run program and then suspend it to the background and i followed suit and suspended it to the background using the hortcut ctrl+z. I then again ran the same /challenge/run command and launched the same program again just as it had asked me to.
```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         153     142  0 20:50 pts/1    00:00:00 bash /challenge/run
root         155     153  0 20:50 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         153     142  0 20:50 pts/1    00:00:00 bash /challenge/run
root         160     142  0 20:50 pts/1    00:00:00 bash /challenge/run
root         162     160  0 20:50 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{cZ0sbC4ZEYKcIfwO1r8o8zJ9sf1.QX1QDO0wiM5gjNzEzW}
```
### What I learned
I learnt to use the ctrl+z command to suspend a process to the background.

## Resuming processes
This challenge teaches us the fg command to bring a suspended command back to the foreground.
### My solve
**Flag:** `pwn.college{g_DR1NZZz1v6miJv_qa17AV0MoU.QX2QDO0wiM5gjNzEzW}`
I first ran the run program in my terminal and then as instructed I used the CTRL+Z command to put the run program to the background and again used the fg to bringt it back to the foreground.
```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{g_DR1NZZz1v6miJv_qa17AV0MoU.QX2QDO0wiM5gjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```
### What I learned
I learned the fg command to bring back a suspended program from the background to the foreground.

## Backgrounding processes
This challenge teaches us to put a suspended process in the background...It runs but is in the background and our bash is available for runnning more commands.
### My solve
**Flag:** `pwn.college{IkRcC8RXvSWxMZoeg1CpwEr9f8h.QX3QDO0wiM5gjNzEzW}`
I started the run program and used ctrl+z to suspend it. I then used the bg command to make it run in the background. I had to hit enter to get to my new bash. I again ran the program run in my foreground as instructed and it gave me the flag.
```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S+   bash /challenge/run
root         140 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S    bash /challenge/run
root         148 S    sleep 6h
root         149 S+   bash /challenge/run
root         151 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{IkRcC8RXvSWxMZoeg1CpwEr9f8h.QX3QDO0wiM5gjNzEzW}
```
### What I learnt
I learnt the bg command to send a suspended program to run in the background of the terminal.

## Foregrounding processes
This challenge just tells us that we can also foreground processes not only suspended ones but also the ones running in the background.
### My solve
**Flag:** `pwn.college{Ah1aMb0yi8HhWKWJCvhOLwyMTqs.QX4QDO0wiM5gjNzEzW}`
I initially invoked the /challenge/run command and then suspended it with ctrl+Z. I then used the bg command to run it in the background. I again used the fg command to bring it to the foreground. It asked me to hit enter and I got my flag.
```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{Ah1aMb0yi8HhWKWJCvhOLwyMTqs.QX4QDO0wiM5gjNzEzW}
```
### What I learned
I learnt that I can also bring up a process running in the background back to the foreground by using the same fg command.

## Starting Background Processes
This challenge teaches us that we can even start a process directly in the background by appending the command with & and it is not necessary to start them off in the foreground and have to suspend and send them to the background.
### My solve
**Flag:** `pwn.college{8NS6sNhyEMA3t2leCXnDDoKUmXh.QX5QDO0wiM5gjNzEzW}`
I simply ran the /challenge/run and added an & at the end in order to start it directly as a background process.
```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 138
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{8NS6sNhyEMA3t2leCXnDDoKUmXh.QX5QDO0wiM5gjNzEzW}

[1]+  Done                    /challenge/run
```
### What I learned
I learned that we can even start a process directly in the background by appending the command with & and it is not necessary to start them off in the foreground and have to suspend and send them to the background.

## Process exit codes
This challenge teaches us about exit codes. Whenever a process ends, it ends with an exit code while terminating.
### My solve
**Flag:** `pwn.college{gkjHsb1CVSjD13HfR1xZTVdC1Gw.QX5YDO1wiM5gjNzEzW}`
I ran the /challenge/get-code program first. I then used the $? command to  print out the exit code of the last terminated command. It gave me the value 19 which was the exit code of the /challenge/get-code program process. I then ran the /challenge/submit-code along with 19 as an argument to the command. This gave me the flag.
```bash
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ $?
bash: 19: command not found
hacker@processes~process-exit-codes:~$ /challenge/submit-code 19
CORRECT! Here is your flag:
pwn.college{gkjHsb1CVSjD13HfR1xZTVdC1Gw.QX5YDO1wiM5gjNzEzW}
```
### What I learned
I learnt about exit codes and that all programs terminate with a specific exit code. I also learnt that the special ? variable when prepended with the $ character can give me the exit code of the last terminated program in my terminal. 
