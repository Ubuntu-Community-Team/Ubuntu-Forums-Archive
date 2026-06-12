---
title: "Beryl/ compiz not working on amd64 with intel946gz"
date: 2007-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammy_pal on 2007-04-07
Neither beryl nor compiz is working on my Intel Core2Duo E6300 with Intel 946GZ mobo(with integrated graphics).
Screen becoming white/blank on starting beryl. I have to restart the xserver after that, otherwise nothing works.
Please help me.:confused:

---

### Post by slowcoach on 2007-04-07
Exactly the same here using a GeForce 6200 and the nVidia proprietary driver, I guess something is buggered. :(

---

### Post by ubonetu on 2007-07-27
I found that if you follow this HOWTO:

[http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html)

And then, if you do lock up white, reboot and use this:

```
beryl-xgl --use-copy
```

You'll have Beryl back on, now just open the Beryl Settings Manager from Applications:System Tools and go to Advanced Beryl Options under the icon and choose Rendering Path: Copy.

That should save the day...

bones

---

### Post by ahchong on 2007-08-01
em.. i just try instal my ATi driver restricted. Compiz cannot been use, even worse, the ubuntu become lag, video lag, program lag, also in typing, uninstalled it, then compiz can be use again.... very bad:(

---

