---
title: "[SOLVED] flv to avi converter"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-15
is there any for ubuntu ?

---

### Post by ad_267 on 2008-05-15
Try avidemux. The version in Gutsy didn't support flv but the latest version does, I'm not sure if this is included in Hardy or not.

---

### Post by ogregore on 2008-05-15
Not graphical -  however you can install mencoder

sudo apt-get install mencoder

then type

mencoder -oac copy -ovc lavc -o video.avi video.flv

for quick conversion (putting your file names to replace "video" above)

Cheers
Ogre

---

### Post by DachaArh on 2008-05-15
avidemux did a great job

thanks alot

---

