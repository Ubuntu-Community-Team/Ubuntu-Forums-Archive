---
title: "anyone have amarok working with ipod on breezy"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by shawn12345 on 2006-01-15
all i get are japanese characters in the list for the media device, or it cant find the device. tried two different ipods formated 2 different ways.

amarok via apt-get version is 1.3.1 

thanks

---

### Post by shawn12345 on 2006-01-15
opps also obviously i mean on ppc also.


thanks

---

### Post by Stormy Eyes on 2006-01-21
Amarok expects your iPod to mounted on /mnt/ipod. So do **sudo ln -s /media/ipod /mnt/ipod** and you should be all set. You have to mount it first before Amarok can connect to it, though.

---

### Post by dombleu on 2006-01-21
Alternatively Rhythmbox works like a charm with my ipod...

---

### Post by shawn12345 on 2006-01-23
Hmm i tried that, i had a symbolic link to /mount from /media so it all should have carried through. It saw the ipod but just got mess when plugged up. I will try it again, i was mostly curious if it was working for anyone on ppc so i knew if i should spend more time on it or not.

Rhythmbox works for me, can't remember what functions...i didn't use it long because the library was slow. Amarok's rdbms backend is what i was looking for
with a large library and so could access the database with scripts.

I'll try amarok again.

thanks! - shawn

---

### Post by jetpeach on 2006-01-23
[QUOTE=dombleu]Alternatively Rhythmbox works like a charm with my ipod...[/QUOTE]
From what I've read and tried, Rythmbox (at least 0.9.1) only lets you play music from your ipod, but you cannot transfer music to it.

---

