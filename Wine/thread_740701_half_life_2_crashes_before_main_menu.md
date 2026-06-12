---
title: "half life 2 crashes before main menu"
date: 2008-03-31
forum: Wine
---

### Post by AmanoAcid on 2008-03-31
I'm running on Ubuntu 7.10 and using Wine 0.9.58... and got Half life 2 Orange Box installed without a problem... it started up and had that 'valve' video at the begining and that blurred screen in the background that's behind the main menu.. and I wait for the actual main menu to load then it just crashes.. and i doubt it's a hardware problem cuz it worked just fine when i had vista

help! i'm an absolute dummy wit this so you'll have to spell out everything to me.. sorry! but thanks for the help

---

### Post by AmanoAcid on 2008-03-31
anyone? 

i know there are others running this game on ubuntu.. but i can't! there should be an answer out there somewhere.. my searches got me nowhere

---

### Post by TheMightyGirth on 2008-03-31
I am fighting with this too (along with all 3d stuff by the looks of it)

I got a little further by adding -novid to the command line.

One of my problems is a _very_ low FPS rate, this made it look like the game had crashed when it was realy trying to play the opening video.

my command line is,

WINEDEBUG=fixme-all wine steam.exe -applaunch 220 -novid -dxlevel 80 -width 1024 -height 768

---

### Post by naz37 on 2008-04-01
I had a similar problem with HL2 and tracked it down to being a problem with wines OSS support, i solved it by using ALSA instead.

Open winecfg,
On the audio tab *enable* ALSA and *disable* OSS.

hopefully it should start for you.

---

### Post by AmanoAcid on 2008-04-01
^that made a small change.. on the valve startup video the screen wasn't set to fullscreen until it began to load the main menu.. then crashed before it finished... 

so no that didn't work :(

---

### Post by AmanoAcid on 2008-04-03
anyone have another idea i can try?

---

### Post by Brynster on 2008-04-04
try setting the dirextx level on launch to directx 8 or 8.1

this is done by adding the flag  -dxlevel 80 or -dxlevel 8.1 to the command listed above

---

