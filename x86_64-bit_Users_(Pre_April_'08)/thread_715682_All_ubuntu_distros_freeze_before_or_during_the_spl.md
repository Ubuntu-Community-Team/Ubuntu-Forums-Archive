---
title: "All ubuntu distros freeze before or during the splash screen"
date: 2008-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by UberrrSauce on 2008-03-05
I am trying to install Ubuntu 7.10 Gutsy Gibbon 64 bit version on my PC (see end of post for specs) and when I launch from the LiveCD it goes through the loading screen (and occasionally freezes just before finishing loading, but this isn't the primary issue) and then arrives at the desktop with the blank browny-peach background. At this point the mouse is present (First it appears as a black X cursor, then a circular loading cursor, and finally a regular pointer cursor) and is movable around the screen, but after about 5 seconds the mouse cursor freezes and nothing happens, no matter how long I leave it. Sometimes the Welcome screen will show up and the welcome sound will play before it freezes.

I have also tried running the LiveCD in safe graphics mode, but when it gets to the point where it should show the desktop, ASCII characters appear all over the screen in a seemingly random pattern. Finally, I also tried a 32-bit LiveCD for Ubuntu 7.04 Feisty Fawn, which also froze at or before the welcome screen. I have heard of the launch parameters -noacpi and -noapic but adding those to the launch parameters did not help the issue. I do however recall similar commands solving a similar problem in the past with Feisty, but I believe there was more than just those two commands.

My PC's vital specs are:

AMD Athlon 64 3200+
80GB Seagate IDE HDD
Inno3D GeForce 7300GT
1.5GB Corsair DDR RAM

---

### Post by TenPlus1 on 2008-03-05
You could try unplugging all non-essential devices and installing again, or use the alternative install cd for a text-only safe install...

---

### Post by UberrrSauce on 2008-03-05
I've also tried installing from a text-only install CD for Feisty but no dice :(

---

### Post by UberrrSauce on 2008-03-05
I solved the issue - I found the launch parameters I was looking for;

irqpoll pci=noacpi noapic nolapic acpi=off

adding that to the launch parameters solves it all. Hope that can help someone else.

---

### Post by UberrrSauce on 2008-03-08
Okay so now I have a new problem - whenever I restart Ubuntu, it goes into low graphics mode and no longer recognises the driver I installed. I have to reinstall the driver to get back my videocard's functionality every time I restart.

---

### Post by crjackson on 2008-03-08
Open a terminal and try this
```
sudo depmod -a
```
Then restart X using ctrl+alt+backspace

If that doesn't work try this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

