---
title: "unusual 64 RAM usage?"
date: 2009-02-24
forum: x86 64-bit Users
---

### Post by ZeldaFan on 2009-02-24
When I had used Hardy Heron 32-bit with compiz fusion, AWN, emerald, and my usual programs open (firefox, amarok, pidgin, etc), I had typically used 500 MB RAM maximum (maybe 600 MB absolute max). Now, with Intrepid Ibex 64-bit with the same conditions, I'm using around 1 GB - 1.2 GB. I have 2 GB RAM, so it doesn't really effect my normal usage of my computer, but I also use virtual machines with vista sometimes. With 32 bit Heron, I could accomodate the RAM usage involved with virtual machines, but with 64 bit the stress on my computers resources makes it much more difficult to use the virtual OS. 
Is this RAM usage ordinary or can I assume that increase in RAM usage is attributed to the use of a 64 bit system as opposed to a 32 bit system?

---

### Post by mtopro on 2009-02-24
My 64 bit system uses no more RAM than the previous 32 bit. But VirtualBox can hog some resources when it is up and running.
Have you checked the system monitor under processes then sort by memory usage to find what is hogging your resources?

---

### Post by darco on 2009-02-24
Type free -m in a terminal and post output

darco

---

### Post by ZeldaFan on 2009-02-25
Yeah, 64 bit is definitely using more resources, even after a restart and starting all of my programs again. Here's my "free -m" output:
```
             total       used       free     shared    buffers     cached
Mem:          2007       1435        572          0         88        559
-/+ buffers/cache:        787       1219
Swap:         5875          0       5875

```

---

### Post by brainiac8008 on 2009-02-25
Try putting top into the terminal and find out what is using up so much of your RAM.

---

### Post by MC707 on 2009-02-25
Strange... I have all the stuff you mentioned open, but only 486MB out of 16GB.

---

### Post by MC707 on 2009-02-25
Strange... I have all the stuff you mentioned open, but only 486MB out of 16GB are used.:?
Edit: Damn sorry double post

---

### Post by ZeldaFan on 2009-02-25
I have Xorg using around 161 MB, Swiftweasel (a firefox derivative) at 165 MB, and 200 MB for a random assortment of processes including pidgin. That's only around what 520 MB total...so I dont understand.

---

### Post by darco on 2009-02-25
> **ZeldaFan said:**
> Yeah, 64 bit is definitely using more resources, even after a restart and starting all of my programs again. Here's my "free -m" output:
```
             total       used       free     shared    buffers     cached
Mem:          2007       1435        572          0         88        559
-/+ buffers/cache:        787       1219
Swap:         5875          0       5875

```

From what I learned from reading the output of the free -m command is, the line that shows -/+ says you are using 787 mb with 1219 mb in cache. So you really arent too much over than before. A possible mem leak or a process that needs to be restarted may show the true amount.

darco

---

### Post by ZeldaFan on 2009-02-25
Nope, 787 MB is the lowest I'll get it to. After letting the programs run for a bit and having any memory leaks propagate a little, RAM usage will increase to 900 MB and usually over 1 GB eventually.

---

### Post by 3Miro on 2009-02-25
On theory 64-bit opcode takes double the size of 32-bit opcode. So 64-bit apps would definitely take up more memory. Data, however, is the same between 64 and 32 bit machines, so the difference should be negligible.

I don't know if you are reading your memory usage right. In general Linux would always use about 98% of your RAM, it cashes files from the HD, doesn't move libraries out of memory unless it has to and so on. If I run basic processes I do get around 500-600MB application RAM, if I do that for some time, however, the size goes up to over a gig. It makes no difference, on the contrary, it makes the system run better.

Keep an eye on the swap usage, it Linux (a desktop not a laptop one) goes into swap then it needs more memory, as long as you are not on the swap it makes no difference how much ram you use.

---

### Post by yther on 2009-02-25
I'm not sure if it's only on 64-bit machines, but there's at least one acknowledged bug with **dbus** gradually consuming excessive amounts of memory.  Logging out and back in resets it, so it's on a per-user basis.  I have 8GB of RAM and if I let my system stay logged in on my desktop for a week, dbus will be consuming nearly half of that by itself.  :shock:

