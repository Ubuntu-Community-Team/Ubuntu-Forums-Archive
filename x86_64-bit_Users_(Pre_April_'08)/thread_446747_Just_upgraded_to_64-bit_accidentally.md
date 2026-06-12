---
title: "Just upgraded to 64-bit accidentally"
date: 2007-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by insane_alien on 2007-05-17
So i had a bad exam, may have had a bit too much to drink and accidentally ordered parts for a new computer i wasn't planning on buying for a few weeks. anyway, i built the computer and installed the 32-bit kernel because i wanted to see if the speed difference was really what everyone says. now, my previous computer(relegated to the domain of my little brothers room, life expectancy: 1 week) was cutting edge in its time, crap now. so i was blown away by the change in speed already. i upgraded to the 64-bit version and i was sure i could see a blue tint from the doppler effect :P why the hell don't more people support this vast amount of speed?

one problem though, my bottom DVD drive won't open. i have another on top which works fine so its no biggy but it is annoying. i tested it on the old machine and it works. any ideas?

---

### Post by kuja on 2007-05-17
It won't open? That should be completely independent of the OS, best make sure it's plugged in.

On the other hand, sometimes in Linux it becomes difficult to eject the drive especially if something is using it. If the drive isn't empty (id est, there's something in it), try  something like "sudo eject /dev/hdc" assuming your bottom drive is /dev/hdc. Now, if that still does nothing, make sure nothing is using it by running "sudo fuser -cki /media/cdrom1" (assuming here that it mounts on /media/cdrom1)

(if for some reason you get a long list of processes potentially including process 1 when running fuser, don't kill it!!)

---

### Post by insane_alien on 2007-05-17
i don't get any processes

i'll give the connections a jiggle(real technical bit). theres nothing in the drive. i press the button the light flickers and nothing happens.

---

### Post by stmiller on 2007-05-17
type

eject

in a terminal

---

### Post by kuja on 2007-05-17
Oh, and while I'm at it, to test if it will eject (independent of OS), try to open/close the drive early in the bootup process, anytime before it tries to load the OS.

---

### Post by insane_alien on 2007-05-17
okay,i opened up my system gave everything a jiggle but to no avail, i replaced the drive with a spare and that one works.so its something about the drive when its used with the mother board. seperately they are fine. this ones confusing.

---

