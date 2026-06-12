---
title: "Even the 64bit installation only sees 2.9 out of 4GB of RAM"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by congogr on 2009-08-21
Right. This is what keeps me up at nights :P :

On my installation of Ubuntu 9.04 (64bit), I cannot fully utilize my RAM. Is a change in the kernel needed EVEN on 64bit installations?

==> My system is a ThinkPad z61m; specs "specify" max 3GB or RAM, but I think one of the BIOS updates allowed for support of more. In any case:
==> The system monitor gives me "2.9GiB" of Memory
==> Issuing $ lshw (without sudo) gives:
...
description: Computer
width: 64 bits
capabilities: vsyscall64 vsyscall32
*-core
description: Motherboard
physical id: 0
*-memory
description: System memory
physical id: 0
size: 3070MiB
...

==> Issuing $ sudo lshw gives:
...
*-memory
description: System Memory
physical id: 29
slot: System board or motherboard
size: 4GiB
*-bank:0
description: SODIMM Synchronous
physical id: 0
slot: DIMM 1
size: 2GiB
width: 64 bits
*-bank:1
description: SODIMM Synchronous
physical id: 1
slot: DIMM 2
size: 2GiB
width: 64 bits
...

==> $ free gives:
total used free shared buffers cached
Mem: 3054592 2376104 678488 0 144424 1373612
-/+ buffers/cache: 858068 2196524
Swap: 7839680 0 7839680


To my knowledge, the systems 'sees' the extra RAM (and thus the hardware supports it...?) but cannot utilise it. Wouldn't the 64bit kernel automatically use the full 4Gigs? Is an extra 'server kernel' installation needed, even with a clean installation of a 64bit edition?

Thanks for the help,
G.

---

### Post by SoftwareExplorer on 2009-08-22
64 bit is supposed to fix the ram 3Gb or so limit. Maybe some of it is getting shared with your graphics card?

---

### Post by SoftwareExplorer on 2009-08-22
By the way, I have 4 Gb and the same situation, too.

---

### Post by congogr on 2009-08-22
How could we check this? :P In any case, I think it is 'impossible' (not to mention odd) to have 1024MB automatically allocated to a X1400 graphics controller which is (if I remember correctly) supposed to have 256MB memory of it's own.

once again (for anyone that can help):
sudo lshw : 4GiB
lshw : 3070MB
BIOS reports: 4096MB of RAM

uname -a output:

Linux UsErNaMe 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by techstop on 2009-08-22
Just having a 64-bit OS and a 64-bit CPU is not enough. Your motherboard needs to see all your memory as well. I have a Dell XPS M1210, and it only sees about 3.2GB of 4.0GB installed on 64-bit Jaunty (even though the BIOS can see that I have 4.0GB).

---

### Post by congogr on 2009-08-22
Agreed. But you obviously mean your BIOS only sees 3. Mine DOES see all 4Gigs...

EDIT: I just saw your EDIT about the BIOS. Well obviously, if the BIOS sees it, your computer supports it; it somehow needs to be enabled on the OS.

---

### Post by techstop on 2009-08-22
> **congogr said:**
> Agreed. But you obviously mean your BIOS only sees 3. Mine DOES see all 4Gigs...

EDIT: I just saw your EDIT about the BIOS. Well obviously, if the BIOS sees it, your computer supports it; it somehow needs to be enabled on the OS.

No. My hardware does not support the full 4.0GB, even though the BIOS knows that it's there. Lots of hardware out there that does the same thing. Anything made in the last year or two should be right though.

---

### Post by congogr on 2009-08-22
That could make sense. Although it's very odd, for a 3year old IBM laptop with a T7200 in it... :-/

---

### Post by howefield on 2009-08-22
> **congogr said:**
> That could make sense. Although it's very odd, for a 3year old IBM laptop with a T7200 in it... :-/

This is quite interesting, 

