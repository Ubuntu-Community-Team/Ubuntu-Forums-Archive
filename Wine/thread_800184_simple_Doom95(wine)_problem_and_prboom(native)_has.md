---
title: "simple Doom95(wine) problem and prboom(native) has stupid issue"
date: 2008-05-19
forum: Wine
---

### Post by CC_machine on 2008-05-19
so i recently bought Doom: Collectors Edition. Love the games =]
running them in wine however, there's a small but very annoying problem: after some amount of time, the music simply stops.
half way through a level, the music just freezes and that note rings on and on and on, never ending.

i have done this on both my nvidia/AMD/integrated Asus sound/ubuntu7.10 desktop system and my intel GMA/intel core 2 duo/integrated intel sound/kubuntu 8.04 laptop, both do the same. both have wine and timidity installed. for the music to work in doom w/wine at all, i had to install all three of the timidity packages that appear in synaptic: timidity, timidity-el. and timidity-interfaces-extra. Other sound in-game works perfectly, as it should.

i would use prboom natively, and the music does work perfectly, but the OpenGL rendering is missing the atmospheric distance-based lighting, and the "8bit" renderer renders way too bright and loses the atmosphere that way. prboom has no gamma / brightness / contrast options. I would just tweak my monitor but 1) i shouldnt have to and 2) theres no way to do this on my laptop.

come on, i shouldnt have to boot Windows for a 13+ year old game :'(

---

### Post by Thirtysixway on 2008-05-19
I had this problem, too.  I somehow fixed it.  I don't know the exact steps, but I remember changing the file that timidity used to play music.  I'll look and see if I can find the old guides I used to fix it.

---

### Post by CC_machine on 2008-05-19
cheers dude :guitar: . I've tried modding the /etc/defaults/timidity file, adding various options i thought could work from the timidity manpage, but really, i'm just shooting in the dark :P, nothing worked sofar.

as the MIDI music in doom loops forever, I suspect there may be an issue with that, not looping the music back from the start again.. maybe. I've tried increasing the buffer size in timidity with the -B<number> option, doesn't help.

---

### Post by WMercier on 2008-06-05
I too had the issue of the music stopping at the reset point, locking on one note. I fixed my problem by downloading prboom and replacing the doom2.wad file in it's directory "/usr/share/games/doom". I can run the game perfectly right now just by running prboom with the wad file rather than using WINE. Perhaps there is some MIDI glitch with WINE? Either way, I hope this helps you solve your problem.

---

### Post by DoktorSeven on 2008-06-06
There are plenty of DOOM native binaries so you don't have to use Wine.  I prefer [Doomsday](http://doomsdayhq.com) myself, and it plays very well with Timidity...

---

### Post by Muhammad on 2008-06-28
> **DoktorSeven said:**
> There are plenty of DOOM native binaries so you don't have to use Wine.  I prefer [Doomsday](http://doomsdayhq.com) myself, and it plays very well with Timidity...
Does a .deb file exist for that one?

---

