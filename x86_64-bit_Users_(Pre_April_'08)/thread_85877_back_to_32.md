---
title: "back to 32"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by smb2004 on 2005-11-03
I want to retrun back to the 32bit verion of ubuntu. (how) can i reinstall over my current partitions while saving my files?

---

### Post by jvictor on 2005-11-03
Havent tried but i GUESS theres an option to leave the partitions data untouched in the disk setup screen of Ubuntu install... u may just give the mount point and leave the partition unfomatted.. DO AT YOUR RISK :) i havent tried it...

---

### Post by cybrjackle on 2005-11-04
Do you have a seperate /home file system?

or handy "tar" and drop them on another box/cd/dvd

---

### Post by ToastedToad on 2005-11-05
Debian/ubuntu has never failed me at preserving my /home partition. The only thing you have to do during partitioning is select it to be used as /home. When it asks if you are sure you want to write the changes, make sure that the /home partitition, has a smiley face next to it:)

Of course this all assumes that you have a seperate /home partition.

---

### Post by skylark on 2005-11-05
I would still seriously consider backing up any critical documents/work you have in /home or other places onto a CD or network copy it to another computer just in case.

---

### Post by BoyOfDestiny on 2005-11-05
[QUOTE=skylark]I would still seriously consider backing up any critical documents/work you have in /home or other places onto a CD or network copy it to another computer just in case.[/QUOTE]

You'll be fine if /home is on another paritition. Just make sure in the set up that you mount them the way you want. In the info you will see something like "Keep existing data", if you select it and hit enter you can make it erase (I'd assume you'd want that for /)

Good luck!

---

### Post by wmcbrine on 2005-11-06
[QUOTE=jvictor]Havent tried but i GUESS theres an option to leave the partitions data untouched in the disk setup screen of Ubuntu install... u may just give the mount point and leave the partition unfomatted.. DO AT YOUR RISK :) i havent tried it...[/QUOTE]
Yeah, I did that after my upgrade from Hoary to Breezy failed (both 64-bit, though). It gives you several strongly-worded warnings with red backdrops, and kinda makes it sound like you can't do it, but you can. Fixed me right up. My only "problem" is that I now have a bunch of programs that run, but which the package manager doesn't know are there.

---

