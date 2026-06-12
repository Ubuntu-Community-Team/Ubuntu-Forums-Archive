---
title: "Low FPS with Wine 53"
date: 2008-01-20
forum: Wine
---

### Post by samurailink3 on 2008-01-20
I'm getting a low FPS in Source Engine games using wine 53, but when I force version back to 46, my FPS returns to normal. Any ideas?? I can use 46, but I was wondering if anyone had any ideas or bugfixes?
Thanks!

---

### Post by midkin on 2008-01-20
i have installed the latest version of wine for my system(ubuntu 7.10 gutsy), the last nvidia drivers for my graphic card(169.07 for linux64), the latest version of directX(nov2007) and when i run CSS through wine i get 40-50 fps...the game is playble but with low fps and stucks at times... I was getting like 100 fps when i had windows xp installed..
Any ideas?
Thanks

P.S. sry for posting here but my problem is simmilar to yours.

---

### Post by midkin on 2008-01-20
if that helps you:

$ glxgears

```
44671 frames in 5.0 seconds = 8934.164 FPS
43985 frames in 5.0 seconds = 8796.953 FPS
44463 frames in 5.0 seconds = 8892.578 FPS
44912 frames in 5.0 seconds = 8982.390 FPS
44173 frames in 5.0 seconds = 8834.512 FPS
43970 frames in 5.0 seconds = 8793.872 FPS
42436 frames in 5.0 seconds = 8487.173 FPS
43710 frames in 5.0 seconds = 8741.991 FPS
44880 frames in 5.0 seconds = 8975.825 FPS
44886 frames in 5.0 seconds = 8977.143 FPS
44486 frames in 5.0 seconds = 8897.107 FPS
44799 frames in 5.0 seconds = 8959.635 FPS
44445 frames in 5.0 seconds = 8888.909 FPS
42180 frames in 5.0 seconds = 8435.860 FPS
44694 frames in 5.0 seconds = 8938.653 FPS
```

---

### Post by hikaricore on 2008-01-20
glxgears results are not really beneficial to this topic..

---

### Post by midkin on 2008-01-20
Sry I just want to find a way to increase my frames on CSS...I get half of what my hardware is capable to get.
I dont know where and what to post...i need some help!

---

### Post by The Noble on 2008-01-20
I have not seen the exact problems you are having with 53, but there are some slight graphical glitches that were not there before. Try reverting 52 for the time being. If you want to help solve the problem go to winehq and check the bug reporting system they have in place. Search before you post anything; you don't want to spam them.

---

### Post by Vadi on 2008-01-20
The thing is that wine started implementing some fancy graphical things directx uses. Before, it would simply ignore them, which resulted in less work to do, and subsequently higher FPS.

So technically, you're supposed to be seeing better graphical effects... although if that's not the case, just tone down the settings in-game.

---

### Post by samurailink3 on 2008-01-20
Allright, I think I'll just keep 46 for now, and wait until the graphicals fixes are better optimized. Thanks for the info!

---

