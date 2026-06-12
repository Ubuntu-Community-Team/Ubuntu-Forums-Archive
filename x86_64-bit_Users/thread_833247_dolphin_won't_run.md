---
title: "dolphin won't run"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by ministoat on 2008-06-18
whether it's related or not, i noticed this problem after a kernel update yesterday..

I can't run dolphin at all..i've tried reinstalling and no joy.

dolphin cash says: 

[KCrash handler]
#5  0x00007f4243a92095 in raise () from /lib/libc.so.6
#6  0x00007f4243a93af0 in abort () from /lib/libc.so.6
#7  0x00007f4243acca7b in ?? () from /lib/libc.so.6
#8  0x00007f4243ad4a14 in ?? () from /lib/libc.so.6
#9  0x00007f4243ad6360 in malloc () from /lib/libc.so.6
#10 0x00007f4243e865ed in operator new () from /usr/lib/libstdc++.so.6
#11 0x00007f42421cc4da in ?? () from /usr/lib/libQtXml.so.4
#12 0x00007f42421cd233 in QDomDocument::createElement ()
   from /usr/lib/libQtXml.so.4
#13 0x00007f4245d1ca4a in ?? () from /usr/lib/kde4/lib/libkio.so.5
#14 0x00007f4245d1cdc9 in KBookmark::setMetaDataItem ()
   from /usr/lib/kde4/lib/libkio.so.5
#15 0x00007f42459871d6 in ?? () from /usr/lib/kde4/lib/libkfile.so.4
#16 0x00007f424598ac3e in KFilePlacesModel::KFilePlacesModel ()
   from /usr/lib/kde4/lib/libkfile.so.4
#17 0x00007f42454cb4f7 in DolphinSettings::DolphinSettings ()
   from /usr/lib/kde4/lib/libdolphinprivate.so.4
#18 0x00007f42454cb606 in ?? () from /usr/lib/kde4/lib/libdolphinprivate.so.4
#19 0x00007f42454cb6d0 in DolphinSettings::instance ()
   from /usr/lib/kde4/lib/libdolphinprivate.so.4
#20 0x0000000000423887 in _start ()
#0  0x00007f4243afdb50 in nanosleep () from /lib/libc.so.6



i also am having audio troubles if thats of any relevance to this, crash log unavailable until the next time it shows up :P


This is really annoying because all my music is on an ntfs drive, and (yes you guessed it, i'm a noob) unless i browse this drive in dolphin, i can't play the music on it. if anyone reading know a way around that, it would be great too :)

thanks

---

### Post by ministoat on 2008-06-18
i'm not goin to mark this solved yet, but an error message asking me to disable aRTS sound popped up..once disabled doplhin worked! what's that all about? :/

---

