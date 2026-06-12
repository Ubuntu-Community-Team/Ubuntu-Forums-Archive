---
title: "ELFCLASS64 -- how do I find the correct 32-bit libraries to support 32-bit celtx"
date: 2009-03-21
forum: x86 64-bit Users
---

### Post by mickeyh on 2009-03-21
I successfully installed (32-bit) Celtx on my Xubuntu 8.10 amd64.  It won't do some of the internet features (typeset, and "open from studio") and running it from the command line revealed the following errors (below).  Other posts suggested I just need to find the correct 32 compatible libraries and install them in /usr/lib32, but I installed the one thing I found, and I still get:

mtq@asus:$ sudo /usr/local/celtx/celtx
*** fetchBannerData: Unknown error
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiofam.so

I installed: libgio-fam_2.18.2-0ubuntu2.1_i386.deb
to no avail.

Any help appreciated.

---

### Post by Cappy on 2009-03-21
Install getlibs from: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
sudo getlibs /usr/local/celtx/celtx
```

---

### Post by mickeyh on 2009-03-21
I did all that successfully, but to no avail.  Given the error messages above, what module should I attempt to get with getlibs?

By the way, when I ran getlibs against celtx, I had to run it against celtx-bin; it said it was downloading, and then installing, libraries (but I wasn't sure what it did).

So if I can figure out the name of what I'm missing, I have a chance (I hope).

Thanks for the reply.

---

### Post by flickh on 2009-06-06
I'm having crashes on my XO laptop Xubuntu 8.10 system running celtx.

Haven't solved it yet - 

[http://forums.celtx.com/viewtopic.php?t=11005&start=15&postdays=0&postorder=asc&highlight=](http://forums.celtx.com/viewtopic.php?t=11005&start=15&postdays=0&postorder=asc&highlight=)

---

### Post by timgood on 2009-06-08
I'm getting the same problem when trying to install Adobe Air applications - installer launches but then segfaults.  Launching Adobe Air Application Installer from command line gives me the same error messages. Any ideas?

---