I believe [this](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/295741) is the bug in question.

---

### Post by ZeldaFan on 2009-02-25
> **3Miro said:**
> On theory 64-bit opcode takes double the size of 32-bit opcode. So 64-bit apps would definitely take up more memory. Data, however, is the same between 64 and 32 bit machines, so the difference should be negligible.

I don't know if you are reading your memory usage right. In general Linux would always use about 98% of your RAM, it cashes files from the HD, doesn't move libraries out of memory unless it has to and so on. If I run basic processes I do get around 500-600MB application RAM, if I do that for some time, however, the size goes up to over a gig. It makes no difference, on the contrary, it makes the system run better.

Keep an eye on the swap usage, it Linux (a desktop not a laptop one) goes into swap then it needs more memory, as long as you are not on the swap it makes no difference how much ram you use.

Normally, I wouldn't mind the increased RAM usage and I have heard what you explained above before. Under standard conditions, my laptop is very responsive. But when I run a virtual machine, this cached memory or something must not be getting cleaned out in favor of making space for the virtual OS because I have 1 GB saved for it and my RAM usage goes up to around 1.9 GB and I am using a ton of swap, more than I needed to with 32 bit to say the least (which was usually none).

---

### Post by 3Miro on 2009-02-25
> **ZeldaFan said:**
> Normally, I wouldn't mind the increased RAM usage and I have heard what you explained above before. Under standard conditions, my laptop is very responsive. But when I run a virtual machine, this cached memory or something must not be getting cleaned out in favor of making space for the virtual OS because I have 1 GB saved for it and my RAM usage goes up to around 1.9 GB and I am using a ton of swap, more than I needed to with 32 bit to say the least (which was usually none).

This is interesting. Does it only happen when you are running virtual machine? I am using Virtual Box left and right and 32-bit system under 64-bit host would be definitely slower than 32 bit under 32 bit, however, the memory usage should not be different.

I would double check the settings on the Virtual Machine, does it by any chance take up way too much RAM (wrong setting or something). What OS are you using, WinXP only needs about 200MB to run and Ubuntu needs 400MB. That is the minimum of course, depending on what you are doing it might be more for both.

Last question: are you using a desktop or a laptop? Keeping data in memory takes up energy, to save energy a laptop would swap data on the hard drive (storing data on the hard is energy free). If I unplug my 64-bit 4GB laptop it would swap data to save battery power. It is possible that the 64-bit machine simply has better power management (on a laptop of course).

---

### Post by Yellow Pasque on 2009-02-25
If you're running virtual OS's on your laptop, it might be financially worthwhile to consider a RAM upgrade. I'm not suggesting that you just throw money at the issue, but if you determine that there's no memory leak, adding RAM could be a good idea.

---

### Post by ZeldaFan on 2009-02-26
I am using vista under the virtual machine, which I understand takes much more memory than xp but I only have a factory settings OEM version of XP, which you cannot install in a virtual machine. I have an actual install disk for vista, so its my own option at  this point. I've been looking for deals for RAM upgrades for laptops, but at the same time my laptop can technically only support 2 GB.
People have added 2 GB more (with 2 x 2 GB sticks) and found that usually only around 2.7-3.3 GB RAM is actually detected/usable, which is still an upgrade but an architectural problem in the chipset prevents the lappy from utilizing all 4 GB. 
Right now, I'm going to reinstall vista on my virtual machine and see what happens from there. Maybe I'm just imagining things or was experiencing an anomaly. 

To be clear, does running a 32 bit virtual OS on a 64 OS slow things down more than a 32 bit on a 32 bit host? I never knew this.

---

### Post by mgol on 2009-10-10
> **ZeldaFan said:**
> I am using vista under the virtual machine, which I understand takes much more memory than xp but I only have a factory settings OEM version of XP, which you cannot install in a virtual machine.
On the record - maybe You know this, but any Vista version including Home Premium and lower cannot be installed in a virtual machine (according to EULA) - but You probably have Business or Ultimate version.

---

