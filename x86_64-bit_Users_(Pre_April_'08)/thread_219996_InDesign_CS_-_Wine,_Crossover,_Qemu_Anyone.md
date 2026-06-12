---
title: "InDesign CS - Wine, Crossover, Qemu? Anyone?"
date: 2006-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-07-20
The last thing I need before I can ditch my Windows computer forever is InDesign CS. InDesign 2.0 won't do, because I have a lot of documents in CS format and you can't save backwards from CS.

With Ubuntu Dapper amd-64 I knew Wine would be a problem, so I skipped Wine and just bought Crossover Office. InDesign CS installed fine, but when I try to launch it I get a long list of error messages. That is, from the menu launch entry installed by Crossover Office it just tries and then quits. From the command line I get a page and a half of error messages. (Saved in a text file, available on request.)

I do have a spare license for Windows 2000 Professional that I am not using.

So has anyone gotten InDesign CS running? Would Qemu do the trick? A chroot environment? Other options?

---

### Post by Kilz on 2006-07-20
> **John Jason Jordan said:**
> The last thing I need before I can ditch my Windows computer forever is InDesign CS. InDesign 2.0 won't do, because I have a lot of documents in CS format and you can't save backwards from CS.

With Ubuntu Dapper amd-64 I knew Wine would be a problem, so I skipped Wine and just bought Crossover Office. InDesign CS installed fine, but when I try to launch it I get a long list of error messages. That is, from the menu launch entry installed by Crossover Office it just tries and then quits. From the command line I get a page and a half of error messages. (Saved in a text file, available on request.)

I do have a spare license for Windows 2000 Professional that I am not using.

So has anyone gotten InDesign CS running? Would Qemu do the trick? A chroot environment? Other options?

Id say qemu, vmware (my fav) or setup a windows partition and boot into it. 
Vmware is nice, there is one 3d modeling program (Rhinoceros v3) that wont run under wine/crossover. I use it once in a blue moon. I dont have to log out of Ubuntu, just start up a windows y2k virtual machine. The best thing is I have the virtual machine on a dvd, I dont even upgrade it. If it ever messes up, I just delete and replace it.

---

