---
title: "moved to a different cable provider-&gt;mythtv reception=static"
date: 2006-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2006-09-25
Hey, I had a working mythtv installation, ivtv based PVR-150's.  I moved and now the reception is really bad.  I have switched from us-cable tuning frequencies to us-cable-hrc and us-cable-irc and back.  Nothing will get it to tune properly, my girlfriend's old TV works just fine, so this isn't an exotic cable system, what am I missing?  I can vaguely see the channel through the static, so I don't see how it can't be showing me the image in full.

---

### Post by rosbif on 2006-09-25
Sounds like a hardware/connection problem.  When you moved, did your myth box get knocked about?  You may have to reseat cards etc.  Other things:
- what does dmesg say, esp in the ivtv section?
- can you see channels just using ivtv and mplayer (or your fav. media player)?
Try (without mythtv running)
mplayer -vo xv /dev/video0
ivtv-tune -c <channel-number> -d /dev/video0

where <channel-number> is one of your valid channels

---

