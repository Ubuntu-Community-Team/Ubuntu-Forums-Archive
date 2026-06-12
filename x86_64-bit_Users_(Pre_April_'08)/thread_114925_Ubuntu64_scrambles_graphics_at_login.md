---
title: "Ubuntu64 scrambles graphics at login"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by gripepe on 2006-01-09
Hi there,

First I must say i'm a newcomer to Ubuntu, while not in linux, as I use a Fedora workstation at the University.

Right after doing a clean installation of the Breezy amd64 release, which went all fine, system boots properly, but at login I just see a brownish screen. I just can't describe it, it's very similar to what I saw in another thread: 

[http://www.geocities.com/pilstilin9/Screenshot.jpg](http://www.geocities.com/pilstilin9/Screenshot.jpg) 

[http://www.geocities.com/pilstilin9/Screenshot2.jpg](http://www.geocities.com/pilstilin9/Screenshot2.jpg)

except in this case sreen is completely jumbled.

My specs are:

Shuttle SN25 (nForce4 chipset)
Athlon 2200+
Nvidia 6600 GT

I tried editing xorg.conf and lowering color depth and resolution, but i won't work neither. BTW ubuntu32 works fine.

Thanks

---

### Post by gripepe on 2006-01-11
hmmmm.... I've tried several things, but my knowledge of linux systems is still too small.

For the moment I will use ubuntu32, maybe in next update I'll try again.

---

### Post by gmontag on 2006-01-11
Try using a different driver in the xorg file.  I had to use vesa instead of nvidia or nv to get the graphical login to work.  Not perfect but a start.  Just edit the xorg file and change where it says nv or nvidia to vesa.

---

