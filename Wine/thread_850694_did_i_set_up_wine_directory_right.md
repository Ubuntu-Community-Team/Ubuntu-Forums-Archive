---
title: "did i set up wine directory right?"
date: 2008-07-05
forum: Wine
---

### Post by upchucky on 2008-07-05
I have a 60 gig partition for my files, and about 10gig free space for my home partition, however wine always wants to install apps and games into my home/user/.wine/C:\program files, and this fills the 10 gig up pretty fast, I am forced to remove some apps when i want to use a new app.

I assumed that I could tell wine to use the 60 gig partition for its various installs, but it will not do that.

did I miss some thing in the original setup?

---

### Post by SBFC on 2008-07-06
Use 'wineprefixcreate' to setup your wine directory. 

Remove your old one, then ```
wineprefixcreate --prefix /path/you/want
```

---

### Post by YokoZar on 2008-07-06
> **SBFC said:**
> Use 'wineprefixcreate' to setup your wine directory. 

Remove your old one, then ```
wineprefixcreate --prefix /path/you/want
```

If you do this, you need to tell Wine to use that prefix when you launch it.


For the OP's situation, it's probably much easier to add a D:\ drive in winecfg pointing to the larger partition and install stuff there.

---

### Post by cogadh on 2008-07-06
If that 60 GB partition is where you have your root directories, then you really have your system set up backwards. The system only needs about 10 GB of space at most (usually). The majority of your drive space should be used for your home directories. For example, I have Kubuntu on a 120 GB drive, 20 GB is set aside for /, 2 GB for swap and the remaining 98 GB for /home.

---

### Post by upchucky on 2008-07-07
Thanks for the help everyone, could someone please explain how to use the other 60 gig partition for wine installs as a lets say drive D

as for my partitions, i set up the system badly because my home partition is my root partition too, this was done when i was using windows mostly, now i have only booted into windows once in the past few months. so i have stolen the drive space from both my windows partitions for ubuntu.


Now I am using a usb image to restore my ubuntu install if i do anything that may break it.

I really would like to have my home on the 60 gig partition, but i have not read of a way to correct my original install without losing and reinstalling everything.

the reason i did install the way i did was because i had my win xp on a small partition, and my files, and programs on a larger partition.

thinking the same way for ubuntu led me to have ubuntu on a 10 gig partition with home, not knowing that home should be on a separate partition.

I have since grown my ubuntu partition to 40 gig, and have removed the swap file, the system is stable without it.

---

