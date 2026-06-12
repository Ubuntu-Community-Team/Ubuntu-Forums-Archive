---
title: "Stablility issue"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by defenestratos on 2007-11-04
Basically I dig Ubuntu and am tantilisingly close to realising my dream system with this distrib, but bei mir it is just totally crashy. I have
-choppy audio in Amarok
-no desktop effects (Is this because I have no graphics acceleration?)
-a little crashy

Put it down to my lack of knowledge about Ubuntu if you like, but hey, that is why I humbly ask my friends at the Forum for help.
Please could you tell me how I can make my 64 bit Ubuntu system as solid as possible.

---

### Post by scotthammy on 2007-11-04
[COLOR="DarkGreen"]Well im a newbe myself, but looking at your forum sig only 512 ram? Ram is very cheap nowadays maybe abit more ram would fix the choppy audio?[/COLOR] :guitar:

---

### Post by zekopeko on 2007-11-04
try checking your RAM with the memtest86 (it is in the GRUB OS loader when you start the 
system). run it at least for 3-4 hours and see if there are any errors. if any replace the RAM.
aslo reinstalling might help is the RAM isn't the problem. sometimes the installation gets messed up in a small way and messes the entire system. 
just have /home separate from /

EDIT

512 MB RAM is enough for gnome. it isn't going to fly but that's not a problem if you have 1GB of swap.
The only reason that you need 320MB RAM for installation with live CD is because it loads a lot off system in RAM. you need less to use it when you install it

---

### Post by John.Michael.Kane on 2007-11-04
Regarding system stability it will take some debugging on your part to find out why you are having these issues. 

Also it it would help if you told us what you where doing with the system at the time of the crashes or lockup etc. 

You should also be able to find out if the event was loged by looking in /var/log/crash .

As for the S3 Unichrome Pro VGA Adapter 64mb in the system you are running. That particular gpu is not supported by desktop effects/compizfusion. To run desktop effects eg:compizfusion you need gpu made by one of the companies below.

ATI
Intel 
NVIDIA

Regarding choppy audio in Amarok you can try the link posted here.
[ Audio playback seems choppy. What causes this? Is there anything I can do?]("http://amarok.kde.org/wiki/FAQ#Audio_playback_seems_choppy.__What_causes_this.3F_Is_there_anything_I_can_do.3F")

---

### Post by defenestratos on 2007-11-21
Thank you everybody. I now have 1,200 megs ram. I have worked out that Amarok doesn't work at all really and uses seventy percent of my cpu just being open. What is really needling me now is the total crashability of both F-spot and Picasa. Picasa will not even start.

---

