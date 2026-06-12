---
title: "WoW in game crash."
date: 2008-02-27
forum: Wine
---

### Post by baudday on 2008-02-27
Ok, so I have WoW running almost absolutely perfectly with my Radeon X850 card. The problem I'm having is a while into playing the game, the whole system will just lock up and i'll have to power it off and back on. I had the problem where it would crash as soon as i entered the world, but I fixed that by adding those 3 lines of code to the wtf file. Another problem i'm having is the game crashing when I adjust the video settings in game. The reason I was doing this was to get optimal resolution, but I can live with 1024 x 780. The main problem now is the mid-game crash.

---

### Post by baudday on 2008-02-27
not sure why i'm never getting replies on any of my threads...

---

### Post by Snipershot on 2008-02-28
I belive you can set the resolution in the WTF file
SET gxResolution "1600x1200"

---

### Post by baudday on 2008-02-28
Thank you very much, does anyone else know anything about the crash that's happening? It seems to happen about 15-20 minutes into playing.

---

### Post by MrShurr on 2008-03-21
I have exactly the same problem. :( It sucks.

---

### Post by MrShurr on 2008-03-21
Hey! I think I fixed the problem! The thing is, I haven't tested it fully. But after making these changes the game seems to be running fine. It's been running for about 30 minutes... which is longer than it used to before crashing.

First of, go into WoW and configure it to run in windowed mode (log into a character, press escape, click video, and check "windowed mode"). This will eliminate any sound or graphical issues when alt-tabbing and stuff like that. After you've done that, exit the game.

Go into terminal and run

>  winecfg 

Click the audio tab. If you've been running under the OSS Driver, then uncheck OSS and check ALSA Driver (This is the one I did). If you've been running ALSA Driver, uncheck ALSA and check OSS Driver. Click Apply and you should be fine.

I was running OSS, and after switching to ALSA it seemed to work fine. I didn't fully test this, though. So it might not work.

Hope I helped!

---

### Post by baudday on 2008-03-24
thanks a lot for that reply. can anyone verify that this has in fact solved the problem? I have applied the changes, but haven't gotten enough time to test it out.

---

### Post by baudday on 2008-04-11
> **MrShurr said:**
> Hey! I think I fixed the problem! The thing is, I haven't tested it fully. But after making these changes the game seems to be running fine. It's been running for about 30 minutes... which is longer than it used to before crashing.

First of, go into WoW and configure it to run in windowed mode (log into a character, press escape, click video, and check "windowed mode"). This will eliminate any sound or graphical issues when alt-tabbing and stuff like that. After you've done that, exit the game.

Go into terminal and run



Click the audio tab. If you've been running under the OSS Driver, then uncheck OSS and check ALSA Driver (This is the one I did). If you've been running ALSA Driver, uncheck ALSA and check OSS Driver. Click Apply and you should be fine.

I was running OSS, and after switching to ALSA it seemed to work fine. I didn't fully test this, though. So it might not work.

Hope I helped!

This solved all my problems. I can now play for hours on end without any problems. Thanks a lot :guitar:

---

