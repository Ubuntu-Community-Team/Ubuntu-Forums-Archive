---
title: "duplicate symbol rol_long - breezy AMD64 - ATI X700"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by nbhaskar on 2006-01-03
While booting up my system I get the error message and I checked my /var/log/Xorg.0.log file and found the following

```
loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a
```

I can only work on command line, gdm fails.

Does this ring a bell linux gurus?

Thanks in advance for any help.

:o

---

### Post by nbhaskar on 2006-01-05
[QUOTE=nbhaskar]While booting up my system I get the error message and I checked my /var/log/Xorg.0.log file and found the following

```
loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a
```

I can only work on command line, gdm fails.

Does this ring a bell linux gurus?

Thanks in advance for any help.

:o[/QUOTE]

Never mind my problem got solved just by changing "ati" to "radeon" in the xorg.conf file. Now I am able to boot successfully into Breezy.

thanks any ways.
:D

---

