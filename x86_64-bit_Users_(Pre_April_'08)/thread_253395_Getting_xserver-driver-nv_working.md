---
title: "Getting xserver-driver-nv working"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by anahata on 2006-09-08
My CD install on a 64 bit system has put in a VESA X driver. It goes up to 1024x768 max, and I'm sure the Nvidia graphics system (built in to the motherboard) can handle higher resolutions, and I know the LCD monitor can go up to 1200, so I'm guessing that I could get the higher resolution by switching to the NV driver.

$ sudo apt-get install xorg-xserver-driver-nv

says it's already installed.

- Does this mean the nv driver won't work with my particular hardware?
- Is there an autodetect program that would show me what is going on?
- or is there a way of telling the server to use the NV driver (other than manually editing tons of stuff in xorg.conf which I won't get right)

Anahata

---

### Post by kuja on 2006-09-08
Strange, nv is usually the default for systems with nvidia cards, but trust me, it's not all that great.

It's not open source, but nvidia's proprietary driver does deliver good performance.

Anyhow, that's likely all besides the point, X probably didn't detect your monitor correctly. In a terminal, run this command:
```

sudo dpkg-reconfigure xserver-xorg

```

The last section of this deals with monitor settings, particularly monitor resolution!

---

