---
title: "64Bit only detects 3GB RAM out of 4GB"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by digitalextremes on 2009-04-24
I have a lenovo Thinkpad T60 (Intel 945 chipset + Core 2 Duo) and installed Ubuntu 9.04 yesterday...everything seems fine except for my RAM, the system only detects 3GB instead of 4GB (I have a two sticks installed that are 2GB each)

Is this a known bug or a setting I can change?

I already looked in BIOS and I don't have memory remapping option availble.

Vista x64 detects all 4GB so I know my ram is working fine.

I used hardinfo to get system info. My apologies if this is a duplicate thread, I didn't one when I searched.

---

### Post by nikgare on 2009-04-24
Are you sure you install the 64bit Ubuntu?

WHat does this command give you:

**uname -a**

---

### Post by Slim Odds on 2009-04-24
For starters, Vista is probably lying to you.

Do search these forums, there are TONS of posts about this issue.

Bottom line is that even a 64 bit OS can't use all of the memory below 4G.

Check your BIOS settings for something called "memory hole" or something like that and make sure that it's enabled.

---

### Post by digitalextremes on 2009-04-24
> **nikgare said:**
> Are you sure you install the 64bit Ubuntu?

WHat does this command give you:

**uname -a**


this sounds like an insult ;) I am offended now....lol

for sure I know have a core 2 duo and downloaded and installed the 64bit distro.

I have been using the 4GB ram on 64bit Vista Ultimate on the other partition, here is the output from uname -a

authorized@laptop1:~$ uname -a
Linux laptop1 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
authorized@laptop1:~$

Here is some info from hardinfo:

-Version-
Kernel        : Linux 2.6.28-11-generic (x86_64)
Compiled        : #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009
C Library        : GNU C Library version 2.9 (stable)
Distribution        : Ubuntu 9.04
-Current Session-
Computer Name        : laptop1
User Name        : authorized (Authorized User)
Home Directory        : /home/authorized
Desktop Environment        : GNOME 2.26 (session name: this-is-deprecated)
-Misc-
Uptime        : 42 minutes
Load Average        : 0.12, 0.10, 0.08

-Memory-
Total Memory        : 3054588 kB
Free Memory        : 2185388 kB
Buffers        : 35624 kB
Cached        : 407924 kB
Cached Swap        : 0 kB
Active        : 444864 kB
Inactive        : 302308 kB
Active(anon)        : 311560 kB
Inactive(anon)        : 8 kB
Active(file)        : 133304 kB
Inactive(file)        : 302300 kB
Unevictable        : 8 kB
Mlocked        : 8 kB
Virtual Memory        : 2041160 kB
Free Virtual Memory        : 2041160 kB
Dirty        : 32 kB
Writeback        : 0 kB
AnonPages        : 303692 kB
Mapped        : 85168 kB
Slab        : 45948 kB
SReclaimable        : 32276 kB
SUnreclaim        : 13672 kB
PageTables        : 17512 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 3568452 kB
Committed_AS        : 669468 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 102836 kB
VmallocChunk        : 34359634611 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 6976 kB
DirectMap2M        : 3137536 kB

---

### Post by dcstar on 2009-04-26
> **digitalextremes said:**
> 
........
for sure I know have a core 2 duo and downloaded and installed the 64bit distro.

I have been using the 4GB ram on 64bit Vista Ultimate on the other partition, here is the output from uname -a

authorized@laptop1:~$ uname -a
Linux laptop1 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
........
-Memory-
**Total Memory        : 3054588 kB**
........

For some reason the kernel is not using all the memory, have a look in your syslog boot time messages and see if you can spot any relevant messages.

---

### Post by dtsat on 2009-04-26
Do you have shared memory with a video card? If so, that memory won't show ;-)

---

### Post by digitalextremes on 2009-04-27
> **dtsat said:**
> Do you have shared memory with a video card? If so, that memory won't show ;-)

yes, I believe the specs of the laptop mentioned that the video card uses shared memory.

does that mean 1GB is being reserved for video memory? or it's sharing is dynamic and it's just not showing but the PC might be using all of 4GB for non-video tasks?

---

### Post by Slim Odds on 2009-04-27
what does 'free -m' say?

(in a terminal)

```
free -m
```

---

### Post by zdavidlnx on 2009-04-28
Same problem with me: 3.8 Gb are now reporting(Ububtu 9.04 x64) with Ububtu 8.10 it was the 4 Gb. RAM

This is not and BIOS issue i suppose, Vista x64 also reports 4GB.

This start when i upgrade from 8.10 to 9.4

Any ideas?

Linux darkstar 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

free -m
             total       used       free     shared    buffers     cached
Mem:          3895       1989       1906          0         92       1249
-/+ buffers/cache:        647       3248
Swap:         2925          0       2925

---

### Post by dabl on 2009-04-28
3.8G is the right number to see in a GUI memory status report, if you have 4G of RAM installed.  Actually on mine it is 3.7somethingG.  This is due to 1,024 bytes = 1KB, 1,024KB = 1MB, 1,024MB = 1GB.  Check how many _bytes_ you have, and it will be a ten digit number that starts with "4".

