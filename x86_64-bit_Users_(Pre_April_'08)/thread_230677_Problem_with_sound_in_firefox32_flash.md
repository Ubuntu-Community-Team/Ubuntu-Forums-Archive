---
title: "Problem with sound in firefox32 flash"
date: 2006-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2006-08-06
I have a problem with simultaneous sounds with flash in firefox32.

This is what happens:
When I am watching something with flash audio (like youtube videos), and I make an artsplay (I use Kubuntu) to play a sound, like any sound from aMSN, the artsplay sound simply doesn't plays and it plays when the flash video is stopped.

WHen this happens, sound in flash brakes, and it will only work after some restarts.

This isn't really a big problem, but is very annoying, since I have to close the firefox windows quite regularly when watching youtube videos and talking in aMSN.

I have already tried to put 'aoss' in /etc/firefox/firefoxrc, but I don't think this helps firefox32, since it is a unpacked version of firefox.
I have also tried to load the firefox binary of firefox32 with the command 'aoss ./firefox', but I get this error:
```

ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

```

Every hint regarding to esd will not work on me because I use KDE and aRTS.

---

### Post by rogeriovinhal on 2006-08-11
up

---

