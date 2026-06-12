---
title: "RAM limited to 3.4GB - what gives?"
date: 2009-02-06
forum: x86 64-bit Users
---

### Post by Eiríkr on 2009-02-06
Hey there folks, I've got a possible stumper for you --

[SIZE="3"]**Hardware:**[/SIZE]

[LIST]
[*]Dell Dimension 5150
[*]Intel Pentium D 2.8GHz dual-core
[*]6GB RAM, 2GB each in slots 1 & 3, 1GB each in slots 2 & 4 -- paired up, as required
[/LIST]

[SIZE="3"]**Problem:**[/SIZE]

BIOS sees all 6GB.  

Formerly-installed (now overwritten) Fedora 9 saw all 6GB.

Installed desktop Ubuntu 8.10 x86_64, using the [font=courier]ubuntu-8.10-desktop-amd64.iso[/font] image, and now I can only seem to access 3.4GB...  ???

```
eirikr@Boreas:~$ uname -a
Linux Boreas 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
eirikr@Boreas:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3519        898       2621          0         16        240
-/+ buffers/cache:        641       2878
Swap:         1482          0       1482
eirikr@Boreas:~$
```

I've tried switching from the generic kernel to the server kernel, but I have the same problem.

```
eirikr@Boreas:~$ uname -a
Linux Boreas 2.6.27-11-server #1 SMP Thu Jan 29 20:13:12 UTC 2009 x86_64 GNU/Linux
eirikr@Boreas:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3519       1020       2499          0         23        382
-/+ buffers/cache:        613       2905
Swap:         1482          0       1482
eirikr@Boreas:~$
```

What gives?  I fully understand that 32-bit systems are limited to 3.4GB due to the inherent mathematical limits of 32-bit memory addresses.  This is why I chose the 64-bit Ubuntu version.  Yet even 64-bit Ubuntu seems unable to see all 6GB of memory.  Just in case, I checked the kernel compilation options listed in [FONT=Courier]/boot/config-2.6.27-11-generic[/FONT] and [FONT=Courier]/boot/config-2.6.27-11-server[/FONT], but I see no mention of any CONFIG_HIGHMEM options.  

Fedora 9 *could* see all 6GB, so I must conclude that the problem is with Ubuntu.  Anyone have any leads?

(NB -- posting here since this seems the more appropriate forum than Absolute Beginner Talk, where I first posted about this issue in [thread=835981]this thread[/thread].)

---

### Post by jespdj on 2009-02-06
I think that CONFIG_HIMEM etc. only applies to 32-bit systems. On 64-bit, there is no special 4 GB limit.

Look in the BIOS settings of your computer if there's an option called "memory remapping" or something similar. If you find it, enable it.

If memory remapping is not enabled, then your graphics card and other devices will take up some of the address space below 4 GB, which can make it look like you have less RAM than what's actually installed.

---

### Post by jrusso2 on 2009-02-06
Is that a dual core or a core2duo?  I think the dual cores are 32 bits but then I am wondering how you got 64 bit Linux to install.

---

### Post by jespdj on 2009-02-06
> **jrusso2 said:**
> Is that a dual core or a core2duo?  I think the dual cores are 32 bits but then I am wondering how you got 64 bit Linux to install.
What do you mean with "dual cores are 32 bits"?

Intel's original Core Duo (NOT Core 2 Duo) was 32-bit only. All Core 2 Duo processors are 64-bit. Some of the later Pentium models are also 64-bit.

If you try to boot a 64-bit Live CD on a computer without 64-bit processor, you'll very quickly get a message and it can't boot. It's impossible to install 64-bit Ubuntu on a 32-bit system.

So if the OP has 64-bit Ubuntu installed, then you can be sure that he has a 64-bit processor.

---

### Post by sanderj on 2009-02-06
As you're running x86_64, you must have a x86_64 system, so that's good.

