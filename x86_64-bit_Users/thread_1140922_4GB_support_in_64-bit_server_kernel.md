---
title: "4GB support in 64-bit server kernel"
date: 2009-04-28
forum: x86 64-bit Users
---

### Post by alienfluid on 2009-04-28
So I installed 9.04 64-bit on my machine this weekend and then upgraded my RAM to 4GB (from 3GB) expecting to be able to use all 4GB of it on the 64-bit platform.

To my surprise, the system still sees only 3.1GB - BIOS correctly shows it as 4GB.

I read some posts that suggesting using the "server" kernel, so I installed the "linux-server" meta package from Synaptic and rebooted. Still the same - the system only recognized 3.1GB.

I know that the system has to reserve some address space for PCI devices, but isn't that only for x86 systems?

What gives?

```
farhan@farhan-linux:~$ uname -a
Linux farhan-linux 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux
farhan@farhan-linux:~$ cat /proc/meminfo
MemTotal:        3301464 kB
MemFree:         2590472 kB
Buffers:           30640 kB
Cached:           313684 kB
SwapCached:            0 kB
Active:           416808 kB
Inactive:         172064 kB
Active(anon):     303472 kB
Inactive(anon):        8 kB
Active(file):     113336 kB
Inactive(file):   172056 kB
Unevictable:           8 kB
Mlocked:               8 kB
SwapTotal:       5020272 kB
SwapFree:        5020272 kB
Dirty:               484 kB
Writeback:             0 kB
AnonPages:        244596 kB
Mapped:            75204 kB
Slab:              32740 kB
SReclaimable:      18496 kB
SUnreclaim:        14244 kB
PageTables:        17928 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6671004 kB
Committed_AS:     870428 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      275464 kB
VmallocChunk:   34359461371 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       49696 kB
DirectMap2M:     3348480 kB
```

---

### Post by Arup on 2009-04-28
Update your system BIOS.

---

### Post by sonicb00m on 2009-04-28
> **Arup said:**
> Update your system BIOS.

Yeha must be something with your board. The 64bit should have no problem reading 4gb (mine does).

The server kernel for i386 will enable over 3gb for 32 bit OS (but this comes at a performance loss, apparently).

---

### Post by jespdj on 2009-04-28
Look if your BIOS has a "memory remapping" (or something similar) setting and make sure that it is enabled.

---

### Post by alienfluid on 2009-04-28
Thanks for the suggestions.

I checked in my BIOS and there's no option for "memory remapping" (or something similar).

I dual boot this system with Windows 7 (Beta) and it can see all of 4GB without any issue, so I suspect it's not a BIOS issue. 

Is there a command that will show me if the OS has reserved any space for PCI devices etc. in Linux?

---

### Post by sanderj on 2009-04-28
Your question is a FAQ. Search google for dmesg uname grep lm bios. See here: [http://www.google.com/search?q=dmesg+uname+grep+lm+bios+site%3Aubuntuforums.org](http://www.google.com/search?q=dmesg+uname+grep+lm+bios+site%3Aubuntuforums.org)

---

### Post by sanderj on 2009-04-28
> **alienfluid said:**
> 

I dual boot this system with Windows 7 (Beta) and it can see all of 4GB without any issue, so I suspect it's not a BIOS issue. 


Even 32-bit Windows Vista+ will report it 'has' 4GB in the Control Panel -> System. However, this is a 'copy' from the hard core BIOS info, and not what Windows can actually use.

> **alienfluid said:**
> 
Is there a command that will show me if the OS has reserved any space for PCI devices etc. in Linux?

This is part of the FAQ. Hint: "dmesg | head -25' or even better 'dmesg | grep e820'.

---

### Post by alienfluid on 2009-04-28
Yes, found it right after I posted the message.

This is what dmesg is telling me:

> farhan@farhan-linux:~$ dmesg | grep e820
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf688c00 (usable)
[    0.000000]  BIOS-e820: 00000000cf688c00 - 00000000cf68ac00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf68ac00 - 00000000cf68cc00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf68cc00 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
farhan@farhan-linux:~$ free -kolt
             total       used       free     shared    buffers     cached
Mem:       3301464     739288    2562176          0      31356     286764
Low:       3301464     739288    2562176
High:            0          0          0
Swap:      5020272          0    5020272
Total:     8321736     739288    7582448

ffb00000 roughly translates to slightly <4GB, so the system can certainly see all of the memory. 'free' shows only 3.1GB usable though. By the way, I rebooted into "memtest" and it can only see 3.1GB as well. 

None of the posts I saw really had a resolution for this if the BIOS doesn't give a "memory remapping" option. I'll look for updates BIOS for my system from Dell, but I'm not keeping my hopes high.

---

### Post by sanderj on 2009-04-28
Only the "usable" parts are ... usable. ;-)

