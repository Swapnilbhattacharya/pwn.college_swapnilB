## Becoming root with su
### My solve
**Flag:** `pwn.college{MDShDu-VTAuXaZnl-bO_4s8u1Yd.QX1UDN1wiM5gjNzEzW}`

```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cd /
root@users~becoming-root-with-su:/#
root@users~becoming-root-with-su:/# ls
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@users~becoming-root-with-su:/# cat flag
pwn.college{MDShDu-VTAuXaZnl-bO_4s8u1Yd.QX1UDN1wiM5gjNzEzW}
```
### What I learned

## Other users with su
### My solve
**Flag:** `pwn.college{UPDQPr2NjL527-D1YJKIRd3YTQR.QX2UDN1wiM5gjNzEzW}`
```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{UPDQPr2NjL527-D1YJKIRd3YTQR.QX2UDN1wiM5gjNzEzW}
```
### What I learnt

## Cracking Passwords
### My solve
**Flag:** `pwn.college{wPnJxRlPDu3fRMBmA9qGQ2bu50s.QX3UDN1wiM5gjNzEzW}`
```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:02 28% 1/3 0g/s 278.2p/s 278.2c/s 278.2C/s sudraz!..bzardus
0g 0:00:00:08 85% 1/3 0g/s 278.9p/s 278.9c/s 278.9C/s Zardus1111..z99999123456
0g 0:00:00:12 0% 2/3 0g/s 277.0p/s 277.0c/s 277.0C/s leslie..boston
0g 0:00:00:14 0% 2/3 0g/s 277.0p/s 277.0c/s 277.0C/s meggie..seattle
0g 0:00:00:15 0% 2/3 0g/s 275.7p/s 275.7c/s 275.7C/s billy1..december
0g 0:00:00:17 0% 2/3 0g/s 276.3p/s 276.3c/s 276.3C/s susan1..121212
0g 0:00:00:19 1% 2/3 0g/s 276.1p/s 276.1c/s 276.1C/s chacha..jazmin
0g 0:00:00:20 1% 2/3 0g/s 275.9p/s 275.9c/s 275.9C/s 10sne1..nermal
aardvark         (zardus)
1g 0:00:00:21 100% 2/3 0.04732g/s 275.5p/s 275.5c/s 275.5C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wPnJxRlPDu3fRMBmA9qGQ2bu50s.QX3UDN1wiM5gjNzEzW}
```
### What I learned

## Using sudo
### My solve
**Flag:** ``
```bash
```
### What I learned
