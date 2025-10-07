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
