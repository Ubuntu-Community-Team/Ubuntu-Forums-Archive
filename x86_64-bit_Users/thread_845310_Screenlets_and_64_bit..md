---
title: "Screenlets and 64 bit."
date: 2008-06-30
forum: x86 64-bit Users
---

### Post by stchman on 2008-06-30
Hello all, since upgrading to 64 bit Hardy I have been using Screenlets.  I was using gDesklets, but they have compatibility problems with 64 bit.

My problem is that when I start the PC only SOME of the screenlets load.  It is random as they all load sometimes and sometimes not.  They also don't stick to all desktops even though I have locked, sticky, and always below checked.  I do notice that if I disable Compiz that they function better.  Is there a fix?

Screenlets are just eye-candy, so they are not crucial to my PC usage.

Thanks.

---

### Post by jerome1232 on 2008-06-30
I have the same problem, Hardy x86_64 testing out the suggestion in this post right now will restart a few times and see if settings are preserved.
[http://forum.compiz-fusion.org/archive/index.php/t-4162.html]("http://forum.compiz-fusion.org/archive/index.php/t-4162.html") 
with a slightly modified script (my files were all in /usr/share/screenlets
instead of the suggested /usr/local/share/screenlets)

```
#!/bin/bash
compiz --replace &
sleep 5
emerald --replace &
sleep 5
/usr/share/screenlets/MyIp/MyIpScreenlet.py > /dev/null &
/usr/share/screenlets/Clock/ClockScreenlet.py > /dev/null &
/usr/share/screenlets/Slideshow/SlideshowScreenlet.py > /dev/null
```

---

### Post by jerome1232 on 2008-06-30
No go, only the clock and sideshow even load, clock doesn't seem to keep the 'sticky' attribute :(

---

### Post by stchman on 2008-06-30
I am convinced that screenlets using Compiz is spotty.  Thank you for your efforts.

---

