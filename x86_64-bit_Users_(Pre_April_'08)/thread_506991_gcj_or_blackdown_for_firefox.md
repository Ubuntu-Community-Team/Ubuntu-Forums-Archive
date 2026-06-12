---
title: "gcj or blackdown for firefox"
date: 2007-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by angryfirelord on 2007-07-22
I'm just curious, since I haven't tinkered around with 64-bit much, what is your solution to the java issue using a 64-bit firefox?

---

### Post by Kilz on 2007-07-22
> **angryfirelord said:**
> I'm just curious, since I haven't tinkered around with 64-bit much, what is your solution to the java issue using a 64-bit firefox?

If you choose to use gcj realise that it runs with **[COLOR="Red"]NO security manager[/COLOR]**. An applet could do anything its designed to do. Like Format your hard drive, install a root kit, add users to your system, ect.
Me I think I will continue to use the 32bit browser and java on my 64bit system untill java 7 is released from Sun. It is supposed to have a 64bit plugin.

---

### Post by angryfirelord on 2007-07-22
> **Kilz said:**
> If you choose to use gcj realise that it runs with **[COLOR="Red"]NO security manager[/COLOR]**. An applet could do anything its designed to do. Like Format your hard drive, install a root kit, add users to your system, ect.
Me I think I will continue to use the 32bit browser and java on my 64bit system untill java 7 is released from Sun. It is supposed to have a 64bit plugin.
Actually, I'm currently playing around with gcj and it shows a popup whenever you run an applet, asking you if you want to run it or not. Fortunately, I know what applets are safe and what are not. 

But yes, I'm also eagerly awaiting 1.7. Are there any roadmaps of it avaliable?

---

### Post by angryfirelord on 2007-07-22
Well, I think I answered my own question. Here's what I got:

GCJ - constant hard drive access, fails to load applet. Complains it's out of memory.
```
GC Warning: Repeated allocation of very large block (appr. size 32768000):
        May lead to memory leak and poor performance.

(npviewer.bin:6883): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(npviewer.bin:6883): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so: wrong ELF class: ELFCLASS64
GC Warning: Repeated allocation of very large block (appr. size 262144000):
        May lead to memory leak and poor performance.
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!

```
Blackdown - applets with no sound run smoothly. Applets with sound crash firefox.

---

