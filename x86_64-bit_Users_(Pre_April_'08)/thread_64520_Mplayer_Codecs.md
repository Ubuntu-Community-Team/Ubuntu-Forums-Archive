---
title: "Mplayer Codecs"
date: 2005-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by zupermanz on 2005-09-11
Mplayer used to play sites like mms://209.190.4.99/alter (that is mms streams)
Now i get only sound... Any ideas?
I didnt had that problem with 32 bit version...
Thanks in advance

---

### Post by negatory on 2005-09-12
That's because it's a proprietary format of windows media player.In a 32bit system you've got the w32codecs package that you can install but in a 64bit that simply isn't possible.But you can chroot a 32bit mplayer and everything will work again.
Hope that helps!
Pedro Carrico

---

### Post by Conq on 2005-09-12
Follow this howto: [http://ubuntuforums.org/showthread.php?p=334873#post334873](http://ubuntuforums.org/showthread.php?p=334873#post334873)

---

### Post by zupermanz on 2005-09-12
thanks! it worked!

---

