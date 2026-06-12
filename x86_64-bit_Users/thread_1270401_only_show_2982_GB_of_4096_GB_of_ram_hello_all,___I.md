---
title: "only show 2982 GB of 4096 GB of ram hello all,   I have HP Pavilion dv5278ea Notebook"
date: 2009-09-19
forum: x86 64-bit Users
---

### Post by Face_Man on 2009-09-19
hello all, 

I have HP Pavilion dv5278ea Notebook with 9.04 64-Bit installed. when I check my ram using free -m it show
             total       used       free     shared    buffers     cached
Mem:          2982        730       2252          0         95        230
-/+ buffers/cache:        404       2578
Swap:         4102          0       4102

However my Bois show 4096!

Notebook Specifications
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00762653](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00762653)

Any help would be much appreciated.

---

### Post by urugTON on 2009-09-19
For starters, would you open a terminal session and post the output of "uname -a"?

---

### Post by pbrane on 2009-09-19
The specs you posted for your computer show that the maximum amount of RAM is 2GB.

**Memory Max      up to 2 GB**

I think if you "cat /proc/meminfo" in a terminal you'll see that you only have 2GB of RAM. Not sure what you're seeing in your BIOS.

---

### Post by Face_Man on 2009-09-19
> **urugTON said:**
> For starters, would you open a terminal session and post the output of "uname -a"?

Linux MyPC-Laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

---

### Post by Face_Man on 2009-09-19
> **pbrane said:**
> The specs you posted for your computer show that the maximum amount of RAM is 2GB.

**Memory Max      up to 2 GB**

I think if you "cat /proc/meminfo" in a terminal you'll see that you only have 2GB of RAM. Not sure what you're seeing in your BIOS.


cat /proc/meminfo
MemTotal:        3054308 kB
MemFree:         2065980 kB
Buffers:          122196 kB
Cached:           377792 kB
SwapCached:            0 kB
Active:           607284 kB
Inactive:         272800 kB
Active(anon):     389624 kB
Inactive(anon):        8 kB
Active(file):     217660 kB
Inactive(file):   272792 kB
Unevictable:           8 kB
Mlocked:               8 kB
SwapTotal:       4200956 kB
SwapFree:        4200956 kB
Dirty:               336 kB
Writeback:             0 kB
AnonPages:        380104 kB
Mapped:            84324 kB
Slab:              47440 kB
SReclaimable:      31164 kB
SUnreclaim:        16276 kB
PageTables:        16792 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5728108 kB
Committed_AS:     758700 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      306524 kB
VmallocChunk:   34359429099 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       68096 kB
DirectMap2M:     3076096 kB

---

### Post by urugTON on 2009-09-19
My first thought when you reported 3GB showing up when you expected 4GB was that somehow you had installed a 32 bit OS and not a 64 bit one. That's easy to do and 32 bit OSes tend report that there's a maximum of 3GB installed because they can not use more than that. 

I should not have worried, you have a 64 bit OS installed. 

It looks as though you also have 3GB of memory installed.  Both the "free -m" and the "cat /proc/meminfo" agree on that.    

I don't know what the BIOS is reporting.  My guess is that it is reporting the maximum the BIOS and/or Motherboard will support.

Interestingly the HP link says that the max memory you can install is 2GB.

I admit I am confused by the HP specified limit, but it sure looks like you have 3GB installed.   

One last point, your headline should read "2982MB of 4096MB".  I read right past that when I responded.  :P

---

### Post by Face_Man on 2009-09-19
> **urugTON said:**
> My first thought when you reported 3GB showing up when you expected 4GB was that somehow you had installed a 32 bit OS and not a 64 bit one. That's easy to do and 32 bit OSes tend report that there's a maximum of 3GB installed because they can not use more than that. 

I should not have worried, you have a 64 bit OS installed. 

It looks as though you also have 3GB of memory installed.  Both the "free -m" and the "cat /proc/meminfo" agree on that.    

I don't know what the BIOS is reporting.  My guess is that it is reporting the maximum the BIOS and/or Motherboard will support.

Interestingly the HP link says that the max memory you can install is 2GB.