I would then say: post "dmesg | head -25" here in this forum to see what the BIOS is offering to the Linux kernel (see the BIOS-e820 lines in the dmesg). I guess there is nothing offered above 0000000100000000, and thus Linux will only see 3.2/3.4 GB. I would then say: update your BIOS. However ...

... as you say Fedora 9 does see the full 6 GB, you could live-boot Fedora and post the "free -m" and "dmesg | head -25" output here. I would be very interested to see that Fedora does see 6 GB, where Ubuntu only sees 3.4 GB ...


BTW / FWIW: [http://www.dell.com/content/products/productdetails.aspx/dimen_5150?c=us&cs=28&l=en&s=dfb](http://www.dell.com/content/products/productdetails.aspx/dimen_5150?c=us&cs=28&l=en&s=dfb) seems to say this Dell can only have 4GB RAM.

---

### Post by Eiríkr on 2009-02-06
> **jespdj said:**
> I think that CONFIG_HIMEM etc. only applies to 32-bit systems. On 64-bit, there is no special 4 GB limit.

Look in the BIOS settings of your computer if there's an option called "memory remapping" or something similar. If you find it, enable it.

If memory remapping is not enabled, then your graphics card and other devices will take up some of the address space below 4 GB, which can make it look like you have less RAM than what's actually installed.

Thanks for explaining about HIMEM; I'm really not familiar with kernel ops.

The only memory remapping option I'm finding in the BIOS allows me to set it so the BIOS only shows the first 2GB, for systems that will fail to boot if they see more than that -- this sounds kinda like the opposite of what you describe, some option to allow me to *show* memory instead of hiding it.  

Plus, I have 6GB in the hardware; I have trouble believing that shared memory for video and the like would take up 2.6GB.  :)

Cheers,

-- Eiríkr

---

### Post by mªrty on 2009-02-06
I don't have extensive experience with ubuntu x86_64, but I'm just thinking of other things you could try to see what detects your full 6GB:
[INDENT][LIST]
[*]Memtest86
[*]Livecd (from any other distro)
[/LIST][/INDENT]

Last, and most significant, do you have the latest **BIOS** version?

---

### Post by Coreigh on 2009-02-06
I know its not Windows but ...

On my Windows server I had to enable Physical Address Extension (PAE) to access memory beyond 3.4GB.

---

### Post by sanderj on 2009-02-06
> **Coreigh said:**
> I know its not Windows but ...

On my Windows server I had to enable Physical Address Extension (PAE) to access memory beyond 3.4GB.

PAE is a 32-bit thing. Not needed (and not possible?) if you run a 64-bit OS. The OP is running a 64-bit OS ...

---

### Post by Eiríkr on 2009-02-07
> **sanderj said:**
> As you're running x86_64, you must have a x86_64 system, so that's good.

I would then say: post "dmesg | head -25" here in this forum to see what the BIOS is offering to the Linux kernel (see the BIOS-e820 lines in the dmesg). I guess there is nothing offered above 0000000100000000, and thus Linux will only see 3.2/3.4 GB. I would then say: update your BIOS. However ...

Bingo!  Duh, I should've thought to look in dmesg.  <facepalm>  The smoking gun:

```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe88c00 (usable)
[    0.000000]  BIOS-e820: 00000000dfe88c00 - 00000000dfe8ac00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfe8ac00 - 00000000dfe8cc00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfe8cc00 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x180000 max_arch_pfn = 0x3ffffffff
[    0.000000] WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 2048MB of RAM.
```

So the BIOS is definitely *showing* all 6GB -- that last [font=courier]BIOS-e820[/font] line specifies a hex value of 0000000180000000 as the upper limit, i.e. 6GB.  

> **sanderj said:**
> ... as you say Fedora 9 does see the full 6 GB, you could live-boot Fedora and post the "free -m" and "dmesg | head -25" output here. I would be very interested to see that Fedora does see 6 GB, where Ubuntu only sees 3.4 GB ...

