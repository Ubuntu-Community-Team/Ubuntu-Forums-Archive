---
title: "Sunbird: cannot load shared libraries error"
date: 2006-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krakatos on 2006-11-12
Hmm well, I wanted to try Sunbird, so I downloaded the 0.3 version form the mozilla.org site and then followed this tutorial
[http://www.ubuntuforums.org/showthread.php?t=278206](http://www.ubuntuforums.org/showthread.php?t=278206)
the only difference being that I moved the uncompressed directory manually to /opt/
If I try to start sunbird from terminal, this is what I get:

krakatos@Krakatos:/opt/sunbird$ sudo ./sunbird
./sunbird-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

But slocate gives me
krakatos@Krakatos:/opt/sunbird$ slocate libgtk-x11
/usr/lib/libgtk-x11-2.0.so.0.1000.6
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.la
/usr/lib/libgtk-x11-2.0.a
/usr/lib/libgtk-x11-2.0.so

I am confused now, any ideas? Thanks in advance

---

### Post by kleeman on 2006-11-12
Try 
sudo apt-get install ia32-libs-gtk

This has the 32bit library you are missing. For future reference
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Has a file search facility which tells you where the missing libraries are located package wise.

---

### Post by Krakatos on 2006-11-12
> **kleeman said:**
> Try 
sudo apt-get install ia32-libs-gtk

This has the 32bit library you are missing. For future reference
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Has a file search facility which tells you where the missing libraries are located package wise.

Thanks a lot. My brain must be fried or something, I didn't even see it was 32bit. Worked perfectly

---

