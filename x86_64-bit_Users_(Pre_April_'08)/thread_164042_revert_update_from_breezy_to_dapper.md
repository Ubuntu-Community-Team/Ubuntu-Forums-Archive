---
title: "revert update from breezy to dapper?"
date: 2006-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tink on 2006-04-22
Hi,

Today I did a dist-upgrade from breezy to dapper, it broke networking
(forcedeth module is loaded but ifconfig can't find the device) and video
(the proprietary NVIdia driver compiles and installs fine, the kernel module
is loaded, but X complains it can't load its module - the module is installed,
and it's current) ... Is there a trivial way of getting back to breezy, or will I have
to actually re-install?


Cheers,
Tink

---

### Post by RAOF on 2006-04-22
There is no simple way to revert.  You have to reinstall.

On the other hand, **my** upgrade to Dapper worked just fine (AMD64, nForce networking, nVidia graphics card).  For the graphics card, at least, you should use the packaged drivers from apt-get - they're the latest driver, anyway.

---

### Post by Tink on 2006-04-22
[QUOTE=RAOF]There is no simple way to revert.  You have to reinstall.
[/quote]
Bummer ...

[QUOTE=RAOF]
On the other hand, **my** upgrade to Dapper worked just fine (AMD64, nForce networking, nVidia graphics card).  [/QUOTE]
Good on yah :)

[QUOTE=RAOF]
For the graphics card, at least, you should use the packaged drivers from apt-get - they're the latest driver, anyway.[/QUOTE]
Hmmm ... too late.  Network ain't working anymore.

Thanks anyway.


Cheers,
Tink

---

