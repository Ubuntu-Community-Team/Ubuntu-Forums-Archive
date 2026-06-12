---
title: "&quot;Your BIOS doesn't leave a aperture memory hole&quot; / &quot;This costs you 64 MB of RAM&quot;"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by felker2 on 2008-12-22
Hi,

My boot / dmesg is saying "Your BIOS doesn't leave a aperture memory hole" and "This costs you 64 MB of RAM". System is a Athlon64 X2 with 4GB RAM on Asus M2A-VM HDMI.

Details from dmesg:

```

[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 41ca000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.004000] Memory: 3916876k/4718592k available (3112k kernel code, 144816k reserved, 1575k data, 536k init)

```

I looked in the BIOS setup, but couldn't find anything with IOMMU nor Aperture there.
So I tried to solve this by playing with the IOMMU boot option: "iommu=noaperture" made the message go away, but I did not get more memory. Other iommu= options like off, soft, 32m resulted in kernel panics and things like that.

So: is there a way to get that 64MB memory back?

Some more details:

```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7ee0000 (usable)
[    0.000000]  BIOS-e820: 00000000d7ee0000 - 00000000d7ee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000d7ee3000 - 00000000d7ef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d7ef0000 - 00000000d7f00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)

```

and


```
sander@ubuntu810-on-athlon64:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3833       3786         47          0         25       2265
-/+ buffers/cache:       1496       2337
Swap:         3812          5       3806
sander@ubuntu810-on-athlon64:~$
```

---

### Post by Kilz on 2008-12-22
I have a similar error with a Asus M3A. My system has 4 gb and sees 3.87. Since I have never see more that 2 gb used it didnt seem like that big a deal. I have no idea how to fix it, but I'm going to watch this one in case its easy to fix.

---

### Post by dcstar on 2008-12-22
Try this boot option and let us know if it helps:

```
iommu=memaper=3
```

The issue seems to be with PCI-E video motherboards as there is no longer an AGP video port and therefore no AGP Aperture setting in the BIOS.

---

### Post by dcstar on 2008-12-22
> **dcstar said:**
> Try this boot option and let us know if it helps:

```
iommu=memaper=3
```

The issue seems to be with PCI-E video motherboards as there is no longer an AGP video port and therefore no AGP Aperture setting in the BIOS.

I just tried this myself and that boot option just sets the AGP Aperture to 256MB - which means that you lose more memory under 4G.

More research shows that this "feature" is deliberate as it allows 32-bit program access to the the AGP Aperture (by having the address under 4Gib), but if your motherboard doesn't remap the genuine RAM on top of your spare address space, you miss out on being able to use it!

Those of us old enough to remember the Expanded/Extended memory issue from the old original IBM PCs may recognise this sort of thing..... ;-)

It boils down to a 32-bit compatibility issue that only seems fixable in the BIOS.

---

### Post by Cope57 on 2008-12-22
AMD64 systems allow the use of the AGP aperture as an [_IOMMU_]("http://en.wikipedia.org/wiki/IOMMU"). Operating systems can take advantage of this to let normal PCI devices DMA to memory above 4 GB. Intel 64 systems require the use of bounce buffers, which are slower.

> The IOMMU's own memory accesses to its in-memory tables may themselves result in several kinds of errors,
including:
• Accesses to nonexistent or non-DRAM addresses (the IOMMU's isochronous virtual channel is restricted to
  DRAM addresses only).
• Uncorrectable ECC errors.
• Reserved value errors, including invalid or unsupported type codes in device table entries and reserved bits
  in page table entries.
The IOMMU records all detected memory access errors in its event log when event logging is enabled.
[AMD I/O Virtualization Technology (IOMMU) Specification Revision 1.0]("http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/34434.pdf") **PDF**

