---
title: "Deus Ex under playonlinux"
date: 2008-09-22
forum: Wine
---

### Post by GSZX1337 on 2008-09-22
I installed Deus Ex through playonlinux. It installed fine, but the game runs too fast. IIRC, the game also runs too fast in WinXP. If this problem also occurs in WinXP, can I just go into wine config and set the game to run in Win98?

---

### Post by jim_24601 on 2008-09-23
Deus Ex has problems with CPU frequency scaling on modern processors. You can turn off frequency scaling by disabling the powernowd daemon: see [this post]("http://ubuntuforums.org/showthread.php?t=739621").

---

### Post by GSZX1337 on 2008-09-23
I tried that, it didn't fix my problem. Any other ideas?

---

### Post by jim_24601 on 2008-09-25
The other thing you can try if a game is running too fast is to restrict it to one CPU core using schedtool. Look it up--I think you do 'schedtool -a1 program' to restrict program to CPU 0, but that's from memory. Mind, I also think I tried that with Deus Ex and it didn't work, but the powernowd approach did. YMMV.

---

