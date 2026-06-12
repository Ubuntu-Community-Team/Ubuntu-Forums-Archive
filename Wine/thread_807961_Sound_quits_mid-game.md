---
title: "Sound quits mid-game"
date: 2008-05-26
forum: Wine
---

### Post by javafiend on 2008-05-26
Wow, looks like a lot of folks are having sound issues, but since I didn't see mine, I figured I'd post my own thread on the subject.

Anyway, I play EQ2, which runs pretty well on Wine, and after I've been playing for a while my sound just quits.  If I shutdown the game and restart it it's fine.  I haven't tried using sound from other applications when the sound quits, but once the game is stopped the sound seems to be working fine.

I'll try sound from other applications next time this happens and will post my observations.

---

### Post by k@e on 2008-05-27
Since the few latest releases of Wine, I've been having exactly the same problem. The sound would just drop after a while, mostly because of screen changes.

Anyway, to work around this I've set the audio hardware acceleration in winecfg to "emulation". This might reduce the audio quality of your Windows apps but it's better than having no sound at all.

---

