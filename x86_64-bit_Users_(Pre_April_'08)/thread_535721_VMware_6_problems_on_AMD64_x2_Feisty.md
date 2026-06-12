---
title: "VMware 6 problems on AMD64 x2 Feisty"
date: 2007-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by akahige on 2007-08-26
I've been running a stock Xubuntu Feisty install on an AMD64 x2 (HP Pavilion hardware w. 2 Gb RAM) for awhile now. Everything pretty much works great, except VMware has some problems. Not a lot of useful info on their site, so I thought I'd turn here and see if anyone had any similar experiences...

The most visible issue is an insane amount of clock drift. According to the VMw forum, there are issues with the way TSC keeps the processor timing synced. I tried searching for info on how to check and see if it's enabled in the stock kernel, or how to change its status, but "TSC" seems to be too small of a search parameter and I get no hits (or false positives). (Along with not knowing how to correct the issue if I actually found anything useful.)

The other glitch that I experience shows up when playing multimedia files: certain parts will stick and skip and repeat, in a rather unpredictable fashion. Watching the behavior, it also seems related to the clock function. The Winamp marquee info scroll will sometimes stick, then race very quickly ahead, for example.

I was hoping that people here might be running VMware Workstation 6 under Feisty on an AMD64 x2, and might be able to give me some pointers or suggestions...

Thanks!

---

### Post by funrider on 2007-08-27
** I am using vmserver, which works great**

Here is my config:
AMx2 4200+
2GB DDR2 677
Nvida 5200 128MB
Fiesty Fawn 64b version

I have been successfully running the following so far
--dual processor
1. winxp64
2. SUSE 10.2
3. Solaris 10
4. Vista64

--single processor
1. MacOX (just for tesing, yea i know it aint right....)

if it is too much trouble to set up vmware, why not using the free one?

---

