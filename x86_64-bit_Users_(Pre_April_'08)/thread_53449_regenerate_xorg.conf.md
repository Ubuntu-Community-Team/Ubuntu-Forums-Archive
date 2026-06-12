---
title: "regenerate xorg.conf?"
date: 2005-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by jakemikey on 2005-07-31
After installing the ATi driver, I accidentially overwrote my default xorg.conf file.  Does anyone know how to regenerate the default file...like the one that was there right after initial installation of Ubuntu?

Thanks in advance,

Jake

---

### Post by jakemikey on 2005-07-31
Here's an example of something that's screwed up since I installed the ATi driver.  Every time I try and compile something from source it complains that I don't have X, X libs, etc.  Example:

checking for X... no
checking X11/Xlib.h usability... no
checking X11/Xlib.h presence... no
checking for X11/Xlib.h... no
configure: error: Xlib.h or Xutil.h not found install xdevel

I'm obviously using X, but it's not picking it up somehow.  I've comiled these same programs with success before I installed the ATi driver...any suggestions?

Thanks,

Jake

---

### Post by jensyt on 2005-08-01
You could try `sudo dpkg-reconfigure xorg` or something to that effect. I don't have my Ubuntu box right now, so I can't tell you for certain, but it would be either xorg or a package similar to that...

---

### Post by NickB on 2005-08-01
That would be:
```

$ sudo dpkg-reconfigure xserver-xorg
```

Nick

---

