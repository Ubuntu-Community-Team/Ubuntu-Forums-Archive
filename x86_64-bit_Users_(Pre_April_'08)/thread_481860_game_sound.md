---
title: "game sound"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by nzadLithium on 2007-06-23
Hey

I know theres hundreds of threads about this but none of them have actually got my sound going properly so im starting another one.

Games i'm trying to get going are:
Return to Castle Wolfenstein
Wolfenstein: Enemy Territory

I can get sound going in games by doing the 
echo "(game name) 0 0 direct" > /proc/asound/card0/pcm0p/oss
but then when i start up teamspeak i dont get any sound in game. 

I been having a look at some sound mixing stuff and found i could use aoss infront of ts to get it to go. This works fine. Now ts sound works while alsa sound apps are running. But i still don't get any sound in games (because they use oss) while ts is going.

I tried sticking aoss infront of my .sh scripts for each game but it doesnt make a difference.

So i went to a couple of million forums and found another way that is supposed to fix it. i'm supposed to do /snddevice /dev/adsp in the game consol. But then the sound doesnt even intialize it just comes up with 
------- sound initialization -------
GETOSPACE: Invalid argument
Um, can't do GETOSPACE?
------------------------------------

if i use the default sound i get this output
....... SOUND INITIALIZATION .......
.........................................................
..... Sound Info .....
sound system is muted  
        1 stereo
32768 samples
      16 samplebits
        1 submission_chunk
48000 speed
0x0858000 dma buffer
No background file.
....................................
Sound memory manager started

which confuses me a bit coz it says its muted but im still getting perfect sound as long as i dont run any other programs at same time as the games. 

so what i need to know is either how do i get games to use alsa sound or
what is another way to get ts and games to work at once?

and also completely off topic but how do you alt-tab in linux?

---

### Post by nzadLithium on 2007-06-25
I found another thing that may or may not help.

modprobe snd-cs46xx mmap_valid=1

how would i perform this command in ubuntu with ac97 audio?

---

