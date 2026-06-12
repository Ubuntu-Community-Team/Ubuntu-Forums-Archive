---
title: "Porting Backports?"
date: 2005-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by d0nk on 2005-07-21
Is there an automated way in wich i can download the source package from backports, then compile them, make the debs, and built a psuedo repository of those .debs?  

Basically, i'm looking for an automated way to make a local port of backports, then if sucessful, post about how i did it, and maybe get someone to make the official amd64-backports or something. 

I just want to be able to use the newer packages outside of my 32 bit chroot...  Any tips or advice?

---

### Post by Tamir on 2005-07-22
[QUOTE=d0nk]Is there an automated way in wich i can download the source package from backports, then compile them, make the debs, and built a psuedo repository of those .debs?  

Basically, i'm looking for an automated way to make a local port of backports, then if sucessful, post about how i did it, and maybe get someone to make the official amd64-backports or something. 

I just want to be able to use the newer packages outside of my 32 bit chroot...  Any tips or advice?[/QUOTE]
 There is one backport now - [http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905).
for the sources, you should do: ```
apt-get source packagename
```
it will download the .orig.tar.gz (the source code), the .dsc, and the .diff, then you should only add your name to the changelog, modify somethings and run ```
dpkg-buildpackage
```.

Look, Do you want to help me with making debs instead of this?
Because I have a lot of work. to details go to the link I gave.

---

### Post by d0nk on 2005-07-22
I've used (and still use) your repo, only problem with it is though, is that firefox 1.0.99 won't work for some reason.  I get segfaults (i do when i compile from source too though, so not sure.)

Working together would be cool, but i don't have all that much time to dedicate to it.

---

