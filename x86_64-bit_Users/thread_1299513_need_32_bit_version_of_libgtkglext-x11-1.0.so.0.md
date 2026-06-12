---
title: "need 32 bit version of libgtkglext-x11-1.0.so.0"
date: 2009-10-24
forum: x86 64-bit Users
---

### Post by Ravernomina on 2009-10-24
Can some 1 tell me how to get this Lib and hot to install the 32bit version Thanks!


This is for getting the pSX emulator working (:

---

### Post by macaholic on 2009-10-24
Download it from one of the Ubuntu packages site mirrors and install with:
Install with ```
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.2.0-1ubuntu1_i386.deb
sudo dpkg -i --force-architecture libgtkglext*

```
You can remove the .deb after the install succeeds.
Hope that helps!

---

### Post by Yellow Pasque on 2009-10-26
macaholic, won't that install 32-bit libraries in /usr/lib ?

Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
Then:
```
sudo getlibs -p libgtkglext1
```

---