I admit I am confused by the HP specified limit, but it sure looks like you have 3GB installed.   

One last point, your headline should read "2982MB of 4096MB".  I read right past that when I responded.  :P

yes I do have 64 bit OS installed.
and My BOIS Show I have 4096 of ram  however the OS show 2982

hehehehe i will change the headline.

---

### Post by ubongo2008 on 2009-09-19
some mainboards use some amount of ram for i/o interfaces and stuff like that. one common occurence  is that gfx-cards also take some amount of your ram because it is an integrated adapter which doesn't have own graphics ram.   for my Zotac ion a it is the same thing (4GB installed) 512 is used by gfx card and again ~500 are used by other devices   so i am also kind of 'missing' ~1GB of ram ... it is pretty normal and there is nothing (except for the gfx ram) you can do about it

---

### Post by sanderj on 2009-09-19
First thing to do: Update your BIOS to the newest version.

If that does not solve the memory problem, check your BIOS for a setting "memory (hole) hoisting" or "memory (hole) remapping": if you find that setting, you should turn it on.


If the above does not solve it, you could be out of luck. Your laptop is late 2006 / begin 2007 (right?) and in that time full 64-bit and 4GB RAM was not yet common technology.


As an afterburner, you could look at the output of "dmesg | grep e820" to see which memory is offered by the BIOS to the OS.

---

### Post by Face_Man on 2009-09-19
Well, I guess I am out of luck, thank you all for replying my thread.

---

### Post by urugTON on 2009-09-19
In an earlier post I noted "32 bit OSes tend report that there's a maximum of 3GB installed because they can not use more than that".  Then sanderj mentioned the BIOS and looking at dmesg entries with e820.  

I knew that with 32 bit OSes the last gigabyte (or so) of memory wasn't usable because the BIOS as well as video and PCI cards took it away.  I had mistakenly thought that 64 bit OSes took care of that by moving the pesky memory squatters elsewhere.  

The reference to e820 got me curious so google and I went looking.  Turns out that 64 bit OSes, with the help of a BIOS that can remap memory and an accommodating motherboard, get to use the full 4 GB.  Key is that remapped memory and friendly motherboard.  It isn't just a 64 bit OS as I thought this morning.

There's a pretty good explanation of all the arm waving and black magic needed to get at the full 4 GB at:

[http://www.codinghorror.com/blog/archives/000811.html](http://www.codinghorror.com/blog/archives/000811.html)

There is also an interesting thread at:

[http://www.mail-archive.com/debian-laptop@lists.debian.org/msg51433.html](http://www.mail-archive.com/debian-laptop@lists.debian.org/msg51433.html)

The article and posts match up pretty well with other articles, blogs and posts that I found with google.  It's interesting reading, but I'd advise against making any serious decisions based on my interpretations of what I found.  :)  

It may be the case that Face_Man's problem is not the OS like I thought or the BIOS as sanderj suggested.  Could be rooted in the motherboard's lack of a facility to support the remapping.  As sanderj pointed out, a 4 GB wasn't a big concern when Face_Man's system was built.

Interesting discussion.  Probably time to move on.

---

### Post by ubongo2008 on 2009-09-20
> **urugTON said:**
> In an earlier post I noted &quot;32 bit OSes tend report that there's a maximum of 3GB installed because they can not use more than that&quot;.  Then sanderj mentioned the BIOS and looking at dmesg entries with e820.  

I knew that with 32 bit OSes the last gigabyte (or so) of memory wasn't usable because the BIOS as well as video and PCI cards took it away.  I had mistakenly thought that 64 bit OSes took care of that by moving the pesky memory squatters elsewhere.  



  Well that is exactly right, with 32-Address space you can address exactly 4GB of memory. But since many devices need some address space for i/o they will use some of the address space and map their own eprom/ram or interfaces there.  They won't even use the &quot;lost&quot; ram they are just using the address space which will result in usable ram-regions.   On an 64-Bit OS you'll have 64-Bit of address space therefore it is possible for most devices to use some upper addresses in order to not conflict with todays ram address spaces.

---

