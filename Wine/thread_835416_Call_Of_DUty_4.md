---
title: "Call Of DUty 4"
date: 2008-06-20
forum: Wine
---

### Post by myromance123 on 2008-06-20
Anyone know where I can get a guide to setting up cod4 on ubuntu 8.04??

 I am using an Nvidia 6600, 2ghz,512mb ram. Any knowledge on cod4 and ubunu I welcome :D

     ( I heard there were wine issues with cod4 and hardy heron, is it true?)

---

### Post by cogadh on 2008-06-20
The major "Wine issue" with Hardy is not really a problem with Wine, but rather the sound system used by default in Hardy. They chose to replace ALSA with PulseAudio, which does not work with Wine. Pretty much the only way to get apps running in Wine is to disable PulseAudio or replace it completely with ALSA o OSS4. Supposedly you can run Wine apps with "pasuspender" so that it only disables PA while that app is running, but I've never been able to test that (I use Kubuntu, which still has ALSA):
```
pasuspender wine foo.exe
```

As for running CoD4, the current version of Wine (1.0) can apparently run it fine, but  you do need to compile Wine yourself with a specific patch to fix the issues that still remain with the game in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429)

---

### Post by myromance123 on 2008-06-20
I see. Thanks for the link. By compile and patch wine yourself, do you mean there is no patch for the problem it gives?? I have to write my own code? Its not that I mind, but I dont know how to code just yet(newbie).

     Have you made your own patch already? does it have to be pc specific ?
Or could you share it with me :D

 Anyway,thanks for replying so very fast. Hopefully I can get cod4 running smoothly soon enough XD:KS

---

### Post by thefishki345 on 2008-06-20
[http://ubuntuforums.org/showthread.php?t=641987](http://ubuntuforums.org/showthread.php?t=641987)


or there is that 23 page thread which contains all the fixes, guides and help of the ubuntu community to get cod4 working,
ahaslam (the guy who wrote most of the guides) hasnt been here for a while, but I am hoping he will make a quick guide on how to compile wine 1.0 for ubuntu 8.04 64 bit .

hope I help.

and cogadh I am going to try your solution for the pulseaudio thing soon...

---

### Post by cogadh on 2008-06-21
> **myromance123 said:**
> I see. Thanks for the link. By compile and patch wine yourself, do you mean there is no patch for the problem it gives?? I have to write my own code? Its not that I mind, but I dont know how to code just yet(newbie).

     Have you made your own patch already? does it have to be pc specific ?
Or could you share it with me :D

 Anyway,thanks for replying so very fast. Hopefully I can get cod4 running smoothly soon enough XD:KS
The patches you need to compile into Wine are linked to on that page I gave you. However, the thread thefishki345 gave you might be a better choice to follow, since it offers Ubuntu-specific advice.

thefishki345,
Please let me know how it turns out. I'm trying to come up with an updated "Stuff I've learned about Wine" document, and a usable PA solution is one thing I am missing.

---

### Post by myromance123 on 2008-06-21
Thanks for the swifty replies guys :)

     I'll post back as soon as I get it up and running :]

---

### Post by thefishki345 on 2008-06-22
cool, and cogadh, it didnt work sorry, but I didnt know where to put it in the command line. although the problem I am having not being able to run Multiplayer is because of my built in soundcard probably, and windows users are having the same problem...

---