---

### Post by stchman on 2009-04-28
My Toshiba laptop with 4GB installed shows ~3.8GB in the System Monitor.

---

### Post by Slim Odds on 2009-04-28
> **dabl said:**
> 3.8G is the right number to see in a GUI memory status report, if you have 4G of RAM installed.  Actually on mine it is 3.7somethingG.  This is due to 1,024 bytes = 1KB, 1,024KB = 1MB, 1,024MB = 1GB.  Check how many _bytes_ you have, and it will be a ten digit number that starts with "4".

[http://en.wikipedia.org/wiki/Gigabyte#Gigabytes_vs._gigabits](http://en.wikipedia.org/wiki/Gigabyte#Gigabytes_vs._gigabits)

---

### Post by zeny on 2009-05-11
I'm having the exact same issue, I'm on Ubuntu 9.04 and I notice I'm only getting a report of 3.8G of ram. However on my Debian boot it shows the full 4G. I highly suspect this to being related to Ubuntu, and no I do not have shared memory, and yes I'm most certain I'm running 64bit.

---

### Post by Zorg-it on 2009-06-23
3.8G is the correct value you have to see, it is just a more accurate and true value of your ram...read the posts below by dabl and slim odds... the issue in this topic is about people like me which see just 3.1G and have installed 4G (or 3.8G which is almost the same) and have a 64bit system installed, so is not about any "High Memory Support" or else.
I think the problem on 64bit systems is about our BIOS configuration and how much memory have dedicated to VGA card. But have no idea how to fix it.

---

### Post by ian dobson on 2009-06-23
Hi,

Look in the bios for an option called memory reallocation or memory remapping, enable it and you'll see about 4Gb ram (minus the ram reserved by the bios).

Regards
Ian Dobson

---

### Post by movieman on 2009-06-23
> **ian dobson said:**
> Look in the bios for an option called memory reallocation or memory remapping, enable it and you'll see about 4Gb ram (minus the ram reserved by the bios).

Except when it doesn't work, then you'll see a system crash and have to go looking for a BIOS upgrade which does work correctly.

That's particularly true on motherboards more than a year or so old, before 64-bit support with >4GB of RAM became a big deal for most motherboard manufacturers. My Asus whatever-it-is, for example, came with broken remapping support in the BIOS when I bought it last summer.

---

### Post by brew1brew on 2009-06-24
I have 8GB in my system and unbutu 9.04/64 is reporting around 6GB So I would like to figure this out as well.

---

### Post by Zorg-it on 2009-06-24
I have a Core2DuoE4400 on a ASRock ConRoe 1333-DVI/H R2.0 with last BIOS upgrade but no way to detect 4GB RAM (2+2) on my Ubuntu 64bit.

---

### Post by Nathan.Flow on 2009-06-24
Most laptops share the system ram with the on board video cards, other laptops allow for sharing with dedicated cards. Also look for side port, I believe that's what it's called. These options are not always changable, some laptops come with a hard coded dedicated percentage of ram allocated to video. I remember seeing some where. 

 Also most ram these days are sold in the *B ranges where * is Mega or Giga, The larger B in this case is in reference to Bytes, not bits, bits are advertised in a *b little "b" fashion. If you were able to by *b then take the number and divide by 8 this is how many bytes are available to you for use. I don't know how some one would get *b ram. As this is not how memory works, computers crunch data in byte increments, not bit, not any more any way.

I would recommend running memtest for bad memory, holes, or leaks some times Linux and even :(windows:( will work around bad ram. Also do some investigation, take the number on the chip the black chip on the ram and google it. You should get the manufacture specifications, maybe it was missed labeled, I had this happen to me before.

---

### Post by ian dobson on 2009-06-25
> **movieman said:**
> Except when it doesn't work, then you'll see a system crash and have to go looking for a BIOS upgrade which does work correctly.

That's particularly true on motherboards more than a year or so old, before 64-bit support with >4GB of RAM became a big deal for most motherboard manufacturers. My Asus whatever-it-is, for example, came with broken remapping support in the BIOS when I bought it last summer.

Hi,

Strange my P5B running a BIOS from the beginning of last year sometime sees 4Gb ram no problems. My P5Q sees 8Gb (Purchased 4 months ago and no BIOS update installed) sees 8Gb ram.

It could well be that the memory remapping in the BIOS for some motherboards is broken, but it's worth a try enabling it. If it is broken complain the the manufacturer. Quite often they fix the mapping problems in leter releases.

Regards
Ian Dobson

---

### Post by Divider on 2009-06-25
Just a quick side note, Most laptops even though say they support "4-8gb of ram" do not out of the box. 

The actual Translation is:

It supports 4-8gb of ram in 64 bit operating systems, but you will need a bios update.

Solution: attempt a bios update, if that doesn't solve the problem, I don't think anything will.

**Another note!**

Intel CPU'S are not TRUE 64 Bit processors.

They Use EMT64 bit emulation technology.

---

