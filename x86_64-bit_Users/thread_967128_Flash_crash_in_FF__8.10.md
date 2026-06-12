---
title: "Flash crash in FF  8.10"
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by kayrune on 2008-11-01
I just installed a fresh 8.10, and flash 10. However I've noticed that flash sometimes crash and is replaced with a grey box. I've had this problem several times playing a youtube video in background and surfing. I usually happens when opening a new site or loading a site in a background tab.

---

### Post by kayrune on 2008-11-04
I can reproduce this every time now, play a youtube video, open another tab with another youtube video and the first turns into a grey box.

---

### Post by istblacken on 2008-11-04
this is a known issue, at least it happens to me on both 32 and 64 bit ubuntu os since flash 9 and it is not fixed in flash 10 neither. workaround for this is opening only 1 flash containing tab at one time or you can use flash blocker for other sites except the one you want the flash content to be playing.

---

### Post by kayrune on 2008-11-04
Unfortunatly I've installed flashblock in FF, and it doesn't help :confused:

This is def a 64bit issue though, looking @ dmesg after it happens:

```

[17570.444674] npviewer.bin[3112]: segfault at 4 ip 00000000f6b7876c sp 00000000ffc454e0 error 4 in libflashplayer.so[f68d0000+951000] 
```

---

### Post by istblacken on 2008-11-05
i was searching a bit more on this issue and i came across to this [https://bugzilla.redhat.com/show_bug.cgi?id=439858](https://bugzilla.redhat.com/show_bug.cgi?id=439858)
it seems linus torvalds have this bug too lol
and still i haven't found any solution to this issue but as you pointed out in your previous post it is most likely related with ndiswrapper...

---

### Post by fignig on 2008-11-05
dual boot w/ windows, best suggestion evar!

or u could just switch back, i'm about to.

---

