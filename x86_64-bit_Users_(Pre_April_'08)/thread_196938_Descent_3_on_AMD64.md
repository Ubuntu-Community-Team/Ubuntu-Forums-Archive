---
title: "Descent 3 on AMD64?"
date: 2006-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by abeowitz on 2006-06-15
I just successfully setup Ubuntu AMD64 on my Shuttle SN25P, which went quite flawlessly.  I have switched to the nvidia drivers, to support my nvidia video card.  The OpenGL screensavers work quite nicely now.  :)

Anyway, tried to setup Descent 3, which is an old Loki game, 32 bit, of course.  

Here's the message I got:

```
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at support(a)lokigames.com
```

I'm afraid to force arch to i386 for glibc-2.x, as it may overwrite my 64bit version.

Other than chroot, is there a way to install a set of 32bit libs to run this game?

Thanks in advance!

---

### Post by Hentai_Jeff on 2006-06-15
I wanna know where you found it. I'd love to have not only decent 3 but the other 2 descents on linux :D

---

### Post by abeowitz on 2006-06-15
Well, I learned about linux32 and got it to install.  Now it's failing on libGl.so, but I think I saw something about some env variables I can set to point to the 32 bit versions...

Hentai Jeff - I bought it retail years ago.  Never got it to work right on my ATI laptop till I installed Ubuntu last year.  Then it worked perfectly!  :D

Lessee if I can get it to run on my nvidia desktop!

---

### Post by abeowitz on 2006-06-15
Well, this does the trick!  :D

linux32 /usr/local/games/Descent3/descent3 -c -g /usr/lib32/libGLU.so.1

Sorry for the lame thread...  :rolleyes:

---

### Post by Kilz on 2006-06-15
[QUOTE=Hentai_Jeff]I wanna know where you found it. I'd love to have not only decent 3 but the other 2 descents on linux :D[/QUOTE]
Check out these pages for the Descent and Descent 2. The games were my all time favorites.
[http://d1x.warpcore.org/](http://d1x.warpcore.org/) and [http://www.dxx-rebirth.de/](http://www.dxx-rebirth.de/)
[http://www.icculus.org/d2x/](http://www.icculus.org/d2x/)

---

