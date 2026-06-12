---
title: "Problem after installing wine 0.9.28"
date: 2007-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by WalmartSniperLX on 2007-02-02
After installing the .deb package, I ran winecfg. However, I ran into this problem:

```
 /usr/local/bin/wine: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/bin/../lib/libwine.so.1)

```

What does this mean? Sorry if this is a dumb question

---

### Post by Mongoose on 2007-02-02
You may just need ia32-libs, and maybe some Wine setup.  Read the Wine setup section in this thread:

[http://ubuntuforums.org/showpost.php?p=2084780&postcount=1](http://ubuntuforums.org/showpost.php?p=2084780&postcount=1)

I just don't like to repeat myself myself.  ;)

---

### Post by WalmartSniperLX on 2007-02-03
> **Mongoose said:**
> You may just need ia32-libs, and maybe some Wine setup.  Read the Wine setup section in this thread:

[http://ubuntuforums.org/showpost.php?p=2084780&postcount=1](http://ubuntuforums.org/showpost.php?p=2084780&postcount=1)

I just don't like to repeat myself myself.  ;)

Thanks :P :)

---

### Post by #Reistlehr- on 2007-02-03
sudo apt-get install -y ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux

worked for me

---