[http://blog.venthur.de/2007/05/14/4gb-ram-on-a-t60/](http://blog.venthur.de/2007/05/14/4gb-ram-on-a-t60/)

Although it is talking about another Thinkpad model, could be the same issue.

---

### Post by SoftwareExplorer on 2009-08-22
My motherboard is supposed to support 8 GB of ram, and my computer still does the same thing. I'm still thinking it could be graphics because yes they have their own memory, but they can still use ram in addition to the memory they already had.

---

### Post by stmiller on 2009-08-22
There are many threads on this, which might have some more help:


[http://ubuntuforums.org/showthread.php?t=1221361](http://ubuntuforums.org/showthread.php?t=1221361)

[http://ubuntuforums.org/showthread.php?t=1031595](http://ubuntuforums.org/showthread.php?t=1031595)

and many others...

---

### Post by Yellow Pasque on 2009-08-23
> specs "specify" max 3GB or RAM, but I think one of the BIOS updates allowed for support of more.
You might want to re-check that and make sure the system supports it before trying to troubleshoot your OS.

Also, you might want to play with LiveCD's of recent distros and see if the same issue occurs (you don't even need a GUI, just check the 'free' command).

---

### Post by chris1950 on 2009-08-23
I have a new Compaq V3000 Presario - lshw shows 4GB, free shows 3.9 Total, 1.01 Used, 2.9 Free. lshw showed graphics using using 0 MB. So where did the 1GB go?:confused:

---

### Post by howefield on 2009-08-23
> **chris1950 said:**
> ..lshw shows 4GB, free shows 3.9 Total, 1.01 Used, 2.9 Free. lshw showed graphics using using 0 MB. So where did the 1GB go?:confused:

What 1 gig ?

---

### Post by movieman on 2009-08-23
> **Temüjin said:**
> You might want to re-check that and make sure the system supports it before trying to troubleshoot your OS.

Indeed: if the BIOS doesn't support memory remapping, you're not going to be able to access that extra 1GB even running a 64-bit kernel. It's also worth noting that some older BIOSes do support memory remapping, but it doesn't actually work; I had to upgrade the BIOS on my CentOS machine in order to access the last 250MB of RAM due to buggy memory remapping code in the old BIOS.

---

### Post by skriefal on 2009-08-23
It's a limitation with the Intel 945 chipset in the Z61M.  The 945 chipset was deliberately crippled by Intel to support a max of 3GB of addressable RAM.  There is no workaround.

---

### Post by dcstar on 2009-08-26
> **skriefal said:**
> It's a limitation with the Intel 945 chipset in the Z61M.  The 945 chipset was deliberately crippled by Intel to support a max of 3GB of addressable RAM.  There is no workaround.

Various MBs have fixed maximum RAM limits but allow installation of RAM chips higher than that limit, so even though the BIOS "sees" a certain amount of RAM, you can only access the maximum amount the MB was designed for.

---

### Post by Bear Knuckle on 2009-08-26
> **chris1950 said:**
> I have a new Compaq V3000 Presario - lshw shows 4GB, free shows 3.9 Total, 1.01 Used, 2.9 Free. lshw showed graphics using using 0 MB. So where did the 1GB go?:confused:

You have 4GB and free tells you, you have 3,9 total, with 1.01 used and 2.9 free, whats 3,91 in a total. Nothing did go anywhere and everythings fine, isn't it?

---

### Post by tenghoward on 2009-08-28
GiB is not the same as GB.

GiB is based on 1024.
GB is based on 1000.

Computer does calculation based on 1024. However, what Windows and retailer did is that they use GB instead. Windows reported RAM as in 4GB = 4000MB.

In Ubuntu, computer uses more precise calculation. So they reported as 3.9GiB.

4GiB = 4096MB
4GB = 4000MB

So that missing 0.1GiB is that 96MB.

---

### Post by Slim Odds on 2009-08-28
I see so many posts about memory on 64 bit systems and I just wanted to mention a simple concept.

Lot's of us use the 64 bit version of Ubuntu without issue. So that really means that this is logically a motherboard issue for those having this problem.

My system reports 7.991 G of RAM for an 8 G installation. I'd say that's close enough.

So let's all understand that there is NO problem with the 64 bit version of Ubuntu. It's always the MOBO.

---

### Post by Cracauer on 2009-08-28
> **SoftwareExplorer said:**
> 64 bit is supposed to fix the ram 3Gb or so limit. Maybe some of it is getting shared with your graphics card?

Not this specific problem.

With a 64 bit kernel or a 32 bit kernel with PAE you can see memory that is above 4 GB.

But the missing stuff from 3-4 GB isn't living above 4 GB.  I lives where the PCI device memory space is and hence the BIOS has turned it off.

If you have 8 GB RAM you would see 7 GB this way with 64bit/PAE, because the 3-4 space would still be turned off.

%%

What you need to do is instruct the BIOS to remap the memory that now lives between 3-4 GB to then live at 4-5 GB and *then* a 64bit or PAE kernel will be able to use it.

That remapping is named differently on each mainboard, you have to dig a little bit. The cheaper Intel chipsets do not do remapping at all.  Even if the chipset supports it (or the CPU has it's own memory controller like with AMD and i7), then you still have to have the BIOS writers put in this option, which some don't do.

---

### Post by PatrickVogeli on 2009-08-29
as Slim Odds says, I also believe the problems lays in some bad desing or implentation rather that in ubuntu. In my laptop, having 4GB, free -m shows a total of 3886 MB, that means 210 MB missing. which I'd say are for my graphic card, and intel with shared memory.

---

### Post by r m h on 2009-08-30
On a ThinkPad T61p with 4GB RAM:

$ uname -a
Linux icefog 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

# cat /proc/meminfo | head -1
MemTotal:        3922376 kB


On one of my servers with 16GB RAM:

$ uname -a
Linux iceax 2.6.28-13-server #45-Ubuntu SMP Tue Jun 30 22:56:18 UTC 2009 x86_64 GNU/Linux

# cat /proc/meminfo | head -1
MemTotal:       16262644 kB


I would agree that it's likely a BIOS issue if you're not seeing all of the RAM.  I believe AMI BIOS is highly suspect with its Windows-only features.

---

