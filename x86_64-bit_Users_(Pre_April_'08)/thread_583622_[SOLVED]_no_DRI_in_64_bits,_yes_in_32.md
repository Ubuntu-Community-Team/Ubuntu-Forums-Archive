---
title: "[SOLVED] no DRI in 64 bits, yes in 32"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Denn1s on 2007-10-20
Hello everyone, i was wondering if you could help me with this problem, i have a Core 2 Duo desktop and until yesterday i installed 64 bit Xubuntu Gutsy, i dual boot with 32 bit Ubuntu Feisty and both systems are using the same Xorg.conf, the problem is i cant get direct rendering to work in the 64 bit version, although Ubuntu 32 worked flawlessly out of the box, Im new to the 64 bit world so any help would be appreciated.

```

Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

```
```

$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Thank you.

---

### Post by Denn1s on 2007-10-20
ok, so i tried wath glx info sujested (setting LIBGL_DEBUG=verbose) :

```
export LIBGL_DEBUG=verbose
```

and this is wath glxinfo says new:

```
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: i915_dri.so
```

---

### Post by Denn1s on 2007-10-20
well this is starting to look like a monologue, i was able to solve the problem, in case somebody runs into this, the solution is pretty complicate so pay attention:

```

 sudo apt-get install libgl1-mesa-dri libgl1-mesa-glx

```

and voila! direct rendering enabled in 64 bit Xubuntu Gutsy for the 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02), the packages are in the Gutsy CD so you really dont even need internet

hope this helps somebody

---

### Post by gaiterodezona on 2007-12-25
Thanks for your help. Even though, being a monologue, it was quite useful to me. :D

---

