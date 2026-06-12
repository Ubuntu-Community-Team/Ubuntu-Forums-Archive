---
title: "Titanium 1Ghz - but CPU runs only at 667 Mhz"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by koni2005 on 2005-12-05
After installing Ubuntu, besides some trouble with the ATI graphics driver for my radeon 9000 Mobility, I stumbled over another weird thing:

Somehow my CPU is only running at 667 Mhz.

In KIfnoCenter, it says:

CPU: 7455, altivec supported
clock: 667 MHZ

Can I set it to 1Ghz?

thanks...

---

### Post by ssam on 2005-12-05
it should step up to 1ghz when you need it.

gnome has a cpu monitor applet that will show you the speed, or run
```
watch -n 1 cat /proc/cpuinfo
```
in a terminal, and shake some windows around/open a large application.

---

### Post by spaceballl on 2005-12-08
hehe that's a cool feature :-)

---