So, in your case:

```
[ 0.000000] BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[ 0.000000] BIOS-e820: 0000000000100000 - 00000000cf688c00 (usable)

```

Only memory above 0000000100000000 will result in more memory than 3.2 GB. You need a not-too-old Mobo & BIOS to use memory above 0000000100000000; you need the Memory Remapping / Hoisting for that.

So upgrade your BIOS to the newest.

If you post here which (Dell?) system you have, we could have a look if that system supports 3.2+GB memory at all.

EDIT:

Google Calculator will help telling how much usable memory you now have in total:

[http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=1qV&q=(0x00000000000a0000+-+0x0000000000000000++)+%2B+(0x00000000cf688c00+-+0x0000000000100000)++in+decimal&btnG=Zoeken&meta=](http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=1qV&q=(0x00000000000a0000+-+0x0000000000000000++)+%2B+(0x00000000cf688c00+-+0x0000000000100000)++in+decimal&btnG=Zoeken&meta=)

will say:

(0x00000000000a0000 - 0x0000000000000000) + (0x00000000cf688c00 - 0x0000000000100000) = 3 479 342 080

To see how much that is in GB (=2^30), Google Calculator will help again:

[http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=nFB&q=3479342080+%2F+2^30&btnG=Zoeken&meta=](http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=nFB&q=3479342080+%2F+2^30&btnG=Zoeken&meta=)

3 479 342 080 / (2^30) = 3.24038982


And now everything in one URL: 

[http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=(0x00000000000a0000+-+0x0000000000000000++)+%2B+(0x00000000cf688c00+-+0x0000000000100000)+)%2F+2^30in+decimal&btnG=Zoeken&meta=](http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=(0x00000000000a0000+-+0x0000000000000000++)+%2B+(0x00000000cf688c00+-+0x0000000000100000)+)%2F+2^30in+decimal&btnG=Zoeken&meta=)

So: 3.24 GB usable memory ...

---

### Post by alienfluid on 2009-04-28
D'oh. Thanks!

It is a Dell Dimension 5150 Pentium D 820 and the Dell website says that it should be able to support 4GB. I just upgraded the BIOS to A07 (from January 2007) and I don't see a newer one available unless I am missing something.

Also, I just noticed something in my dmesg:
> 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf688c00 (usable)
[    0.000000]  BIOS-e820: 00000000cf688c00 - 00000000cf68ac00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf68ac00 - 00000000cf68cc00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf68cc00 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xcf688 max_arch_pfn = 0x3ffffffff
**[COLOR=Red][    0.000000] Scanning 2 areas for low memory corruption[/COLOR]**
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000093000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cf688c00 (usable)
[    0.000000]  modified: 00000000cf688c00 - 00000000cf68ac00 (ACPI NVS)
[    0.000000]  modified: 00000000cf68ac00 - 00000000cf68cc00 (ACPI data)
[    0.000000]  modified: 00000000cf68cc00 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-00000000cf688000
[    0.000000]  0000000000 - 00cf600000 page 2M
[    0.000000]  00cf600000 - 00cf688000 page 4k
[    0.000000] kernel direct mapping tables up to cf688000 @ 10000-16000
[    0.000000] last_map_addr: cf688000 end: cf688000

Is that normal to have this there?

---

### Post by alienfluid on 2009-04-28
By the way, how do I tell what the "(reserved)" memory ranges are actually reserved for?

---

### Post by Slim Odds on 2009-04-28
> **alienfluid said:**
> I checked in my BIOS and there's no option for "memory remapping" (or something similar).

Some times it goes under different names. Maybe "memory hole", or something....  else....

---

