---
title: "HELP! Mac Mini G4"
date: 2006-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by +ZERO+ on 2006-05-24
Ok, im a total n00b here, so help me out, please.  Im on my lunch break in between finals, so i didnt have time to search this.  

System Stuff:
Mac Mini G4
OS X 10.3.9
Used Disk Utility to Burn

I downloaded ubuntu linux live cd (breezy badger) (odd name isnt it?)  Anyways, it took forever, and so i left it download overnight.

I burned it to a cd (took a while at x4) and i tried to boot from it

Turned on Compy
Held Option
Clicked the cd
Pressed Little Arrow
It asks me the boot thingy
I pressed enter
It says "Loading Kernal...", Then my cd drive slows, and the machine freezes...  Help me please, i want to know whats wrong!

---

### Post by linear on 2006-05-24
Bad burn? I've never had any luck burning Ubuntu CDs with Disk Utility. Try [FireStarter FX]("http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter") instead.

---

### Post by +ZERO+ on 2006-05-24
K, thanks, ill try that

---

### Post by Ptero-4 on 2006-05-24
Check the size of the iso image. It can be a corrupted download. Also download iGetter, it's a very useful tool that allows you to stop a download if it takes too much and resume later (the next day for example) from where you left it.

---

### Post by +ZERO+ on 2006-05-25
Ok, i got the live cd to work...

Now im going to download the install cds, and i already partitioned my 160GB external hd, i partitioned with three spots 1. 119 GB (Main one for OS X 10.3.9) 2. 15 GB (One for my experiments with OS X 10.4.4) and 3. 15 GB (Ubuntu linux).

Do i need to partition my hd more, or is that fine?  Ive got about 2 days till im done downloading, so no rush.

---

### Post by linear on 2006-05-25
[quote=+ZERO+]i already partitioned my 160GB **external** hd[/quote]
AFAIK, getting Linux to boot from an external drive is a bit of work. Here are some threads where you can read about it:

[http://www.ubuntuforums.org/showthread.php?t=84131]("http://www.ubuntuforums.org/showthread.php?t=84131")
 [http://www.ubuntuforums.org/showthread.php?t=40536]("http://www.ubuntuforums.org/showthread.php?t=40536")
 [http://www.ubuntuforums.org/showthread.php?t=91755]("http://www.ubuntuforums.org/showthread.php?t=91755")
 [http://www.ubuntuforums.org/showthread.php?t=89990]("http://www.ubuntuforums.org/showthread.php?t=89990")

---

### Post by 3rdalbum on 2006-05-26
When you partitioned the drive, did you make the "Ubuntu partition" just free "unallocated" space?

Ubuntu actually creates 2 partitions minimum (one for swap space), so it's easiest to give it unallocated space.

If you made the partition "allocated" and you have trouble installing Ubuntu into it, can I suggest that you give it a bit more space? You've got masses of space on your hard disk, so you might as well get a good experience by being able to install all the packages you want.

---

