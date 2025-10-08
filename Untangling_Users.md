# Becoming root with su
This challenge teaches us to go into the root as an user and read the flag.
### My solve
**Flag:** `pwn.college{MDShDu-VTAuXaZnl-bO_4s8u1Yd.QX1UDN1wiM5gjNzEzW}`
This expected me to get into the root directory using su. I did so and put in the password. That took me to my root user and i used cat /flag to read the flag.

```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{MDShDu-VTAuXaZnl-bO_4s8u1Yd.QX1UDN1wiM5gjNzEzW}
```
### What I learned
I learned about the su command which is required to get into the root directory with a password.

# Other users with su
This challenge teaches us to use su as a command along with a particular argument to go into some particular password protected user directory.
### My solve
**Flag:** `pwn.college{UPDQPr2NjL527-D1YJKIRd3YTQR.QX2UDN1wiM5gjNzEzW}`
This challenge wanted me to get into the zardus user directory using su zardus and then putting in the password. I wrote the command, entered the password and became "zardus".
```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{UPDQPr2NjL527-D1YJKIRd3YTQR.QX2UDN1wiM5gjNzEzW}
```
### What I learnt
I learnt that we can also use su to get into some pssword protected user.

# Cracking Passwords
This challenge teaches about the john-the-ripper application which is used to crack passwords when we have the hash of the password.
### My solve
**Flag:** `pwn.college{wPnJxRlPDu3fRMBmA9qGQ2bu50s.QX3UDN1wiM5gjNzEzW}`
I first used "john" as a command and used /challenge/shadow-leak as an arguemnt in order to decode the hash present in /shadow-leak file.
This gave me the password after decryption.
I then used the su command again with zardus as the argument and entered the given password to get into the zardus user. I then ran /challenge/run and this printed the flag for me.
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
This challenge taught me to use the john-the-ripper application in order to decrypt passwords from their hashes.

# Using sudo
This challenge makes the use of sudo to use administrative actions instead of su.
### My solve
**Flag:** `pwn.college{4AceICy03dKI3K3JqysSNuQPoc_.QX4UDN1wiM5gjNzEzW}`
In this challenge I used sudo which requires a command to be used along with it. I had to read the flag from /flag and thus it became my argument with the cat command.
```bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{4AceICy03dKI3K3JqysSNuQPoc_.QX4UDN1wiM5gjNzEzW}
```
### What I learned
I learned about the sudo command which unlike su,doesn't rely on password authentication. sudo checks policies to determine whether the user is authorized to run commands as root. I used its syntax to read the flag.
