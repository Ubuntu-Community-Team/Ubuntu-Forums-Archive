---
title: "Rendering Method?"
date: 2009-06-07
forum: x86 64-bit Users
---

### Post by gogreenpower on 2009-06-07
does anyone know how to fix this? i've tried editing my xorg.conf file but no luck...

kane@desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by philinux on 2009-06-07
Is that a legacy xorg from an upgrade?

Also have a search for ati, fglrx etc on the forums. This came up.

[http://ubuntuforums.org/showthread.php?t=546756](http://ubuntuforums.org/showthread.php?t=546756)

I use nvidia but I know ati is a pain from what I've seen on the forums.

---

### Post by gogreenpower on 2009-06-07
no its a fresh install with manually installed drivers. the driver install fine, i just need to know if there are options to enable the rendering method?

---

### Post by gogreenpower on 2009-06-08
bump

---

### Post by Yellow Pasque on 2009-06-09
Look at /var/log/Xorg.0.log and see why AIGLX failed to enable. Make sure you installed the driver properly (i.e. no Mesa/Software Rasterizer in your glxinfo):
```
LIBGL_DEBUG=verbose glxinfo
```

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by gogreenpower on 2009-06-09
there is no EE errors in it and thats about the limit of my knowledge, heres some copys of the outputs. i follow that link to the letter and had no errors returned

---

