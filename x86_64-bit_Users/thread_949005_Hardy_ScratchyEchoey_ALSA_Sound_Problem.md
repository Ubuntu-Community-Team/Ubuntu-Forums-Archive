---
title: "Hardy Scratchy/Echoey ALSA Sound Problem"
date: 2008-10-15
forum: x86 64-bit Users
---

### Post by elemental11 on 2008-10-15
I just installed a fresh copy of Hardy on my dual boot hp m9350f, and any sound played is all scratchy or echoey sounding. I've tried installing the the new ALSA driver, utils, libs, etc. but I get errors when I try to execute make when installing the driver. Will installing new ALSA 1.0.17 fix the problem or is there something else I should try?

Here is the "make" error:
make[3]: *** [/home/df12/Desktop/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/home/df12/Desktop/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/home/df12/Desktop/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [compile] Error 2

It is an Intel HDA card

Thanks

---

### Post by renesisspeed on 2008-10-15
Not my fortay whatsoever, but when I had a similar problem (along with other audio problems as well) this post helped me out a lot.
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

