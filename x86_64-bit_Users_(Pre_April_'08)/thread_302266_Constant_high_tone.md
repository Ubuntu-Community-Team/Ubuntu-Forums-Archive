---
title: "Constant high tone"
date: 2006-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by vidar_nelson on 2006-11-18
I've got a problem with my VIA HDA soundmax sound card on my new desktop computer. I do get sound, but in addition to that, I also get a constant, high pitched tone that really destroys my ears. If I try to change the PCM volume the tone goes away but sadly, so does all the rest of the sound too. The only thing I can come up with to get it back is to reboot.

[Edit: I've Reinstalled ubuntu, and the problem persist]

Running amd64 ubuntu.


Thankful for replies!

Vidar

---

### Post by vidar_nelson on 2006-11-23
Just wanted to add two things:
1. The sound work in windoze, so it's not a hardware problem
2.*bump!* (realy don't want my ubuntu system to bee unusable just becouse of this problem :()

---

### Post by Sukarn on 2006-11-24
I am getting the exact same thing. Sound is working on my windows installation, but not on ubuntu. I have to add though, drivers were supplied on CD for Windows.

---

### Post by yanewby on 2006-11-24
I have (or should I say had) the same problem as you where a high pitched tone was played at the same time as any other sound.

I can take no credit for this answer as I simply followed the instructions here:
[http://ubuntuforums.org/archive/index.php/t-260352.html]("http://ubuntuforums.org/archive/index.php/t-260352.html")

In summary, type sudo gedit /etc/modprobe.d/alsa-base in a terminal (and type in your password as we are using sudo).

This will open up gedit with the file (/etc/modprobe.d/alsa-base) open in it.  Simply add the following line at the bottom (where there may be some other lines beginning with "options"), don't delete anything else just add this line:

options snd-hda-intel position_fix=1 model=3stack

Reboot your computer and hopefully the high pitched tone will have gone, it worked for me!

---

### Post by vidar_nelson on 2006-11-25
yanewby:
I LOVE you!
Thanks a lot.
:KS :KS :KS :KS :KS

---

