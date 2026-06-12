---
title: "[SOLVED] 8.04.01 resets on ati 3850"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by Marcin Nawrocki on 2008-08-04
I've got kubuntu 8.04.1 64bit working on AMD x2 3800, 2Gb ram, ASROCK agp mainboard. System used to work perfectly with NVIDIA card. Now I've got ATI 3850. System resets every time.
I checked live version from CD (64bit kubuntu 8.04), the same effect - resets.
I doesn't want to work with ATI proprietary drivers (resets) and without them (on vesa - fuzzy, damaged screen).

What I found in logs is:
kdm.log
/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: LoadSubModuleLocal
xorg logs don't contain any errors

---

### Post by markbuntu on 2008-08-09
In 64 bit there is a link you have to make to get around that problem:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

