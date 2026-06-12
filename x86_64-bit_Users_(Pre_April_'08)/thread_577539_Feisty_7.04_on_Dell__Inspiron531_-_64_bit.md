---
title: "Feisty 7.04 on Dell  Inspiron531 - 64 bit"
date: 2007-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by alexterm on 2007-10-16
After misadventures with Mandriva 2007.1(32) and likewise with Free Suse 10.2 (64) I was delighted with Feisty (I've been a Mandriva/Mandrake user since 2002).

Is it possible to convert fairly easily to the KDE desktop without acquiring Kubuntu and reinstalling?

When Top is run I've had up to 5 users shown with only one logged-in. The first time I noticed this, the reaction was: rootkits, system compromised, alarm, etc., etc.  This could not be reproduced on a Mandriva 2006 system.

The only problem encountered so far has been with wifi - have to use ethernet, connecting to my Netgear router. The system seems to recognise the Netgear WG311T PCI card - there must be some configuration problem

AMD LiVE X2 5600, mem 2GB 667MHz DDR2, 256MB nVidia GeForce 8600GT

alexterm

---

### Post by Kilz on 2007-10-16
> **alexterm said:**
> After misadventures with Mandriva 2007.1(32) and likewise with Free Suse 10.2 (64) I was delighted with Feisty (I've been a Mandriva/Mandrake user since 2002).

Is it possible to convert fairly easily to the KDE desktop without acquiring Kubuntu and reinstalling?

When Top is run I've had up to 5 users shown with only one logged-in. The first time I noticed this, the reaction was: rootkits, system compromised, alarm, etc., etc.  This could not be reproduced on a Mandriva 2006 system.

The only problem encountered so far has been with wifi - have to use ethernet, connecting to my Netgear router. The system seems to recognise the Netgear WG311T PCI card - there must be some configuration problem

AMD LiVE X2 5600, mem 2GB 667MHz DDR2, 256MB nVidia GeForce 8600GT

alexterm

open a terminal, type or copy paste ths iin
```
sudo aptitude install kubuntu-desktop
```
After you reboot it will be added to the possible sessions you can log into.

---

### Post by alexterm on 2007-10-17
> **Kilz said:**
> open a terminal, type or copy paste ths iin
```
sudo aptitude install kubuntu-desktop
```
After you reboot it will be added to the possible sessions you can log into.

Many thanks - it worked very smoothly.

alexterm

---

