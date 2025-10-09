# Launching screen
This challenge introduces us to screens in linux terminal which is nothing but a virtual terminal inside my original terminal.
### My solve
**Flag:** `pwn.college{kRjmB2p_fITjAnKs2XLGMlTZu5Z.0VN4IDOxwiM5gjNzEzW}`
I simply wrote screen on my terminal and it opened up the screen for me on pressing enter and going to the next page I found my flag.
```bash
hacker@terminal-multiplexing~launching-screen:~$ screen

**Pressed Enter**

                                             Screen version 5.0.1 (build on 2025-05-15 15:05:07)
Copyright (c) 2025 Alexander Naumov
Copyright (c) 2018-2024 Alexander Naumov, Amadeusz Slawinski
Copyright (c) 2015-2017 Juergen Weigert, Alexander Naumov, Amadeusz Slawinski
Copyright (c) 2010-2014 Juergen Weigert, Sadrul Habib Chowdhury
Copyright (c) 2008-2009 Juergen Weigert, Michael Schroeder, Micah Cowan, Sadrul Habib Chowdhury
Copyright (c) 1993-2007 Juergen Weigert, Michael Schroeder
Copyright (c) 1987 Oliver Laumann

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the
Free Software Foundation; either version 3, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program (see the file COPYING); if not, see
https://www.gnu.org/licenses/, or contact Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02111-1301  USA.

Send bugreports, fixes, enhancements, t-shirts, money, beer & pizza to screen-devel@gnu.org

**pressed enter**

Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{kRjmB2p_fITjAnKs2XLGMlTZu5Z.0VN4IDOxwiM5gjNzEzW}
hacker@terminal-multiplexing~launching-screen:~$ exit

**Pressed Enter**

[screen is terminating]
```
### What I learned
I learnt about the screen command which can open up a virtual terminal(screen) inside my original terminal.

# Detaching and Attaching
This teaches us the purpose of a screen. While working on something important over a remote connection, if our connection drops, everything's gone. With screen, our work keeps running, and we can reattach it later. We can also detach on purpose.
### My solve
**Flag:** `pwn.college{oAJbFR5BWD_2LKfs2bcS3IhIE5K.0lN4IDOxwiM5gjNzEzW}`
I first launched screen using screen command. On getting inside the screen I detached it using thr Ctrl+A command followed by D. Then in the main terminal I wrote /challenge/run whic printed my flag to the particular screen session. I then reattached screen using the screen command but this time with the -r argument.
```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 139.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 139.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[screen is terminating]
```
### What I learned
I learnt how to detach and reattach a screen session and also its practical uses in case of dropped connections.

# Finding Sessions

### My solve
**Flag:** `pwn.college{EINl6WUYJLaMARIDXDTV5Aw9rFC.01N4IDOxwiM5gjNzEzW}`
I used the -ls argument with screen to find all active screens on my terminal. I then started reattaching to each screen one by one using the screen -r command along with the respective screen PIDs as arguments. The first screen 144 had nothing in it so I used ctrl+a and d to detach and again reattached to session 147 and here I found the flag.
```bash
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        161.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_88610ab238d9c06a    (Detached)
        147.session_644813e9c4238ad6    (Detached)
        150.session_62d9a1f8386765be    (Detached)
4 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
[detached from 144.session_88610ab238d9c06a]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147
[screen is terminating]
```
### What I learned
I learnt that we can have multiple screens running on a single terminal at once and can attach and reattach to them as necessary. Moreover, I can list down the active screens ans locate them with their names or their PIDs.

# Switching Windows
This challenge teaches us that we can not only have multiple screens but also have multiple windows inside one single screen.
### My solve
**Flag:** ` pwn.college{ATS4YqnyA4SAyLjsei2tALbXnYj.0FO4IDOxwiM5gjNzEzW}`
I used the screen -ls command to look for the challenge screen. I then used its PID as argument with screen -r in order to go into the screen (attach it). It opened up the window 1 in front of me which instructed me to go into window 0 to get the flag. I used the command ctrl+A along with 0 to go into the 0 window and there was my flag. 
```bash
hacker@terminal-multiplexing~switching-windows:~$ screen -ls
There are screens on:
        161.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_88610ab238d9c06a    (Remote or dead)
        150.session_62d9a1f8386765be    (Remote or dead)
        135.challenge_session   (Detached)
4 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~switching-windows:~$ screen -r 135
 cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
[ctrl+A, 0]

hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{ATS4YqnyA4SAyLjsei2tALbXnYj.0FO4IDOxwiM5gjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{ATS4YqnyA4SAyLjsei2tALbXnYj.0FO4IDOxwiM5gjNzEzW}
hacker@terminal-multiplexing~switching-windows:~$
[ctrl+A D]

[detached from 135.challenge_session]
hacker@terminal-multiplexing~switching-windows:~$
```
### What I learned
I learned that we can not only have multiple screens but also have multiple windows inside one single screen and ctrl+a along with window number as argument can take us to a particular window. Also there are other arguments with ctrl+A like c which creates a new window or p to go into the previous window and n for next window or " to bring up a selection menu of all windows.

# Detching and Attaching (tmux)
This challenge teaches us about tmux or Linux Terminal Multiplexer. This is a modern version  of screen with more or less the same uses but different key bindings.
### My solve
**Flag:** `pwn.college{YomwOencP7CQGMbgPB56v4WhIz7.0VO4IDOxwiM5gjNzEzW}`
Just like the previous screen command i used tmux to start the multiplexer. Then I used ctrl+B and D to detach the multiplexer. I then ran /challenge/run as instructed and then went into the multiplexer by reattaching it with "tmux a" command. This gave me my flag. I then closed the multiplexer using ctrl+D.

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 61;4;6;7;14;21;22;23;24;28;32;42;52c
-bash: 61: command not found
-bash: 4: command not found
-bash: 6: command not found
-bash: 7: command not found
-bash: 14: command not found
-bash: 21: command not found
-bash: 22: command not found
-bash: 23: command not found
-bash: 24: command not found
-bash: 28: command not found
-bash: 32: command not found
-bash: 42: command not found
-bash: 52c: command not found
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{YomwOencP7CQGMbgPB56v4WhIz7.0VO4IDOxwiM5gjNzEzW}
Congratulations, here is your flag: pwn.college{YomwOencP7CQGMbgPB56v4WhIz7.0VO4IDOxwiM5gjNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$
```
### What I learned
I learned about Terminal multiplexer and its uses along with the specific key bindings for it.

# Switching Windows(tmux)
This challenge introduces us to the concept of windows again but now in tmux.
### My solve
**Flag:** `pwn.college{8IsLy-ARnJX7NDdpcH3e1T7AtjE.0FM5IDOxwiM5gjNzEzW}`
I used the tmux attach command to go into the tmux created and it opened up in window 1. I used the keyoard shortcut ctrl+B and then presses 0 which took me to the 0th window. There the flag was written.
```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux attach
 cat <<MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows-tmux:~$

//pressed [ctr+B and then 0]

hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{8IsLy-ARnJX7NDdpcH3e1T7AtjE.0FM5IDOxwiM5gjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{8IsLy-ARnJX7NDdpcH3e1T7AtjE.0FM5IDOxwiM5gjNzEzW}
hacker@terminal-multiplexing~switching-windows-tmux:~$
```
### What I learned
I learnt to navigate windows in a Linux Terminal Multiplexer.