After mucking about for a while and re-installing Fedora 9, I had another <facepalm> moment -- I'd seen the 6GB number in System Monitor, sure enough, only it was apparently for how much spare room was left in the partition.  Gawd, I'm having a really stupid couple days.  Though somewhat in my defense, the previous Fed 9 install (the one I overwrote with Ibex) behaved differently, which is kinda confusing.  But I only did a quick-and-dirty install this time, and didn't update anything, so maybe that's what's different...

Oddly enough, Fedora's dmesg reports a different amount of RAM lost to MTRR problems:

```
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000dfe88c00 (usable)
 BIOS-e820: 00000000dfe88c00 - 00000000dfe8ac00 (ACPI NVS)
 BIOS-e820: 00000000dfe8ac00 - 00000000dfe8cc00 (ACPI data)
 BIOS-e820: 00000000dfe8cc00 - 00000000e0000000 (reserved)
 BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
 BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
Entering add_active_range(0, 0, 160) 0 entries of 3200 used
Entering add_active_range(0, 256, 917128) 1 entries of 3200 used
Entering add_active_range(0, 1048576, 1572864) 2 entries of 3200 used
end_pfn_map = 1572864
WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 2560MB of RAM.
```

This 512MB difference from 4GB would leave roughly 3.4GB available, which is what the System Monitor GUI shows in both OSes.

Looking into [font=courier]/proc/mtrr[/font] in Ibex shows the following, clearly indicating only 3.4GB:

```
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 512MB: write-back, count=1
reg03: base=0xdff00000 (3583MB), size=   1MB: uncachable, count=1
```