### Post by alienfluid on 2009-04-28
Yeah, looked through the BIOS quite thoroughly but no luck :(

---

### Post by Slim Odds on 2009-04-28
> **alienfluid said:**
> Yeah, looked through the BIOS quite thoroughly but no luck :(

How much memory does your motherboard support?

---

### Post by Yellow Pasque on 2009-04-28
It seems to be a common problem. I wish I could find the link on Intel's site that explained why they don't force their board partners to implement memory remapping properly on their ICH southbridges. "It's a feature, not a bug. We swear!" (My paraphrasing)

AMD boards seem to be hit and miss too, but I don't remember an official doc on it.

---

### Post by digitalextremes on 2009-04-28
> **alienfluid said:**
> So I installed 9.04 64-bit on my machine this weekend and then upgraded my RAM to 4GB (from 3GB) expecting to be able to use all 4GB of it on the 64-bit platform.

To my surprise, the system still sees only 3.1GB - BIOS correctly shows it as 4GB.

I read some posts that suggesting using the "server" kernel, so I installed the "linux-server" meta package from Synaptic and rebooted. Still the same - the system only recognized 3.1GB.

I know that the system has to reserve some address space for PCI devices, but isn't that only for x86 systems?

What gives?

```
farhan@farhan-linux:~$ uname -a
Linux farhan-linux 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux
farhan@farhan-linux:~$ cat /proc/meminfo
MemTotal:        3301464 kB
MemFree:         2590472 kB
Buffers:           30640 kB
Cached:           313684 kB
SwapCached:            0 kB
Active:           416808 kB
Inactive:         172064 kB
Active(anon):     303472 kB
Inactive(anon):        8 kB
Active(file):     113336 kB
Inactive(file):   172056 kB
Unevictable:           8 kB
Mlocked:               8 kB
SwapTotal:       5020272 kB
SwapFree:        5020272 kB
Dirty:               484 kB
Writeback:             0 kB
AnonPages:        244596 kB
Mapped:            75204 kB
Slab:              32740 kB
SReclaimable:      18496 kB
SUnreclaim:        14244 kB
PageTables:        17928 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6671004 kB
Committed_AS:     870428 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      275464 kB
VmallocChunk:   34359461371 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       49696 kB
DirectMap2M:     3348480 kB
```

I have the same issue, I posted in a different thread in this same forum....my system has 4GB (Lenove T60) and Vista 64 bit shows full GB, 8.04 and 9.10 both show 3GB. If it was the BIOS then how come Vista can read it properly already without the need of any fix to the BIOS?

---

### Post by sanderj on 2009-04-29
> **alienfluid said:**
> Yeah, looked through the BIOS quite thoroughly but no luck :(

You could indeed be out of luck: if your newest BIOS is dated January 2007, then your Mobo must be older and it can very well be that memory hoisting / remapping was not implemented.

---

### Post by scheuri on 2009-04-29
Well, a few ideas (however, I can not say for sure they will work or give more information):

- Use memtest to check your memory. I personally had to make the unpleasant experience that I had faulty memory which worked fine, but was just not used completely. Maybe, just maybe, that is the case here, too.

- Do you have integrated graphics which takes its graphics memory from the RAM? (shared memory)
If that is the case, maybe the missing RAM is used by the graphics card...

- please post your "uname -a" output.

cheers
scheuri

---

### Post by sanderj on 2009-04-29
> **digitalextremes said:**
> I have the same issue, I posted in a different thread in this same forum....my system has 4GB (Lenove T60) and Vista 64 bit shows full GB, 8.04 and 9.10 both show 3GB. If it was the BIOS then how come Vista can read it properly already without the need of any fix to the BIOS?

Maybe you should first read a thread before bumping into it?

Anyway, as said:

> 
Even 32-bit Windows Vista+ will report it 'has' 4GB in the Control Panel -> System. However, this is a 'copy' from the hard core BIOS info, and not what Windows can actually use.

So: Windows is being friendly (or just lying) to you. It reports the RAM *installed*, which is something else then the RAM *usable/available*. See [http://support.microsoft.com/kb/946003/](http://support.microsoft.com/kb/946003/) . I haven't got Windows, so I can't check this, but the article seems to say that "the System Information tool (Msinfo32.exe)" will tell you the real memory information.

---

### Post by alienfluid on 2009-04-29
Thanks for the ideas folks, but I'm still out of luck.

I performed a memtest86+ and everything came back clean. The weird thing is that memtest86+ also sees only 3.2 GB - so it's got to be an issue with the BIOS or the Motherboard. Right?

The motherboard is an Intel i945P/G. Looking at the specs online, it's supposed to support 4GB so it's not a hardware limitation.

Perhaps I will install Vista or Windows 7 64-bit on the other partition to see what it tells me. If it can address the entire 4GB then there's something wrong with my configuration otherwise it's my hardware (or BIOS).

I'll try to post something on the Dell forums to see if anyone has access to an updated BIOS for this system.

Here's the uname -a output as requested:

```
farhan@farhan-linux:~$ uname -a
Linux farhan-linux 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

```

---

### Post by scheuri on 2009-04-29
> **alienfluid said:**
> Thanks for the ideas folks, but I'm still out of luck.

I performed a memtest86+ and everything came back clean. The weird thing is that memtest86+ also sees only 3.2 GB - so it's got to be an issue with the BIOS or the Motherboard. Right?
[...]


Then I ask again, what kind of graphic card is installed? Does that card use RAM (shared memory) as video RAM or does it have own memory...
It is just an idea...

cheers
scheuri

---

### Post by alienfluid on 2009-04-29
It's integrated graphics. And yes, it uses shared RAM - but it is configured for quite a low number in the BIOS - certainly not >700MB. I can try sticking in a dedicated graphics card to see if it makes a difference though.

UPDATE:

I put in a dedicated PCI Express video card (Nvidia 8500GT 256MB) and it did not make a difference :(

---

### Post by sanderj on 2009-04-29
@alienfluid:

Can you post the output of 'cat /proc/mtrr' here?

Reason: I checked on a modern 4GB system *with* memory hoisting / remapping, and that system had this /proc/mtrr:

```
reg00: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: uncachable
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size=  512MB, count=1: write-back
reg04: base=0x120000000 ( 4608MB), size=  256MB, count=1: write-back
reg05: base=0x0cf700000 ( 3319MB), size=    1MB, count=1: uncachable
reg06: base=0x0cf800000 ( 3320MB), size=    8MB, count=1: uncachable

```
I'm no mtrr expert, but I'm trying to find out whether this mtrr info tells 
1) yes, there is 4GB (the line with "base=0x000000000 (    0MB), size= 4096MB")
2) the BIOS is doing remapping (the stuff with base=0x1..).

So: can you post your /proc/mtrr?

---

### Post by alienfluid on 2009-04-29
Sure, here it is:
 
[EMAIL="farhan@farhan-linux:~$"]```
 
[/EMAIL][EMAIL="farhan@farhan-linux:~$"]farhan@farhan-linux:~$[/EMAIL][EMAIL="farhan@farhan-linux:~$"] cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x0cff00000 ( 3327MB), size=    1MB, count=1: uncachable


```[/EMAIL]

---

### Post by alienfluid on 2009-04-29
Okay, I think I found the answer to the problem:
 
[COLOR=#1f497d][SIZE=3][FONT=Calibri]>  
[COLOR=#1f497d][SIZE=3][FONT=Calibri]Q: I have 4GB of RAM in my new Lenovo T60P and I am running Vista x64, why do I still see only 3GB or RAM!?  [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]A: 64bit client and server OS’s all support remap on hardware with remap support and, as such all physical memory will be visible up to the limits of the SKU and hardware. Unfortunately, while nearly all desktop and server x64 systems built in the last 3 years support PAE/x64 remap, prior to the new Santa Rosa chipset (which shipping in June-July 2007), no Intel chipset based notebooks, even if equipped with x64 capable Core2 based CPU’s, support memory remap. As a result most Intel based notebooks purchased in the last year will never see all 4GB of installed RAM.  [/FONT][/SIZE][/COLOR]
[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][FONT=Calibri][SIZE=3][/SIZE][/FONT][/COLOR] 
[COLOR=#1f497d][FONT=Calibri][SIZE=3]Basically, I am assuming that my chipset is old (pre 2007) and does not support PAE/x64 remap. I bought the system in 2006 and it has been in production for at least 6 months prior so it's safe to say that it's a valid assumption. I'll just live with 3.2Gb for now - it's still better than (if only slightly) 3GB that I had previously.[/SIZE][/FONT][/COLOR]

---

### Post by sanderj on 2009-04-29
> **alienfluid said:**
> Sure, here it is:

```
 
 
[EMAIL="farhan@farhan-linux:~$"] cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x0cff00000 ( 3327MB), size=    1MB, count=1: uncachable


```


Ah. Pity. This only counts up to 2048+1024+256-1=3.25GB. That is the same amount as seen by dmesg/e820 (which is good), but I had hoped to see all 4GB RAM here, just to be able to explain that Windows *can* report 4GB RAM, as you said earlier:

> I dual boot this system with Windows 7 (Beta) and it can see all of 4GB without any issue,

So I guess I have to look further how Ubuntu can see how much physical RAM is installed (apart from how much is usable) ...

---

### Post by sanderj on 2009-04-29
@alienfluid

Can you do another test? Can you 'sudo lshw > lshw.txt', then search that file lshw.txt for the part starting with '*-memory', and post that memory part here?

Here is the output of my 1GB laptop, showing the two memory DIMMs in my system:

```

     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DDRII 1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: SODIMM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DDRII 2
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)

```

Hopefully your lshw will show the physical 4GB too ...


EDIT:

A quick & dirty one-liner to get the physical memory info:

```

ubuntu@ubuntu:~$ sudo lshw | grep -A 200 memory | grep -B 200 -e pci$ | grep -vi pci
     *-memory             
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DDRII 1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: SODIMM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DDRII 2
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
ubuntu@ubuntu:~$

```

Please run this on your 4GB system ...

---

### Post by sanderj on 2009-04-29
And FWIW, here's the output of my one-liner on a 4GB system, with memory remapping BIOS, and a 32-bit OS:


```

ubuntu@ubuntu:~$  sudo lshw | grep -A 200 memory | grep -B 200 -e pci$ | grep -vi pci
PCI (sysfs)  
     *-memory             
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: 64T256020EDL2.5C2
             vendor: 7F7F7F7F7F510000
             physical id: 0
             serial: 24006625
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: 64T256020EDL2.5C2
             vendor: 7F7F7F7F7F510000
             physical id: 1
             serial: 24006724
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3528        668       2859          0         78        328
-/+ buffers/cache:        261       3267
Swap:            0          0          0
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
ubuntu@ubuntu:~$

```

So:
with my lshw one-liner, all physical memory (4GB) is found. That's good. It's not OS-bitness dependant, so that's handy. I think it is not BIOS dependant, but I'm not 100% about that.

---

### Post by alienfluid on 2009-04-29
Yes, it seems like the OS can "see" the entire 4GB, just can't address it:
 
```
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 99U5429-005.A00LF
             vendor: 7F98000000000000
             physical id: 0
             serial: 0B1E9052
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: VS1GB667D2
             vendor: 7F7F9E0000000000
             physical id: 1
             serial: 15080644
             slot: DIMM_3
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 99U5429-005.A00LF
             vendor: 7F98000000000000
             physical id: 2
             serial: 341ECF90
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: VS1GB667D2
             vendor: 7F7F9E0000000000
             physical id: 3
             serial: 32300526
             slot: DIMM_4
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
```
 
Also, I confirmed that my chipset doesn't support memory remapping:
 
[http://en.wikipedia.org/wiki/Intel_chipset](http://en.wikipedia.org/wiki/Intel_chipset)
 
From the page:
 
945PLakeport82945P (MCH)ICH7May 2005Pentium 4, Pentium D, Celeron D533 / 800 / 1066DDR2 400/533/6674GB[SIZE=2]1[/SIZE]No / NoPCI-Express x16945PLLakeport82945PL (MCH)ICH7 ?Pentium 4, Pentium D, Celeron D533 / 800DDR2 400/5332GBNo / NoPCI-Express x16946PLLakeport82946PL (MCH)ICH7 ?Pentium 4, Pentium D, Celeron D533 / 800DDR2 533/6674GB[SIZE=2]1[/SIZE]No / NoPCI-Express x16945GLakeport-G82945G (GMCH)ICH7May 2005Pentium 4, Pentium D, Celeron D533 / 800 / 1066DDR2 400/533/6674GB[SIZE=2]1[/SIZE]No / No
[LIST]
[*]PCI-Express x16
[*]Integrated [GMA 950]("http://ubuntuforums.org/wiki/Intel_GMA#GMA_950")
[/LIST]945GZLakeport-G82945GZ (GMCH)ICH7 ?Pentium 4, Pentium D, Celeron D533 / 800DDR2 400/5332GBNo / NoIntegrated GMA 950946GZLakeport-G82946GZ (GMCH)ICH7 ?Pentium 4, Pentium D, Celeron D533 / 800DDR2 533/6674GB[SIZE=2]1[/SIZE]No / No
[LIST]
[*]PCI-Express x16
[*]Integrated [GMA 3000]("http://ubuntuforums.org/wiki/Intel_GMA#GMA_3000")
[/LIST]
[COLOR=red]**[SIZE=2]1[/SIZE] Lakeport chipsets lacks support for remapping memory; the size of addressable memory space may be less than 4GB, regardless whether the processor operates in 64-bit mode.**[/COLOR]
 
I have the 945P :(.
 
Well, at least we got to the bottom of this - thanks a bunch for your help!

---

### Post by sanderj on 2009-04-29
FWIW: a handy tool to read your BIOS version and some BIOS capabilities (don't know about Memory Hoisting / Remapping): 

```

ubuntu@ubuntu:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: FUJITSU // Phoenix Technologies Ltd.
	Version: Version 1.24 
	Release Date: 04/26/2007
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		3.5"/720 KB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 1.36

Handle 0x0027, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 2
		enUS
		jaJP
	Currently Installed Language: enUS

ubuntu@ubuntu:~$

```

---

### Post by sanderj on 2009-04-29
> **alienfluid said:**
> Yes, it seems like the OS can "see" the entire 4GB, just can't address it


That must be then how Vista SP1+ sees and reports 4GB, even when on non-remapping hardware.

Thank you for running my MTRR and lshw one-liners. Hopefully it will help future cases of "Help, my 4GB system only sees 3.2GB".

In the meantime I found a even shorter one-line hack to report on the physical RAM:

```


ubuntu@ubuntu:~$ sudo lshw | grep -A 200 memory | grep size:
          size: 1GiB     
             size: 512MiB
             size: 512MiB

ubuntu@ubuntu:~$ sudo lshw | grep -A 200 memory | grep size: | head -1
          size: 1GiB     

ubuntu@ubuntu:~$ sudo lshw | grep -A 200 memory | grep -B 200 -e pci$ | grep -e size: -e bank
          size: 1GiB      
        *-bank:0
             size: 512MiB
        *-bank:1
             size: 512MiB
ubuntu@ubuntu:~$


```

Some more lshw options:

```

ubuntu@ubuntu:~$ sudo lshw -short | grep memory
/0/0                         memory      64KiB BIOS
/0/400/700                   memory      32KiB L1 cache
/0/400/701                   memory      2MiB L2 cache
/0/1000                      memory      4GiB System Memory
/0/1000/0                    memory      2GiB DIMM DDR Synchronous 800 MHz (1.2 ns)
/0/1000/1                    memory      2GiB DIMM DDR Synchronous 800 MHz (1.2 ns)
ubuntu@ubuntu:~$

```

and this one:

```

ubuntu@ubuntu:~$ sudo lshw -class memory
  *-firmware              
       description: BIOS
       vendor: Dell Inc.
       physical id: 0
       version: A05 (07/30/2008)
       size: 64KiB
       capacity: 1984KiB
       capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 700
       size: 32KiB
       capacity: 32KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 701
       size: 2MiB
       capacity: 2MiB
       clock: 66MHz (15.0ns)
       capabilities: pipeline-burst internal varies unified
  *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM DDR Synchronous 800 MHz (1.2 ns)
          product: 64T256020EDL2.5C2
          vendor: 7F7F7F7F7F510000
          physical id: 0
          serial: 24006625
          slot: DIMM_A
          size: 2GiB
          width: 64 bits
          clock: 800MHz (1.2ns)
     *-bank:1
          description: DIMM DDR Synchronous 800 MHz (1.2 ns)
          product: 64T256020EDL2.5C2
          vendor: 7F7F7F7F7F510000
          physical id: 1
          serial: 24006724
          slot: DIMM_B
          size: 2GiB
          width: 64 bits
          clock: 800MHz (1.2ns)
ubuntu@ubuntu:~$

```

---

### Post by sanderj on 2009-04-30
Interesting to see: even a 32-bit Ubuntu will show a dmesg with memory (remapping) above the 0000000100000000 = 4GB barrier, and will mark it as usable. So this will only tell you something about the hardware and BIOS, not about the OS!

Example:

```

[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe5c800 (usable)
[    0.000000]  BIOS-e820: 00000000dfe5c800 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xdfe5c max_arch_pfn = 0x100000

```

And then there was a second memory thing, which I don't understand:

```
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000dfe5c800 (usable)
[    0.000000]  modified: 00000000dfe5c800 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
```


Filtered it looks like this:

```
ubuntu@ubuntu:~$ dmesg | grep usable
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe5c800 (usable)
[    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)

[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 0000000000100000 - 00000000dfe5c800 (usable)
[    0.000000]  modified: 0000000100002000 - 0000000120000000 (usable)
ubuntu@ubuntu:~$ 
```


It seems the modified version has split the first e820 line into three lines / smaller memory areas. I don't know why.

---

