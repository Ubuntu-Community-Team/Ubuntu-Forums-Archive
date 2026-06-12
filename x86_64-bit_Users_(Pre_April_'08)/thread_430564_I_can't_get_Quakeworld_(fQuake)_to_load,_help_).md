---
title: "I can't get Quakeworld (fQuake) to load, help :)"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by lucky2 on 2007-05-02
*./ezquake-gl.glx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory*

is ther error I get when I try to run ezquake-gl.glx , I've tried to copy the missing file from the .deb in the ubuntu repository but it still can't be found by quake, I've also tried sudo linux32 ezquake-gl.glx but thats a no go too, help please and I'l shine you're shoes, cheeers

**FIXED**(I  just ran ldconfig, all is well)

---

### Post by mrblue23 on 2007-06-26
hi,
i have the same exact problem. what do you mean by "you just ran ldconfig"? (or if anybody else reads this: what did he mean? :) )

edit: the lib actually seams to be there...

```

mrblue23@mrblue23-desktop:~$ ls -s /usr/lib/libXxf86*
28 /usr/lib/libXxf86dga.a          0 /usr/lib/libXxf86misc.so.1
 0 /usr/lib/libXxf86dga.so        12 /usr/lib/libXxf86misc.so.1.1.0
 0 /usr/lib/libXxf86dga.so.1      24 /usr/lib/libXxf86vm.a
24 /usr/lib/libXxf86dga.so.1.0.0   0 /usr/lib/libXxf86vm.so
12 /usr/lib/libXxf86misc.a         0 /usr/lib/libXxf86vm.so.1
 0 /usr/lib/libXxf86misc.so       20 /usr/lib/libXxf86vm.so.1.0.0

```

---

### Post by Butthead on 2007-06-26
I seem to be having this very same problem trying to run AlienArena2007 too. :confused:

---

### Post by mrblue23 on 2007-06-27
@butthead:

at the bottom of this page might be the solution for your problem :)
[http://icculus.org/~ravage/alienarena2006/](http://icculus.org/~ravage/alienarena2006/)



unfortunately i couldn't solve mine yet...

---

### Post by Butthead on 2007-06-27
Hi mrblue23,

Thanks for posting the link for me!  Hope it still works with AlienArena2007 though. :guitar:

Hmm, did you ever get in touch with lucky2 to see if he can explain his ldconfig fix? :confused:

---

### Post by Butthead on 2007-06-28
Hi mrblue23,

Thanks, that seems to have fixed the problem. :guitar:

Thank you very much for your help!

---

### Post by aidanr on 2007-06-28
or sudo aptitude install libxxf86dga1 should work also

edit:// actually not so sure about that, i think i may have used those binaries aswell, can't remember

---

### Post by homerhomer on 2007-09-06
or you can install this 

it's ezquake with the shareware pak0 file

[http://www.mediafire.com/?9o1cmwkznnd](http://www.mediafire.com/?9o1cmwkznnd)

---

