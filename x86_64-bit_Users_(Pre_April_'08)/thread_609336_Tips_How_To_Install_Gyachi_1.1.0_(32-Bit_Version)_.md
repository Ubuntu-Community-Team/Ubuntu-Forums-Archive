---
title: "Tips How To Install Gyachi 1.1.0 (32-Bit Version) on Ubuntu Gutsy 7.10 64 Bit-Version"
date: 2007-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ramadhian on 2007-11-10
After dowload "gyachi_1.1.0-1_i386_gutsy.deb" and "gyachi-codecs.deb"
do following step :

1.) sudo dpkg -i gyachi-codecs.deb

2.) sudo dpkg -i --force-all gyachi_1.1.0-1_i386_gutsy.deb
     (if you see messeges about incompatiblity x386 messeges , just ignore it)

3.) Download & Install GetLibs :

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

4.) sudo getlibs -32 libgtkhtml-2.so.0

5.) sudo getlibs -32 libjasper.so.1

and Now your gyachi 32-Bit should be run with your Ubuntu 64-Bit


If you see some messeges like this at console :

(gyachi:7635): Gtk-WARNING **: Error loading theme icon 'gtk-stop' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory


don't worry bcoz I have the same here, but so far everythings work fine...
Webcam Viewer, Voice Support work fine too ..

---

### Post by abish on 2008-01-22
Thanks man! it worked!!
thank you.

---

### Post by bit2 on 2008-06-30
Thanks man but hw cn i start webcam?

---

