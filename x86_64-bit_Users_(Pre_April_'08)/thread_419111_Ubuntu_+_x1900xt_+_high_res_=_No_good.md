---
title: "Ubuntu + x1900xt + high res = No good"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by toronkusu on 2007-04-22
Linux has never been friendly too me. Its always been a disaster getting driver and now it seems no different.

I have:
ABIT AN8 SLI Mobo
AMD 64 3200+
2GB DDR 500 OCZ Platinum RAM
ATI Radeon X1900XT 512MB

When i use the Ubuntu config I can only get into the OS if i select vesa as a driver and i dont push the res over 1280 or so.  Anymore than that i cant get in. I tried installing the new drivers by using envy, and that didnt work either.  I really dont know wwat to do.  When I select ati instead of VESA it says "no device found" and it kicks me back to the command line.

I really dont know what to do at this point.

---

### Post by FiggyG on 2007-04-22
Go to [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) and select Ubuntu, your version... I use Method #2 to install the fglrx drivers from AMD. PM me if you have troubles with using aticonfig and I'll help ya out, then post the fixes for your problem here. I have an X1600XT & a 19" LCD running 1440x900.

---

### Post by toronkusu on 2007-04-23
I think I love you.

Fixes:
Well I did exactly what you said.  It was that simple.  I didnt execute those extra commands to compile the kernel, but everything looks good.

Thanks so much.

---

