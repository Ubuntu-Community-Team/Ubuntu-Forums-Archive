---
title: "sound crashing my system"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by billrad1 on 2009-11-07
ok, I have a new machine, athlon 64 dual core with 8 gigs corsair ram, nvidia 9500 1 gig video, and built in HD 8 channel audio on an asus motherboard.


everything is running good, but sound keeps crashing my system.

history:

installed flash 64 for firefox to see videos, all works, however...after a while watching videos, like youtube, system locks up 

sound was not right, only two of four speakers working, wrong balance etc.

also, in flightgear application, sound was buggy and staticy, so I removed all traces of pcm audio, and use  alsa exclusively.  Flightgear has excellent sound now, but after a couple minutes, locks up the desktop. (same as before).  speakers all work great now.

also, after going to alsa exclusively, startup sound sounds like it is on fast forward...


I am looking for HOW to figure this out, as well as a solution

thanks

billrad1

> /proc/asound/card0/codec#0:Codec: VIA VT1708B 8-Ch
/proc/asound/card0/codec#0:Vendor Id: 0x1106e721
/proc/asound/card0/codec#0:Subsystem Id: 0x104382ea
/proc/asound/card0/codec#0:Revision Id: 0x100100
  

>  0 [SB     ]: HDA-Intel - HDA ATI SB
                       HDA ATI SB at 0xf7ff4000 irq 16
        1 [Camera ]: USB-Audio - PC Camera
                       V Micro. Corp. PC Camera at usb-0000:00:12.0-3, full speed
  

---

