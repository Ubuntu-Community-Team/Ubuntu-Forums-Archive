---
title: "Choppy sound ubunu + wine1.2.2"
date: 2011-10-25
forum: Wine
---

### Post by editheraven on 2011-10-25
I have reinstalled wine today. The sound in frozen throne started to be choppy and lagged. I tried this [http://bugs.winehq.org/show_bug.cgi?id=12182](http://bugs.winehq.org/show_bug.cgi?id=12182) for the SupCom but still no sound (not even for the intro movies). In torchlight, for example, i have sound. It's a pulseaudios server problem or a codec one?

---

### Post by blade4 on 2011-10-25
Here are a few suggestions : 

1) Run the game from terminal and check the output to see what   
   exactly the problem is ( you can ignore the fixme errors ) 

2) try enabling both alsa and oss drivers in the wine config menu 
   - I know from personal experience that games like diablo 2 
   need oss for sound 

3) Dunno if this will really help , but try running it in opengl 
   mode 

   wine /path_to_file/war3.exe -opengl

4) you might try updating to wine 1.3  


Hope these help , 

Cheers :)

---

### Post by editheraven on 2011-10-25
I tryed all wine versions. I use alsa through pulseaudio sever.

---

### Post by editheraven on 2011-10-25
I noticed that killing pulseaudio server gets rid of the sound lag. What's the thing between pulse and wine?

---

