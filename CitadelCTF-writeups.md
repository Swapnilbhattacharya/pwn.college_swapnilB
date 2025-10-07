# ZAHARD'S WELCOME
“ The base of Citadel rises before you, its great doors sealed with fractured steel and dead circuitry. Faded corporate protocols 
still hum in the lock, relics of the world that fell. Those who came before tried to climb but all failed. Their echoes linger as 
fragments of voices, reminders of broken attempts to free humanity. Now you have chosen to take their place. You will be the one to 
scale the Citadel and finish what they could not. The voices of the fallen whisper through the static: 
"The path begins in the gathering place. There, candidates are chosen". Here is your invitation. Step into the gathering place where 
all climbers are briefed before the ascent.”

### MY SOLVE
**Flag:** ` citadel{7h3_c174d3l_b3ck0n5}`

### THOUGHT PROCESS/STEPS
In this challenge, we just had to follow a simple clue — the invitation link provided in the description. Once we clicked on it, 
it led us to the discord server, and from there, we explored the channels a bit. Eventually, we headed to the #rules channel, and 
that’s where we found the flag at the very beginning.

# THE SOCIAL NETWORK
“The ascent begins. The first floor is not metal or binaries but of memory. Among the echoes, one voice lingers, of an early 
climber. He was among the earliest to challenge the Citadel, and though he failed, his traces remain scattered across the ruins of the 
old world.
It is said that the key to the next floor can be found by tracing the socials of this legendary climber.
Start by checking out citadweller on Instagram.”

### MY SOLVE
**Flag:** ` citadel{17_1s_jus7_7h3_b3g1nn1ng}

### THOUGHT PROCESS/STEPS
In this challenge, we first headed to the Instagram page citadweller, where we found the first part of the flag hidden in one of 
the stories. Along with it, there was another clue that pointed us toward a Twitter page. When we checked there, we discovered 
the second part of the flag. After that, we simply combined both parts — and that gave us the complete flag.

# OMNISCIENT FLAG'S METADATA

“As you step into the second chamber, a figure manifests. Before you stands a forgotten deity, a dead god spoken of only in 
whispers. Known by countless names: “Apostle of Epilogue and Eternity”, “Lone Messiah” and many more lost to time.They leave nothing 
but a single image, a relic carrying his final secret. Hidden within its layers lies the key to ascend to the next chamber.” 

## MY SOLVE
**Flag:** ` citadel {th1s_ch4ll3ng3_1s_f0r_th4t_On3_ex1ft00l_4ndb1nw4lk_enthus14st}`

### THOUGHT PROCESS/STEPS
In this challenge, we first downloaded the given JPG file and then searched online for an Exif tool, since the challenge hinted that 
the image contained hidden metadata. Using the tool, we checked the metadata and noticed a clue in the author name field — it 
hinted that there was another image hidden inside this one. Following that lead, we searched for an image layer extractor and found 
a website called Aperisolve. We uploaded the image there, and it provided us with a downloadable ZIP file containing the extracted 
layers. Inside that ZIP, we found a PNG image — and that image had the flag written on it.


## REFERENCES 
https://exif.tools/

https://aperisolve.fr/

## WHAT I LEARNT 
Learnt the use of exif and binwalk tools.

# TRACK 8
“Bypassing the second chamber leads to an empty floor except for a single artifact in the center: an old MP3 player, scratched 
and worn. On its surface, a cipher is etched, a message left behind for anyone who can decode it:
twj eys zpr ukm 'viamnwqw' bx lzgo: esmqqui{yyr_oshwwcm_bwupa}
When you power it on, the sound fills the chamber. The tracks play like whispers from a lost world, and you recognize it as a song 
from Panchiko’s latest studio album, particularly track no. 8. Its title feels familiar, hinting at a famous cipher. Decrypt it 
by using the album name as your key and continue your ascent.” 

## MY SOLVE
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

## REFERENCES 
https://cryptii.com/pipes/vigenere-cipher

## WHAT I LEARNT 
Learnt what is a cipher .

# TEST OF SWEETNESS
“This floor feels like a digital world. The space is an illusion, all pink and sweet, stretching around you in impossible patterns. 
Here, you are no longer a climber but just another user.
Ahead, a door glows faintly. It is the only path forward and requires a level of authority you do not yet have. Fragments of session 
memory flicker, hinting at what it might take to gain higher access..” 

## MY SOLVE
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

## REFERENCES 
https://testofsweetness.citadel.cryptonitemit.in/

## WHAT I LEARNT 
Learnt a simple way to take admin access of a website that if possible we could use a cookie edit if the website uses cookies .

# ROTTEN APPLE
“Among the debris of this floor, you find a relic of sound: An album which turns out to be D>E>A>T>H>M>E>T>A>L by Panchiko, a long 
lost album. But the music is warped, as though it has undergone disc rot.

The path forward is hidden in the distortion. Similar to how the album was warped, the password to the next floor has been warped 
first by a factor of 47, then by a factor of 13. Untangle these changes to reveal the code and continue your ascent.

4:R256=Y3oRRoP0#~%Ro?A” 

## MY SOLVE
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

## REFERENCES 
https://rot13.com/
https://www.dcode.fr/rot-47-cipher

## WHAT I LEARNT 
Learnt about ROT ciphers.

# SELECTED AMBIENT WORK
“The symphonic adventure does not end here. On the next floor, a single song keeps echoing through the floor, repeating in a 
haunting loop. Amid the sound, you find a note left by a past candidate. It hints that the song holds a secret message, hidden in 
plain sight, much like how Aphex Twin concealed his face within his music with the help of spectrograms.
To move forward, you must find the message hidden in this sound.
Note: Separate the words in the flag with _ and make it UPPERCASE. Example: citadel{S3L3CT3D_AMB13NT_W0RK}” 

## MY SOLVE
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

## REFERENCES 
https://www.audacityteam.org/
https://morsecode.world/international/decoder/audio-decoder-adaptive.html

## WHAT I LEARNT 
Learnt the process of decoding a morse code.




# ROBOTS_TRAIL
“You enter a virtual maze, a labyrinth of shifting corridors and endless paths. A guardian robot patrols the floor, leaving a 
trail behind as it moves. Follow the path it carves, trace its movements carefully, and uncover the key it leads you to. Only by 
following the robot’s trail can you reach the door to the next floor. 
Challenge: https://therobotstrail.citadel.cryptonitemit.in” 

## MY SOLVE
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

## WHAT I LEARNT 
I learnt patience


