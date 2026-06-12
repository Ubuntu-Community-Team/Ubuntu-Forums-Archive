---
title: "X.org eats memory like free chips."
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by sorhed on 2008-04-24
Hello everyone,

I've got myself a brand new Thinkpad T61p with 4G RAM and 1920x1200 screen, installed Hardy-amd64 and disabled swap space completely (I always wanted to do it). Of course, I've enabled every (still reasonable) eye candy feature in compiz.

I understand that X in these conditions can be somewhat memory hungry, but according to top, now it uses 2.3G RAM (I am a Java developer, so I've got IDEs, browsers, test applications and all other stuff launched). I can account for everything, but 2.3G just for X.org? Why? Is it normal? For G-d's sake, how can every pixmap imaginable take 2.3G?

OK, maybe X is smarter than me, and somehow is using all available memory just in case. I just want to know is it normal or not.

Sorry for my less than perfect English, I am Russian living in Switzerland.

---

### Post by soxs on 2008-04-24
It is definitly not normal. When I run compiz with extra effects, I get Xorg eating about 120 MiB of Ram (out of 4 GiB)
Do not aksk me how to fix it, I have no clue what is going up, but a first step is to throw some info in. (GPU, driver, /etc/X11/xorg.conf, Xorg.0.log)

---

### Post by Major_Kong on 2008-04-26
Memory leaks. The only solution i know is disabling compiz.

---