> **sanderj said:**
> BTW / FWIW: [http://www.dell.com/content/products/productdetails.aspx/dimen_5150?c=us&cs=28&l=en&s=dfb](http://www.dell.com/content/products/productdetails.aspx/dimen_5150?c=us&cs=28&l=en&s=dfb) seems to say this Dell can only have 4GB RAM.

Yep, which I always figured was due to XP (which is generally always 32-bit in consumer-level computers, unless you go out of your way to find the 64-bit variety).  Since this is Dell we're talking about, I assumed they were simply describing, in CYA fashion, the 32-bit OS limitation on RAM.  It even says something very similar in their [owner's manual for the Dimension 5150](https://support.dell.com/support/edocs/systems/dim5150/en/index.htm):

> [SIZE="2"]**Addressing Memory With 4-GB Configurations**[/SIZE]
Your computer supports a maximum of 4 GB of memory when you use four 1-GB DIMMs. Current operating systems, such as Microsoft® Windows® XP can only use a maximum of 4 GB of address space; however, the amount of memory available to the operating system is less than 4 GB. Certain components within the computer require address space in the 4-GB range. Any address space reserved for these components cannot be used by computer memory.


This ambiguous wording always made me think they were talking about the software limitations of 32-bit OSes, not some built-in hardware limitation -- especially given that the CPU is 64-bit.  But the more I dig, the more I'm curious about what's going on here.  

I tried flashing to the next available BIOS version from Dell's website, and while the flashing worked, the new BIOS version produces the same problem.  I wondered if it might possibly be the chipset that's at fault, but the [Intel 945G Express](http://www.intel.com/products/desktop/chipsets/945g/945g-overview.htm) chipset that this mobo uses seems to have no 32-bit limit.  Reading about the chipset, it's clear that it has on-board video (integrated Intel Graphics Media Accelerator 950), which is usually what steals away some RAM, but since I've got an ATI Radeon X600 GPU installed anyway, is there any way of disabling this and reclaiming the shared RAM that I don't need for video processing?  No obviously relevant option presents itself in the BIOS.  I thought about replacing the stock Dell BIOS with a FOSS one, but [CoreBoot](http://www.coreboot.org/) (formerly LinuxBIOS) doesn't support my mobo (no big surprise), so that's not an option.  

...

I don't suppose anyone reading this understands better what MTRRs are and what options I might have?  Is this a hardware limitation, or a crappy BIOS implementation?  

Curious,

-- Eiríkr

---

### Post by Eiríkr on 2009-02-07
> **mªrty said:**
> I don't have extensive experience with ubuntu x86_64, but I'm just thinking of other things you could try to see what detects your full 6GB:
[INDENT][LIST]
[*]Memtest86
[*]Livecd (from any other distro)
[/LIST][/INDENT]

Last, and most significant, do you have the latest **BIOS** version?

BIOS fully updated, using the latest version posted on Dell's website.  

Memtest works fine up through the first 4GB, and then slows to a crawl and shows nothing but errors for every memory address higher than 4096.0MB.  I assume this is due to the same MTRR BIOS bug mentioned in [font=courier]dmesg[/font], but please clue me in if my assumption is wrong.  

I haven't tried a non-Ubuntu liveCD yet -- I thought I had one for Fedora 9, but it was just an installer DVD, not bootable itself.  I'll look into that later; I think I have one for Mandriva, I just need to find it.  :)  I'll report back here with any discoveries.  

Cheers,

-- Eiríkr

---

### Post by sanderj on 2009-02-07
First step would be upgrading BIOS, but as you've alrady done that:

I think the interesting, google-able part is "WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 2048MB of RAM."

[http://fixunix.com/kernel/550350-pat-mtrrs.html](http://fixunix.com/kernel/550350-pat-mtrrs.html) gives some interessing information, especially in the last two messages. It involves a lot of /proc/mtrr hacking. I don't have any experience with mtrr, so I will only follow what you will achieve.

When you dive into /proc/mtrr, this might be interesting too: [http://ubuntuforums.org/showthread.php?p=4766662](http://ubuntuforums.org/showthread.php?p=4766662)

---

### Post by Eiríkr on 2009-02-07
> **sanderj said:**
> First step would be upgrading BIOS, but as you've alrady done that:

I think the interesting, google-able part is "WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 2048MB of RAM."

[http://fixunix.com/kernel/550350-pat-mtrrs.html](http://fixunix.com/kernel/550350-pat-mtrrs.html) gives some interessing information, especially in the last two messages. It involves a lot of /proc/mtrr hacking. I don't have any experience with mtrr, so I will only follow what you will achieve.

When you dive into /proc/mtrr, this might be interesting too: [http://ubuntuforums.org/showthread.php?p=4766662](http://ubuntuforums.org/showthread.php?p=4766662)

Excellent leads, sanderj, I'll have to try these out -- though I might not have time until Monday.

Cheers!

-- Eiríkr

---

### Post by sanderj on 2009-02-07
In the meantime you could

```
sudo dmidecode > dmidecode.log
```

and look for the "Memory Controller Information" information.

My laptop says:

```
Memory Controller Information
        Error Detecting Method: None
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 2048 MB
        Maximum Total Memory Size: 4096 MB
```

So, I can't use more than 4GB RAM.

My AMD X2 mobo says:

```
Memory Controller Information
        Error Detecting Method: 64-bit ECC
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 2048 MB
        Maximum Total Memory Size: 8192 MB
```

So, this mobo can't use more than 8GB.

So: check your mobo if it supports more than 4GB at all ...

---

### Post by Eiríkr on 2009-02-07
> **sanderj said:**
> In the meantime you could

```
sudo dmidecode > dmidecode.log
```

and look for the "Memory Controller Information" information.

Interestingly enough, my output has no "Memory Controller Information" section.  The closest I get to a clue is the following section:

```
Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 1 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4
```

Then I get the info for each DIMM stick, accurately showing which sockets have the 2GB modules installed:

```
Handle 0x1100, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_1
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 533 MHz (1.9 ns)
        Manufacturer: 7F7F9E0000000000
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number: CM2X2048-6400C5   

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_3
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 533 MHz (1.9 ns)
        Manufacturer: 7F7F7F0B00000000
        Serial Number: 69062764
        Asset Tag: Not Specified
        Part Number: NT1GT64U8HA0BY-37B

Handle 0x1102, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_2
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 533 MHz (1.9 ns)
        Manufacturer: 7F7F9E0000000000
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number: CM2X2048-6400C5   

Handle 0x1103, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_4
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 533 MHz (1.9 ns)
        Manufacturer: 7FA8000000000000
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number: S1024R3NN2QK-I
```

And here we see that the system does indeed *see* all 6GB that I have installed.  If the sockets were actually limited to only 1GB each, as suggested by the [font=courier]Physical Memory Array[/font] section, I would expect the module sections above to show only 1GB each, and this section below to show only 4GB.  But we see all 6GB...?

```
Handle 0x1301, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0017FFFFFFF
        Range Size: 6 GB
        Physical Array Handle: 0x1000
        Partition Width: 0
```

And here we get the actual memory addresses, again going all the way up to 6GB:

```
Handle 0x1402, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0007FFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x1100
        Memory Array Mapped Address Handle: 0x1301
        Partition Row Position: 1

Handle 0x1403, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00080000000
        Ending Address: 0x000BFFFFFFF
        Range Size: 1 GB
        Physical Device Handle: 0x1101
        Memory Array Mapped Address Handle: 0x1301
        Partition Row Position: 1

Handle 0x1404, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x000C0000000
        Ending Address: 0x0013FFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x1102
        Memory Array Mapped Address Handle: 0x1301
        Partition Row Position: 1

Handle 0x1405, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00140000000
        Ending Address: 0x0017FFFFFFF
        Range Size: 1 GB
        Physical Device Handle: 0x1103
        Memory Array Mapped Address Handle: 0x1301
        Partition Row Position: 1
```

This is the first time I've ever heard of dmidecode, so thanks for the lead.  However, I note the following in the man page (italics mine):

> **DESCRIPTION**
[indent]**dmidecode** is a tool for dumping a computer’s DMI (some say SMBIOS) table contents in a human-readable format. This table contains a description of the system’s hardware components, as well as other useful pieces of information such as serial numbers and BIOS revision. Thanks to this table, you  can retrieve this information without having to probe for the actual hardware.  While this is a good point in terms of report speed and safe&#8208;ness, *this also makes the presented information possibly unreliable*.[/indent]

...

**BUGS**
[indent]More often than not, information contained in the DMI tables is *inaccurate, incomplete or simply wrong*.[/indent]

So now that I've found this information about the purported maximum capacity of each RAM socket on my mobo, how do I evaluate the accuracy of the claimed 1GB limit per socket?  Is this an artificial limitation imposed by the BIOS, or is each socket somehow intrinsically limited to a max of 1GB by the actual hardware?  And if the sockets were indeed so limited, how would the BIOS even be able to see a 2GB RAM module?

Full of questions!  :)  I think I'll still try the MTRR hints you posted earlier -- but not today, no time, I've got a boatload of work to do by Monday AM JST.  :D  Hey, better busy than bored!

Cheers,

-- Eiríkr

---

### Post by dcstar on 2009-02-07
> **Eiríkr said:**
> Hey there folks, I've got a possible stumper for you --

[SIZE="3"]**Hardware:**[/SIZE]

[LIST]
[*]**Dell Dimension 5150**
[*]Intel Pentium D 2.8GHz dual-core
[*]6GB RAM, 2GB each in slots 1 & 3, 1GB each in slots 2 & 4 -- paired up, as required
[/LIST]

.........

According to this the MB only takes 4G maximum:

[http://www.memorystock.com/memory/DellDimension5150.html](http://www.memorystock.com/memory/DellDimension5150.html)

---

### Post by Eiríkr on 2009-02-07
> **dcstar said:**
> According to this the MB only takes 4G maximum:

[http://www.memorystock.com/memory/DellDimension5150.html](http://www.memorystock.com/memory/DellDimension5150.html)

Thanks David, but if you'll read through the rest of the thread, you'll find that this 4GB limit is questionable.  

Cheers,

-- Eiríkr

---

### Post by Gramps on 2009-02-08
Maybe this is the problem:
 ```
Each memory slot can hold DDR2 PC2-5300 with a maximum of 2GB per slot.*

*Not to exceed manufacturer supported memory.
```

From: [http://www.crucial.com/store/listparts.aspx?model=Dimension%205150](http://www.crucial.com/store/listparts.aspx?model=Dimension%205150)

---

### Post by Eiríkr on 2009-02-08
> **Gramps said:**
> Maybe this is the problem:
 ```
Each memory slot can hold DDR2 PC2-5300 with a maximum of 2GB per slot.*

*Not to exceed manufacturer supported memory.
```

From: [http://www.crucial.com/store/listparts.aspx?model=Dimension%205150](http://www.crucial.com/store/listparts.aspx?model=Dimension%205150)

Thanks Gramps.  I'm still left wondering what is meant by "manufacturer supported memory" -- is there some hard limit inherent to the chipset and sockets used on the mobo?  Or does it all come down to assumptions made when programming the BIOS?  

Moreover, the only Dell-authored material I can find about the 5150 only very vaguely* specifies a 4GB limit overall, and 1GB per socket, disagreeing with what Crucial's page says.  Plus there's the simple fact that the BIOS can apparently see all 6GB, but for some reason I cannot access all of it -- making me deeply suspicious that it's some sort of BIOS snafu.  

* (By "very vaguely", refer to my previous post in this thread, wherein I suspect that the 4GB limit actually refers to the limitations of any 32-bit OS.)

Cheers,

-- Eiríkr

---

### Post by dcstar on 2009-02-09
> **Eiríkr said:**
> 
........
Moreover, the only Dell-authored material I can find about the 5150 only very vaguely* specifies a 4GB limit overall, and 1GB per socket, disagreeing with what Crucial's page says.  Plus there's the simple fact that the BIOS can apparently see all 6GB, but for some reason I cannot access all of it -- making me deeply suspicious that it's some sort of BIOS snafu.  
........

It seems as clear as day to me, you can have up to 4GB total whether it be a combination of 2GB (max) sticks or whatever.

Just because the BIOS reports the total capacity of the sticks you have installed does not mean that you get use of all the capacity.

The plain fact that the software cannot see anything over 4GB should remove any doubt whatsoever.

---

### Post by Eiríkr on 2009-02-09
> **dcstar said:**
> It seems as clear as day to me, you can have up to 4GB total whether it be a combination of 2GB (max) sticks or whatever.

Just because the BIOS reports the total capacity of the sticks you have installed does not mean that you get use of all the capacity.

The plain fact that the software cannot see anything over 4GB should remove any doubt whatsoever.

My question, however, is whether this 4GB limit is imposed by the hardware (i.e. something intrinsic to the mobo, where some component limits memory addressing in some way), or by the software (i.e. the BIOS arbitrarily imposing a limit due to various assumptions made by the manufacturer/BIOS programmer).  I have not yet found anything definitive either way.  

If the limit is imposed by the BIOS, then my question becomes whether it is possible to specify any boot options that would work around the BIOS shortcomings.  I have found suggestions (thanks, sanderj) that setting certain MTRR options might do the trick, but I have not yet found time to experiment with them.  

Cheers,

-- Eiríkr

---

### Post by dcstar on 2009-02-10
> **Eiríkr said:**
> My question, however, is whether this 4GB limit is imposed by the hardware (i.e. something intrinsic to the mobo, where some component limits memory addressing in some way), or by the software (i.e. the BIOS arbitrarily imposing a limit due to various assumptions made by the manufacturer/BIOS programmer).  I have not yet found anything definitive either way.  
........

Maximum Address Space is limited by the width of the Address Bus, if the MB is only designed to have 4GB maximum addressable RAM then the bus has the required amount of width for that and no more.

---

### Post by Eiríkr on 2009-02-11
> **dcstar said:**
> Maximum Address Space is limited by the width of the Address Bus, if the MB is only designed to have 4GB maximum addressable RAM then the bus has the required amount of width for that and no more.

Good lead, thank you David!  This is certainly something I can look into.  Cheers!

-- Eiríkr

---

### Post by novafluxx on 2009-02-11
Don't know if this has been mentioned yet, but check the owners manual for the Dimension 5150 on support.dell.com. Check the specs to see if the max RAM for the system is 4GB.

Let me check actually...brb...checking...almost there...5150 or 5150c...lets go with 5150...

[http://support.dell.com/support/edocs/systems/dim5150/en/om/WD846A02.pdf](http://support.dell.com/support/edocs/systems/dim5150/en/om/WD846A02.pdf)

Max memory is 4GB...so its probably the motherboard limitation.

For shoots and grins I'll check the 5150c and E510 too...

5150c manual states 4GB max: [http://support.dell.com/support/edocs/systems/dim5150C/en/om/WD300A03.pdf](http://support.dell.com/support/edocs/systems/dim5150C/en/om/WD300A03.pdf)

XPS 200 is: [http://support.dell.com/support/edocs/systems/xps200/om/TD649A03.pdf](http://support.dell.com/support/edocs/systems/xps200/om/TD649A03.pdf)

4GB Maximum on EACH of those

The post by dcstar about it being a motherboard limitation is correct.

---

### Post by Eiríkr on 2009-02-11
> **novafluxx said:**
> Don't know if this has been mentioned yet, but check the owners manual for the Dimension 5150 on support.dell.com. Check the specs to see if the max RAM for the system is 4GB.

Let me check actually...brb...checking...almost there...5150 or 5150c...lets go with 5150...

[http://support.dell.com/support/edocs/systems/dim5150/en/om/WD846A02.pdf](http://support.dell.com/support/edocs/systems/dim5150/en/om/WD846A02.pdf)

Max memory is 4GB...so its probably the motherboard limitation.

For shoots and grins I'll check the 5150c and E510 too...

5150c manual states 4GB max: [http://support.dell.com/support/edocs/systems/dim5150C/en/om/WD300A03.pdf](http://support.dell.com/support/edocs/systems/dim5150C/en/om/WD300A03.pdf)

XPS 200 is: [http://support.dell.com/support/edocs/systems/xps200/om/TD649A03.pdf](http://support.dell.com/support/edocs/systems/xps200/om/TD649A03.pdf)

4GB Maximum on EACH of those

The post by dcstar about it being a motherboard limitation is correct.

Cheers, novafluxx.  It sure sounds like it -- though I admittedly feel a chump since now I've got 6GB RAM and no way of using it all.  :-\  

I'd read the Dell manual before, but as I'd noted earlier in the thread, the wording was a bit ambiguous as to whether the 4GB limitation was hardware, or if it was simply a roundabout way of saying that Windows XP wouldn't be able to use more than 4GB.  

After digging around and finding out that this mobo apparently uses Intel's 945G Express chipset, I went looking on Intel's site for details.  It sounds like Intel rather strangely designed the chipset to support 64-bit CPUs, but to only use 32-bit memory addressing -- which is either shockingly stupid, or simply cutting corners by using up older obsoleted inventory.  Here's the [PDF](http://download.intel.com/design/intarch/manuals/30882301.pdf) I found.  

Somewhat confusingly, though, page 15 includes the following:
> With appropriate 64-bit supporting hardware and software, platforms based on an Intel processor supporting EM64T can use extended virtual and physical memory.
I'm not entirely sure what that's supposed to mean in the context of this particular chipset; maybe it's just techno-babble market-droid-ese.  

Cheers,

--Eiríkr

---

### Post by novafluxx on 2009-02-11
Try everything you can! No guarantees that it'll work though :(

---

### Post by Vico Vicario on 2009-02-12
I went through a similar problem with a laptop. I installed 4GB, the BIOS recognized 4GB, but 64-bit linux told me I had 3.4GB. After much reading I discovered that due to Windows memory limitations, the hardware manufacturers (HP) had started crippling the physical memory and using it for other purposes, i.e. video and PCI-express. It is not physically available to the OS. Since Windows couldn't use it, then it was not needed right? So unfortunately in my case it is a hardware limit. Apparently you hit the same limit.

V.

---

### Post by ben2talk on 2009-03-03
> **Vico Vicario said:**
> I went through a similar problem with a laptop. I installed 4GB, the BIOS recognized 4GB, but 64-bit linux told me I had 3.4GB. After much reading I discovered that due to Windows memory limitations, the hardware manufacturers (HP) had started crippling the physical memory and using it for other purposes, i.e. video and PCI-express. It is not physically available to the OS. Since Windows couldn't use it, then it was not needed right? So unfortunately in my case it is a hardware limit. Apparently you hit the same limit.

V.

**** - I just thought I'd get amd64 Ubuntu, and had 512+512+1024+1024 - so I ran out and swapped a 512 for a 2048MB

massive boost from 3GB to 3.4GB

Bad BAD HP

It stinks - as you look around their site, it's all about upgrading to XP or Upgrade from XP to Vista.

They aren't Hardware manufacturers, they're Microsoft Support manufacturers by the looks of it - why did I pay for a 64 bit processor to find it's crippled? Not much I can do about it now though I guess...

---

### Post by fjgaude on 2009-03-03
Could your issue be that using 2GB chips is not understood by the motherboard, or the mixed sizes of 1GB and 2GB. Don't they say 4GB using 1GB chips?

---

### Post by mªrty on 2009-03-11
I just wanted to add that I'm having the same issue with a BIOSTAR k8m800 micro AM2 motherboard, 4GB of OCZ ram, and an Athlon 64 X2 processor running Ubuntu 8.10 (latest bios and ubuntu updates)

Only sees 3.4GB.

---

### Post by satendra on 2009-04-01
Friends,
I brought a new HP dual core E2200 Intel CPU desktop with 6 GB of RAM. I installed 64 bit Ubuntu Desktop. The memory shown is only 3.2 GB while my BIOS shows all 6 GB of RAM. Here is what dmesg show


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-server (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 01:36:05 UTC 2009 (Ubuntu 2.6.24-23.48-server)
[    0.000000] Command line: root=UUID=ce931921-ebf3-491a-9050-ce37f53369ae ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf590000 (usable)
[    0.000000]  BIOS-e820: 00000000cf590000 - 00000000cf5e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf5e3000 - 00000000cf5f0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf5f0000 - 00000000cf600000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 849296) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F80B0 checksum 0
[    0.000000] ACPI: RSDP 000F80B0, 0014 (r0 HPQOEM)
[    0.000000] ACPI: RSDT CF5E3000, 0038 (r1 HPQOEM SLIC-BPC 42302E31 AWRD        0)
[    0.000000] ACPI: FACP CF5E3080, 0074 (r1 HPQOEM SLIC-BPC 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT CF5E3100, 4A8B (r1 HPQOEM AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CF590000, 0040
[    0.000000] ACPI: HPET CF5E7C80, 0038 (r1 HPQOEM SLIC-BPC 42302E31 AWRD  


I upgraded to server kernel too but without any improvement. Here is out of free-m and  uname -a

root@sks:~# free -m
             total       used       free     shared    buffers     cached
Mem:          3266        961       2304          0         26        407
-/+ buffers/cache:        527       2738
Swap:         9538          0       9538
root@sks:~# uname -a
Linux sks 2.6.24-23-server #1 SMP Mon Jan 26 01:36:05 UTC 2009 x86_64 GNU/Linux

My problem is same as mentioned above. Any Help please

---

### Post by alienfluid on 2009-04-28
Eirikr,

I've got the exact same system and am having issues even getting 4GB to be reported correctly. Did you ever get the system to at least report all of 4GB properly (i.e. the manufacturer's maximum?).

Thanks.

---

