---
title: "Wine 0.9.61 for Gutsy HERE!!!"
date: 2008-05-05
forum: Wine
---

### Post by Mr_Congeniality on 2008-05-05
For all of those of you who do not want to upgrade to Hardy and suffer being left out in the cold because WineHQ isn't producing packages for Gutsy...I've got your relief here.

[http://www.megaupload.com/?d=2DD99GRA]("http://www.megaupload.com/?d=2DD99GRA")

This is built for i386 architectures, I'm not sure if it will run on AMD, 64-bit or other processors.

And I built it all by myself :)

P.S. this version does include icons in the "Applications" menu, so you will have to run wine commands and stuff using ALT+F2 or through the command line.

Wine's configuration can be accessed using "winecfg", and your drive c in wine should be located at /home/username/.wine/drive_c/

Enjoy!

---

### Post by Eisenhemm on 2008-05-05
Thanks Man, You solved one of my problems

---

### Post by dfreer on 2008-05-05
... why not just add the "Hardy" wine repository to your gutsy source list?

---

### Post by cogadh on 2008-05-05
Because using packages built for a different version isn't always the smartest thing to do. I'm not sure if that is the case with Wine, but why risk it?

---

### Post by Mr_Congeniality on 2008-05-05
That is the exact reason of this release, to ensure full compatibility for Gutsy, rather than risk it for packages intended for Hardy.

Compiling software and installing it without it being a debian package also prevents the system to have the ability to upgrade, ever.

I learned this the hard way.

---

