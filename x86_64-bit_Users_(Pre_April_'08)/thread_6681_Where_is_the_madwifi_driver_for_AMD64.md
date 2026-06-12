---
title: "Where is the madwifi driver for AMD64?"
date: 2004-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by JayBee on 2004-11-30
I read somewhere (I forgot where) that an atheros-based wlan card "just worked" out-of-the-box for a new Ubuntu user. 

It worked either using the LiveCD or the i386 installation (again, sorry for my lack of memory -- I have been reading a *lot* of stuff trying to get my card to work.)

Do we, the Ubuntu AMD64 loyals, have such a driver pre-built and ready for download from somwehere?

If not, does anybody have Ubuntu-specific instructions I can follow? I have already tried the Debian instructions (see the madwifi faq), and the readme from the code.

I will be happy to share the fruit of my CPU cycles.

---

### Post by jdong on 2004-11-30
[http://packages.gentoo.org/search/?sstring=madwifi](http://packages.gentoo.org/search/?sstring=madwifi)

Consulting the authority on AMD64 compat: madwifi: ~x86, -amd64

In short: no AMD64 support for MadWifi.

---

### Post by JayBee on 2004-11-30
Interesting.

The madwifi sources includes HALs for several architectures beyond x86 (x86_64 being one of them).

Gentoo may be choosing to build for x86 only. That may well be the case with Ubuntu as well. Then again, I don't know enough about the decision-making mechanics regarding builds, architectures, and packages of either project.

That being said, I have been able to compile the driver. Albeit with a lot of warning messages about unresolved symbols.
Recompiling the Ubuntu kernel with CONFIG_MODVERSIONS=n, as suggested by the madwifi faq, did not help. I may not be building the kernel as the driver needs it, even if my recompiled kernel works as expected after installing it & rebooting.

I will keep looking into this. But if anybody has any pointers, I (and future readers) will be very grateful if they posted/pointed to them here.

---

