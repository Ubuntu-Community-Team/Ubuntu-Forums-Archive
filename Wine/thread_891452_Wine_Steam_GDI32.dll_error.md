---
title: "Wine Steam GDI32.dll error"
date: 2008-08-16
forum: Wine
---

### Post by jarrhed on 2008-08-16
Well lately whenever I try to load up CSS, Hl2, or any game off of Steam I get the following error when a message is supposed to pop up saying Launching Counter-Strike Source, Please Wait.
```
wine: Call from 0x106e42ad to unimplemented function GDI32.dll.GdiEntry1, aborting

```
I have tried using wine 1.0 & wine 1.1.2 and neither works
I have treid using MS gdi32.dll
I have tred this on other distros (Slackware 12.1 with GSB)

I cannot figure out this error and google is no help
Any help here?

---

### Post by jarrhed on 2008-08-17
bump, i really need this

---

### Post by Brynster on 2008-08-18
what hardware are you using ?

---

### Post by jarrhed on 2008-08-18
I'm running on
AMD Atholon 64 x2 3800+
PNY Geforce 7600gt
2.5gb of ram
37gb 10k rpm sata
80gb ide 5200rpm drive
GA-K8N-SLI (nForce 4 SLI AMD)


It worked before but not now (I got new ram recently but everything else is working)
2x1gb Corsair Stick
2x 256mb Kingston

---

### Post by kdorf on 2008-08-18
The error means exactly what it says, that something is calling an unimplemented function (read: Wine doesn't do it yet) in gdi32.dll.

Did you look at the AppDB at all? [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2095](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2095)

---

### Post by Knorr on 2008-08-21
Just had the same problem with Championship Manager 2008, which ran perfectly 10 hrs ago.

I found that removing all ddraw and d3d9/d3d8 from the native override in winecfg helped.

---