["DVMA Resources and IOMMU Translations]("http://developers.sun.com/solaris/developer/support/driver/wps/pci/html/DMA.doc.html#289")

---

### Post by lyricalpapa on 2008-12-22
Take a look at this bug report in the Red Hat Bugzilla – Bug 169115:

[https://bugzilla.redhat.com/show_bug.cgi?id=169115](https://bugzilla.redhat.com/show_bug.cgi?id=169115)

I've added the following to my menu.lst file:

"iommu=memaper=3 pci=nommconf"

I'm still working on trying to get CrossfireX to run, but don't have any boot problems now.

Adding "iommu=noaperture" had originally allowed me to install Kubuntu 8.10, but my display was still flickering when I activated the video driver, so I replaced the noaperature with the above.

Gigabyte GA-MA78GM-S2H motherboard
4 gig 1066 DDR2
ATI 3200 on motherboard
ATI HD 3450 in PCI-e slot

---

### Post by TheAlteredState on 2008-12-23
I'm also getting this on 8.10. Don't remember seeing it in 8.04?

I have an [ASUS M2N32-SLI Deluxe Wireless]("http://www.asus.com/products.aspx?modelmenu=2&model=1163&l1=3&l2=101&l3=0&l4=0") Mobo with 4GB of RAM, AMD Phenom 9600 and 2x 9600GT's in SLI.

---

### Post by Bloemetjesgordijn on 2008-12-23
I have got the same issue.
Never bothered to do something about it, until this thread. (its only 64 mb)

Never had this with Ubuntu 8.04

System:
Gigabyte GA-MA78GM-S2H motherboard
4 gig DDR2
ATI 3200 on motherboard
ATI HD 3450 in PCI-e slot

Cheerz

Bloemetjesgordijn

---

### Post by ericy on 2008-12-23
(deleted)

---

### Post by felker2 on 2008-12-23
> **ericy said:**
> I have a question about this line (in dmesg output):
> BIOS-e820: 0000000100000000 - 0000000120000000 (usable)

Does it mean the memory remap function is working(both the iommu hardware and its driver)?


The 'general' memory remapping / hoisting is working indeed: I almost have 4GB available. The point of my post is that the boot / dmesg is warning about 64 MB memory lost...

---

### Post by wd5gnr on 2008-12-23
I was somewhat surprised. I also noticed this after upgrading to 8.10. I put iommu=noaperture on the kernel line and the message went away! Good right? Um... well /proc/meminfo with the noaperture option says I have 4054548 bytes of memory. Without that option I get 4054960! So even though the message says I'm losing 64MB, it would appear get a very small boost in memory by NOT inhibiting the message (only 412 bytes, but I did NOT gain 64MB of free memory by doing this).

For the record my error message tells me my aperture points to "e820 RAM." Guess I'll have to google that.

---

### Post by felker2 on 2008-12-23
> **wd5gnr said:**
> I was somewhat surprised. I also noticed this after upgrading to 8.10. I put iommu=noaperture on the kernel line and the message went away! Good right? Um... well /proc/meminfo with the noaperture option says I have 4054548 bytes of memory. Without that option I get 4054960! So even though the message says I'm losing 64MB, it would appear get a very small boost in memory by NOT inhibiting the message (only 412 bytes, but I did NOT gain 64MB of free memory by doing this).


Yep, I have the same: no message anymore, but no extra memory.

> **wd5gnr said:**
> 
For the record my error message tells me my aperture points to "e820 RAM." Guess I'll have to google that.

Wikipedia gives this information on e820:


> e820 is shorthand to refer to the facility by which the BIOS of x86-based computer systems reports the memory map to the operating system or boot loader.

It is accessed via the int 15h call, by setting the AX register to value E820 in hexadecimal. It reports which memory address ranges are usable and which are reserved for use by the BIOS.

You will often see BIOS-e820 as the first thing reported by a Linux kernel booting, and it can also be seen with the dmesg command.

Sometimes the BIOS is buggy and incorrectly reports the reserved memory. This can cause memory testing software, like Memtest, to report errors.

I'll run memtest to see whether memtest says anything about my 64MB aperture stuff ...

---

### Post by dcstar on 2008-12-24
> **Bloemetjesgordijn said:**
> I have got the same issue.
Never bothered to do something about it, until this thread. (its only 64 mb)

Never had this with Ubuntu 8.04



Yep, 1.6% of 4G of RAM lost.... no wonder most people don't care.

My 8.04 system has these messages - but they aren't causing me any loss of sleep.

---

### Post by efeurich on 2008-12-24
@Fleker, So what dd you do precisely to get it to work?

I am having the same  problem here after installing Ubuntu 8.10. 
Before I had Ubuntu Studio and this problem never occurred.

---

### Post by felker2 on 2008-12-25
> **efeurich said:**
> @Fleker, So what dd you do precisely to get it to work?


Nothing. The message is non-blocking: the boot just continues.
I'm looking for a way to get the 64MB memory back.

---

### Post by Kilz on 2008-12-25
I built my brother a computer on tuesday. I used the same motherboard as I did,  2 gb ram, and a athlon64 x2 6000. He runs Intrepid 64bit (same as me), but I dont see the error message on his computer.

---

### Post by soxs on 2008-12-25
I would say get a bios update. For my brother, using an ASUS M3A32 MVP Deluxe, a BIOS updated added an option for IOMMU and so fixed that problem.

---

### Post by felker2 on 2008-12-25
> **Kilz said:**
> I built my brother a computer on tuesday. I used the same motherboard as I did,  2 gb ram, and a athlon64 x2 6000. He runs Intrepid 64bit (same as me), but I dont see the error message on his computer.

Do you think it's possible that the error message is gone because your brother is only using 2GB? I could try this myself by removing one memory bank.

Or is it something else, for example a newer BIOS?

---

### Post by felker2 on 2008-12-25
> **soxs said:**
> I would say get a bios update. For my brother, using an ASUS M3A32 MVP Deluxe, a BIOS updated added an option for IOMMU and so fixed that problem.

I'm already using the newest BIOS version 2201 on my Asus M2A-VM HDMI. See BIOS overview [here]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2A-VM HDMI").

---

### Post by felker2 on 2008-12-25
> **felker2 said:**
> Do you think it's possible that the error message is gone because your brother is only using 2GB? I could try this myself by removing one memory bank.


Well, I tried it myself, not by removing a memory bank, but by booting with the "mem=2G" kernel option.

Result ... no more error message. (And, yes, 2GB of RAM sacrificed ;-( ).
So: it must be related to the 4GB memory I've got. Problem not solved, but hopefully a step closer to the root cause.

```

[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Memory: 2048284k/2097152k available (3112k kernel code, 48480k reserved, 1575k data, 536k init)

```

mem is now 2009 MB, which is 39 less than 2048 MB
```

sander@ubuntu810-on-athlon64:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1155        853          0         25        347
-/+ buffers/cache:        782       1226
Swap:         3812          0       3812
sander@ubuntu810-on-athlon64:~$
```

And here is the start of dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=f6b0b4b8-a4c5-4dc0-a6e5-c6706741df4e ro quiet splash mem=2G
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dbee0000 (usable)
[    0.000000]  BIOS-e820: 00000000dbee0000 - 00000000dbee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dbee3000 - 00000000dbef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dbef0000 - 00000000dbf00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  user: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 0000000080000000 (usable)
[    0.000000]  user: 00000000dbee0000 - 00000000dbee3000 (ACPI NVS)
[    0.000000]  user: 00000000dbee3000 - 00000000dbef0000 (ACPI data)
[    0.000000]  user: 00000000dbef0000 - 00000000dbf00000 (reserved)
[    0.000000]  user: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  user: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x80000 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping

```

---

### Post by felker2 on 2008-12-25
In the meantime, I found something on the Linux Kernel Mailing List ([http://lkml.org/lkml/2008/4/21/415](http://lkml.org/lkml/2008/4/21/415)):

> 
Date	Mon, 21 Apr 2008 12:32:45 -0700
From	"Yinghai Lu" <>
Subject	Re: Aperture memory hole on x86_64

On Mon, Apr 21, 2008 at 12:13 PM, Alan <alan@clueserver.org> wrote:
> Something I noticed on my new AMD64 laptop with 4 gigs of RAM and a 256meg
>  video card.
>
>  I am running 2.6.25 from Fedora 9 beta.
>
>  When i boot, I get the following messages:
>
>  Checking aperture...
>  Node 0: aperture @ 9816000000 size 32 MB
>  Aperture beyond 4GB. Ignoring.
>  No AGP bridge found
>  Your BIOS doesn't leave a aperture memory hole
>  Please enable the IOMMU option in the bios setup
>  Mapping aperture over 65536 KB of RAM @ c000000
>
>  Is this a bug or is the x86_64 supposed to map the video aperture into
>  something that is 32bit addressable?
>
>  Also, there is no video settings at all on this particular laptop in bios.
>   (It is an HP dv6700 with almost everything maxed out.)
>
>  Just curious if this is correct behavior or not. (Since I am using the
>  xorg nv driver, it may not make any difference.)

you have 4G ram installed, and hw mem hole is enabled, so you memory
top is above 4g.
and kernel need to use gart for iommu.

and you bios didn't setup your gart because you didn't have agp..

please check if you BIOS have setup for gart, and you can set size to
64M, and then you could get 64M ram back.

YH





Again: 4GB.

This "Yinghai Lu" is a "LinuxBIOS and Linux Kernel developer", so I guess he must be an authority on this subject.

As my BIOS says nothing about IOMMU nor GART, I guess I'm out of luck. :-(

---

### Post by Kilz on 2008-12-25
> **felker2 said:**
> Do you think it's possible that the error message is gone because your brother is only using 2GB? I could try this myself by removing one memory bank.

Or is it something else, for example a newer BIOS?

I upgraded my bios to the latest to no effect.

---

### Post by Yellow Pasque on 2008-12-25
I had a recent Asus board (M3A78-EM) that had an option for Memory Remapping, but enabling it didn't make the message go away. Either that BIOS option didn't work correctly or another step is necessary. I ended up getting a refund on that board (for other reasons).

[http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt](http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt)

---

### Post by dcstar on 2008-12-25
> **felker2 said:**
> Well, I tried it myself, not by removing a memory bank, but by booting with the "mem=2G" kernel option.

Result ... no more error message. (And, yes, 2GB of RAM sacrificed ;-( ).
So: it must be related to the 4GB memory I've got. Problem not solved, but hopefully a step closer to the root cause.
.......

It is **not** an "error" message, it is an information message and the only real "problem" is that people see it because it has virtually no effect on system operation.

It only occurs when you have 4GB (or more) of RAM installed because the AGP Aperture address must be in the base 4GB address space (for 32-bit software compatibility). When you have 2GB RAM then there is 2GB of unused address space available so you do not lose any of the RAM.

---

### Post by Yellow Pasque on 2008-12-30
Just to clarify, it's not really an "error", but if you have a recent motherboard and your BIOS doesn't have an option for remapping the aperture above the 4GB limit, then write to your motherboard vendor and bug them to get with the (64-bit) times.

---

### Post by felker2 on 2008-12-30
> **Temüjin said:**
> Just to clarify, it's not really an "error", but if you have a recent motherboard and your BIOS doesn't have an option for remapping the aperture above the 4GB limit, then write to your motherboard vendor and bug them to get with the (64-bit) times.

Writing to Asus? ;-(

FWIW: the word IOMMU only occurs a few times on asus.com. One occurence is interesting: in the manual of "KFSN4-DRE Series KFSN4-DRE/SAS KFSN4-DRE/2S KFSN4-DRE Motherboard":

> 
IOMMU Option Menu

Main Advanced BIOS SETUP UTILITY [Disabled] Set GART size in systems without AGP, or disable altogether. Some OSes require valid GART for proper operation. If AGP is present, select appropriate option to ensure proper AGP operation. IOMMU Mode

IOMMU Mode [Disabled] Allows you to set GART size in systems without AGP, or disable altogether. Some operating systems require valid GART for proper operation. If AGP is present, select appropriate option to ensure proper AGP operation. Configuration options: [AGP Present] [Disabled] [32MB] [64MB] [128MB] [256MB] [512MB] [1GB]


I guess this is what I would need on my Asus mobo, right? I don't expect that Asus will introduce it, but the quote above proofs that Asus does know what IOMMU is ... ;-)
As the KFSN4-DRE is a 306 Euro mobo, I guess Asus only has that feature for high end mobo's.

---

### Post by valros on 2009-02-26
From a newer ASUS mobo I've also had this bug, when I enable "Remapping around memory hole" in the bios Ubuntu only then recognizes 3.2 Gigs of RAM, not the 4 in there. lshw shows 2 sticks of 2 gigs but under the gnome system monitor is says X memory used out of 3.2G.

---

### Post by jonah1980 on 2009-02-28
i also have this problem with amd phenom 9950 quad core and 8gig of ram on T3-M3N8200 asus barebone...

Been waiting for a fix for sometime, any word on one yet?

---

### Post by soxs on 2009-02-28
> **jonah1980 said:**
> i also have this problem with amd phenom 9950 quad core and 8gig of ram on T3-M3N8200 asus barebone...

Been waiting for a fix for sometime, any word on one yet?
Don't wait on firms doing their job, they rather die before.

---

### Post by pseudonym on 2009-03-02
One other solution is to rebuild your kernel without agp support. I haven't tried it myself but it stands to reason that it would work.

---

### Post by x-na on 2009-03-03
Just my 2 cents here, but my Asus M2N68 has this option in the northbridge -> memory configuration:

Memory Hole Remapping [Enabled]
Allows you to enable or disable the Memory Remapping Around Memory
Hole.Configuration options: [Disabled] [Enabled]

And this is what my 'free' says:

```
pekka@candy:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3960       3929         30          0         24       2583
-/+ buffers/cache:       1321       2638
Swap:         7632          5       7627

```


I'm just assuming other Asus boards might have this same option.

---

### Post by warpasylum on 2009-03-06
I've got the same issue here on my Acer Aspire 5050 with 4 GB of RAM.  I'll post back if I find anything.

---

### Post by warpasylum on 2009-03-09
Tried updating my Phoenix BIOS to 3309 and 3315. No luck with either. No mem remap option and ubuntu wouldn't boot. Went back to the original 3302 n' Ubuntu boots again.

---

### Post by marcelkoopman on 2009-03-09
Did you try iommu=false as boot option in grub configuration?

---

### Post by zika on 2009-03-09
[http://ubuntuforums.org/showpost.php?p=6855830&postcount=88](http://ubuntuforums.org/showpost.php?p=6855830&postcount=88)

---

### Post by Slim Odds on 2009-03-21
> **marcelkoopman said:**
> Did you try iommu=false as boot option in grub configuration?

Turning off the iommu is a bad idea (it disabled USB on my system).

A better solution is:```
iommu=noagp,noaperture
```

---

### Post by jo4hnc on 2009-03-24
Has anyone checked out this bug post?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

It may be overkill but might be worth a check.

---

### Post by philinux on 2009-03-24
Intrepid
```
Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 2047768k/2096768k available (3116k kernel code, 48544k reserved, 1575k data, 540k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated

```

I get a warning about aperture exceeding 4 gig, ignoring, in Intrepid but that error at boot is not reported in Jaunty, however it's still in dmesg.

Jaunty
```
Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ bb66000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 2025476k/2096768k available (4764k kernel code, 456k absent, 70148k reserved, 2541k data, 536k init)
```

---

### Post by qQChtIhpk1 on 2009-04-02
Suggest setting BIOS "Memory Hole Remapping" to "disable".  This reduced the messages to "Apeture beyond 4 GB - Ignoring".  this sounds better, but no guarantee.

Ubuntu 8.10 on XFXforce 750a SLI motherboard with AMD Phenom X3 cpu.

---

### Post by philinux on 2009-04-02
Fixed now anyway. Must just be a software thing.

---

### Post by presence1960 on 2009-04-16
I have read this thread many times and after careful consideration 64Mb of RAM is not that big of a deal. So for me I think the best option is to live with it or ignore it. No disrespect meant to anyone's ideas on this subject.

---

### Post by rbuergin on 2009-07-28
> **soxs said:**
> I would say get a bios update. For my brother, using an ASUS M3A32 MVP Deluxe, a BIOS updated added an option for IOMMU and so fixed that problem.

can you please tell me how to find this option? would be kind of you!

---

### Post by Slim Odds on 2009-07-28
> **rbuergin said:**
> can you please tell me how to find this option? would be kind of you!

These are in the /boot/grub/menu.lst file.

The best place to put it is in the "defoptions" section. 

Here's mine:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash iommu=noagp,noaperture vga=795
```

---

