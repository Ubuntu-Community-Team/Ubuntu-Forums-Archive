---
title: "[Software]CD image extraction software"
date: 2006-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tinuz on 2006-01-24
I searched a bit but couldn't find anything. Is there any software around to extract CD images such as iso's and bin's?

---

### Post by FluffyElmo on 2006-01-24
*k3b* generally supports everything I've ever wanted to do with CDs, including creating ISOs. I can definitely recommend it. Just enable the Universe repository in Synaptic and you should be good to go for installing it. Also install all the recommended packages for the widest range of options.

If you don't want to install the KDE libraries *Gnomebaker* has some .iso creation support as well, just choose "Copy Data CD" and select create ISO only in the dialog.

Also, before doing any ripping or burning make sure you have DMA enabled on your drive. It will work without it, but slowly. My drive is at */dev/hdc* so adjust as needed:
```
sudo hdparm -d1 /dev/hdc
```

---

### Post by ChrisC on 2006-02-05
I'm also trying to simply copy an audio CD.  In Gnomebaker, clicking "Copy Audio CD" ultimately failed when I went to swap the discs -- it ejected the source disc, but then immediately pulled the disc back in and the operation failed.

[QUOTE=FluffyElmo]If you don't want to install the KDE libraries *Gnomebaker* has some .iso creation support as well, just choose "Copy Data CD" and select create ISO only in the dialog.[/QUOTE]

OK, so I figured I'd try the ISO route.  But Gnomebaker only has the "Create ISO" option for Data CDs (tried it, didn't work).  I'm trying to copy an audio CD, and there is no ISO option for that.  I guess there is no such thing as an audio CD ISO?

Help me copy an audio CD without installing KDE?!

P.S.  Also, if anyone knows a way of donating to this forum or Ubuntu Linux in general WITHOUT using PayPal, please let me know ...

---

### Post by ChrisC on 2006-02-05
Bad Ubuntu!  I wasted an hour on this, only to find:

Audio disc on Desktop -> right-click -> Copy CD

I'll open another thread.  This was a ridiculously Bad User Experience.

---

