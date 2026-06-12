---
title: "will force feedback work in games in wine?"
date: 2008-10-05
forum: Wine
---

### Post by jyaan on 2008-10-05
I'm thinking about buying a Logitech Rumblepad 2, but will the force feedback work under Wine? Or should I just get the plain version? Thanks.

---

### Post by jyaan on 2008-10-05
Buying tonight online (building computers for my family). Help?

---

### Post by DaVince21 on 2008-10-06
If I remember correctly it does work (with my PS2 controller + USB connector), but I'm not completely sure since it's been a while since I tried a Windows game in Wine with force feedback support.

---

### Post by holmes0 on 2008-10-07
It will probaly work but only if you recompile your kernel with the good option. The default kernel has no force feedback support so far.

See here for the correct configuration:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246952)

and here for wine:
[http://wiki.winehq.org/ForceFeedback](http://wiki.winehq.org/ForceFeedback)

Good luck

---

### Post by jyaan on 2008-10-16
Thanks

---

### Post by jyaan on 2008-10-16
I bought the gamepad by the way; It's already arrived :)

I've compiled my own kernel many times in the past, but that was on Gentoo. I'm wondering how I should make the headers available (vmware and nvidia drivers need to build modules), but I'm guessing that consists of merely extracting a tar into the directory since uname would have been updated anyways.

Any quick guides? Thanks again.

---

### Post by holmes0 on 2008-10-16
There is a guide in the community documentation but it is not very clear (at least to me).

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I managed to compile a kernel with force feedback support but with no sound and no wifi.
If you manage to do it correctly, I would appreciate if you could explain how you did it.

Good luck

---

### Post by jyaan on 2008-10-17
Thank you, I will let you know the results. 

Regarding a lack of sound and wifi, this must mean that you are missing the corresponding modules. A good place to look regarding the actual kernel configuration menu (make menuconfig) is in the gentoo documentation.

For sound, you need both the alsa and oss (if you want oss support; games like rtcwolf and other id games rely on oss) modules, as well as the module for your sound chipset. These need to be built, but alsa *should* auto-load them for you, mean you don't need to add that to the loaded modules list. Again, the gentoo doc can be helpful -- but especially alsawiki.

Regarding wifi, I unfortunately have no experience. Just make sure both the chipset module and wifi capability module(s) are set.

Sure, this is ubuntu but the gentoo docs are often just as useful as the ubuntu ones, especially when it comes to things involving compilation.

---

### Post by stan.distortion on 2009-07-15
Quick note, on debian systems read up on "kernel-package" for compiling kernels. As to documentation, I'll second the above post, the gentoo kernel doc's are very good (there are a few of them with varying depth). Also google a few howto's, there will be at least one that makes sense and probably quite a few that target exactly what you need.
cheers

---

### Post by holmes0 on 2009-07-23
Hi,

Since 9.04 (and kernel 2.6.28), it is no longer necessary to compile a custom kernel. Force Feeback support is from now on a standard feature. I have personnaly tested it with a Sidewinder Force Feedback 2 using ff-utils and gforce (a ff testing application with a GUI). It works perfectly. It appears Sidewinder support is no longer experimental since I don't have any more freeze as it used to happen with previous kernels.

Now we have to wait for the next SDL 2 (with a FF API) which is now the single element lacking for a FF support within Freespace SCP!

Hope it will come soon ...

---

