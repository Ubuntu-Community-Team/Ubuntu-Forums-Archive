---
title: "Mplayer doesn't resize"
date: 2005-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by mozzi on 2005-12-21
Hello all

I have mplayer on Kubuntu breezy upgraded to kde 3.5.
Installed mplayer, when running mplayer from the commandline
#mplayer movie.avi it works perfectly but when I hit "f" for full screen the picture stays the same size, small in the middel of this huge blackness.
It worked perfectly under Suse10.0 oss.

Mozzi

---

### Post by codejunkie on 2005-12-21
[QUOTE=mozzi]Hello all

I have mplayer on Kubuntu breezy upgraded to kde 3.5.
Installed mplayer, when running mplayer from the commandline
#mplayer movie.avi it works perfectly but when I hit "f" for full screen the picture stays the same size, small in the middel of this huge blackness.
It worked perfectly under Suse10.0 oss.

Mozzi[/QUOTE]
you need to adjust the video settings in mplayer and set the video driver to xv and restart mplayer that worked for me.

---

### Post by mozzi on 2005-12-21
[QUOTE=codejunkie]you need to adjust the video settings in mplayer and set the video driver to xv and restart mplayer that worked for me.[/QUOTE]

Thanx setting driver to xv worked for me

---

### Post by cvmostert on 2006-11-11
thank you, xv worked for me too. I know this thread is almost dead... just thought i give my 2c.

---

### Post by BlackBaron1024 on 2008-07-05
Actually, it doesn't work for me. If select xv as the video driver, I get the following error message:

> Error opening/initializing the slected video_out (-vo) device

I think it has something to do with my video car driver (I have an ATI Radeon Mobility x1300), and I don't think I can fix it until a newer (better) driver is released.

Does anyone knows any workaround?

Thanks (and sorry for resurrecting an old post).

P.S. I have 32-bit, but I don't think that makes any difference.

---

### Post by sisco311 on 2008-07-05
> **BlackBaron1024 said:**
> Actually, it doesn't work for me. If select xv as the video driver, I get the following error message:



I think it has something to do with my video car driver (I have an ATI Radeon Mobility x1300), and I don't think I can fix it until a newer (better) driver is released.

Does anyone knows any workaround?

Thanks (and sorry for resurrecting an old post).

P.S. I have 32-bit, but I don't think that makes any difference.

Try to rum mplayer with the -zoom option:
```
mplayer -zoom file.avi
```
If works add *zoom=1 *to the ~/.mplayer/config file.

---

