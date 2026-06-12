---
title: "pentium i5 should i install 64bit?"
date: 2009-10-13
forum: x86 64-bit Users
---

### Post by white-zilla on 2009-10-13
Hello, I'm getting a new rig, and I got 2 quick questions.

1)should i install 64bit ubuntu. The system is a pentium i5 (4 gig ram) and I plan on running 64bit win7 through virtual box.  I can't find much documentation on ppl installing ubuntu on the new "I" series.

I tried 64bit ubuntu back in version 7 on an AMD64 and it was a terrible.

2)I'm gonna set up a master slave config, what should I format the drives as? Fat32?

much thanx

---

### Post by P4man on 2009-10-13
CPU is irrelevant, all CPU's are 64 bit capable these days. With 4GB Ram, you might want the 64 bit version, and especially so if you intend to run 64 bit OS in a virtual machine (although it is apparently possible to run a 64 bit client on a 32 bit host, it can't be a good idea).

Not sure what was terrible in 2007, there shouldn't be much difference between 32 and 64 bit versions. You might have some minor issues with flash on firefox, but thats certainly solveable. 

As for the partitions, let ubuntu installer handle it. Certainly not FAT32, you'll have the choice between Ext3 and Ext4. If you meant for a shared partition between windows and ubuntu, I guess ntfs is a not too bad choice. If your windows will only run in virtualbox under ubuntu, there is no point in using anything other than Ext as filesystem. (virtualized) Windows can access it through networking.

---

### Post by white-zilla on 2009-10-13
okay, much thanks.  I was afraid I'd run into problems because according this website, the "i" line isn't supported yet.

also I had a rough time back in 07' mainly cause of my graphics card, only the 32-bit driver was supported at the time and i run dual monitors. So i wasn't happy about having my setup crippled.


and wait. so if i format my slave as an ext, I can only access it on my visualized copy of win7 through networking?  That sounds like that would slow down my system.  is doing it this way really faster/better than just formatting the slave as ntfs?

---

### Post by P4man on 2009-10-13
> **white-zilla said:**
> okay, much thanks.  I was afraid I'd run into problems because according this website, the "i" line isn't supported yet.


I believe there are some issues with 'turbo' mode that are only resolved in the latest kernels, Im not sure. Turbo is intel feature that will automatically overclock on or two cores. Im not even sure the i5 has turbo, and regardless, its not a huge loss.

> and wait. so if i format my slave as an ext, I can only access it on my visualized copy of win7 through networking?  That sounds like that would slow down my system.  is doing it this way really faster/better than just formatting the slave as ntfs?[


A virtualized OS can not directly access your physical drives. It will not see the "slave", it will only see virtual harddisks you create on the host OS, or networked shares. Therefore, the filesystem is irrelevant to the client OS (windows), its invisible. You should pick a filesystem that works well with the host (ubuntu). You can do two things to make the client access drives:

1) make virtual harddisks in virtualbox (or vmware). Those will simply be .vdi files to ubuntu residing on a Ext3/4 or ntfs drive. To windows they will look like unformatted disks, you can just format in ntfs for windows. Whatever you put on them (inside those .vdi's)  will not be visible to the host OS, so this is not ideal to share data.

2) use shared network folders. Virtualbox creates a shared folder of an existing (Ext3/4 nfs, whatever) folder, and presents it to the client OS (windows) as a network drive. Again, filesystem is irrelevant. Speed is not a concern, since you don't actually pass over a network, its all virtual ;)

---

### Post by white-zilla on 2009-10-13
OOOOOOOOOOOOOOooooooo....

Yeah, I'm kinda new to running a virtual OS, so that cleared up alot of things for me. Many thanx :)

---

### Post by CHR15B on 2009-10-13
I'm a brand new Ubuntu user here, running 9.04 64-Bit on my system.

I have an Intel i7 920 with 6GB RAM and a nVidia 260GTX with zero problems. :)

Hope this helps.

---

