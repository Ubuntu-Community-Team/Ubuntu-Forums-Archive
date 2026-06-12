---
title: "&quot;FGLTexMgrAllocMem failed&quot; error"
date: 2006-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-10-30
I was playing quake 4 succesfuly on linux for about a hour and a half when i starting getting extremely laggy, im talking 1 fp**m** (minute), i quit q4 and i have this error spammed in my terminal

> fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!


i didn't post this in the gaming and leisure forum becuase i think this goes beyond quake 4 and is a fglrx 64bit driver issue. I read something about mounting /dev/shm but i have no clue what they mean by that... if anyone can help it'd be greatly appreciated, I want to finish the game!!

---

### Post by kuja on 2006-10-30
It **IS** a fglrx issue. As far as I can gather from reading around, it's an issue with opening shared memory, which the FGLRX driver uses to communicate with other processes.

Try taking a look at [this page](http://www2.ati.com/drivers/linux/linux_8.16.20.html#176878), I'm not sure if it resolves the issue or not. You say it works fine for about an hour and a half, and then grinds to a screeching halt right? This sounds like a memory leak to me. Try again, and see if that's what it is.

P.S. Quake4 runs beautifully for me for as long as I'd like with the NVidia drivers :D

---

### Post by xstaticxgpx on 2006-10-30
well it runs fine except when a certain texture is drawn.

(after cain is turned into a strogg and he's in the walker thing, those blue link electric things that shoot up completely screw my fps)

---

### Post by xstaticxgpx on 2006-10-30
ahh, I think that site fixed my problem, I can't test it tonight, I have school tommorow, I'll test it when I get back and post the outcome. Ty kuja

---

### Post by xstaticxgpx on 2006-10-30
i sneaked a few minutes in and tested it, your link defenitly did fix it and im getting slightly better fps (i think, could be my mind playing tricks on me :)) ty kuja, again

---

### Post by kuja on 2006-10-30
Hey, no problem. Have fun :mrgreen:

---

