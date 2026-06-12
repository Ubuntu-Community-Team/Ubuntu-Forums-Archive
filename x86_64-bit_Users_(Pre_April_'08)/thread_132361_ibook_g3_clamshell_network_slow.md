---
title: "ibook g3 clamshell network slow"
date: 2006-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flipper on 2006-02-18
hi!

I just installed Ubuntu on my ibook g3 366mhz clamshell, everything went smoth but i notice that the network is too slow like if its @ 10mb/s not 100mb/s , does anyone have this problem? i take about 15/20min to copy a 700mb file over the network :|

---

### Post by jdp on 2006-02-18
Go into a Terminal and use **ifconfig** to see the settings for the network adapters.  Somewhere it might show what the speed setting of the network is.  I'd guess that it's eth0.  For wireless you'd use **iwconfig**.  If you are going over wireless, it's limited to 11MBps.  For wired ethernet, you do have 10/100 on there.  Does it work at full 100 speeds in OS 9 or X?

---

### Post by Flipper on 2006-02-19
Yap it works in OSX and OS9 @ 100mb/s

I cant seem to find where does it say its @ 10 or 100 in ifconfig?

---

### Post by Flipper on 2006-02-19
help! :P

---

### Post by jdp on 2006-02-20
I just fired up my iBook 600, and ifconfig doesn't show the speed.  Turns out it's reported in dmesg though!
> [ 1420.777807] eth0: Link is up at 100 Mbps, full-duplex.
[ 1465.967942] eth0: Link is up at 100 Mbps, full-duplex.
[ 1465.967971] eth0: Pause is disabled
[ 1469.842704] eth0: Link is up at 100 Mbps, full-duplex.
[ 1469.842730] eth0: Pause is disabled
[ 1476.406075] eth0: no IPv6 routers present


 haven't done any speed runs, but both dmesg and the router report that it's connecting at 100.

---

