---
title: "Intrepid Diablo II: Insert Install Disc?"
date: 2008-11-02
forum: Wine
---

### Post by cereal killer on 2008-11-02
D2 keeps telling me to insert the install disc over and over? Didn't have this issue on Hardy. Using Wine 1.1.7

---

### Post by sk8ordie97 on 2008-11-03
try a nocd

---

### Post by cereal killer on 2008-11-03
Looks like it has something to do with the bugfest that Intrepid is and maybe related to the eject -> reinsert bug many have been having with their disc drives. I installed Warcraft 3 fine, but then it tells me it doesn't detect a CD-ROM drive...while I launch it from autoplay menu.

I hope this gets patched soon, this is ridiculous.

---

### Post by cereal killer on 2008-11-03
Ok, turn outs this was an issue with Wine 1.1.7. I rolled back to 1.1.5 (the last one I used before upgrading) and everything is perfect.

---

### Post by IamJester on 2009-02-01
I had the same problem.  The issue is that wine doesn't recognise the cd drive.  You need to go into the wine configuration, click on the "drives" tab, add drive and give the location of the mounted cd drive (in my case /media/cdrom0) then it should work.  Autodetect in the drives tab might work too.

I think it's not an issue of the version of wine, but rather an issue of whether there was a cd in the drive when wine was installed (it autodetects settings when it installs).

Hope this helps.

---

