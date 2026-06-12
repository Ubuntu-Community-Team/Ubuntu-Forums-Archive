---
title: "Does 64bit Ubuntu Handle 4GB RAM?"
date: 2006-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-11-06
This is a continuation of the thread Memory Upgrade Results in Kernel Panic

Initially I had a kernel panic using 4 1GB sticks of RAM. Once I resolved the problem of the kernel panic, I noticed that the system monitor in Ubuntu reports 2.7GB of memory rather than the 4GB.

The total memory is 4GB. 1 GB sticks X 4. 2 Kingston & 2 PNY.

The BIOS reports that I have 4GB installed and usable. I can't possibly be losing all of that memory, can I? If that's true, I might as well remove the extra 2 GB! 3 sticks give me 2.7 GB in Ubuntu too. Where's the rest of the memory?
When I was running at 2GB, Ubuntu saw all of the memory. Once I stepped up to 3GB, I saw a drop in speed and memory listed in Ubuntu. The funny thing is that at 3GB (3 sticks) the bios doesn't see all 3 GB. It sees 3GB less 256 MB and Ubuntu sees 2.7 GB. When I bump up to 4GB, assuming that somehow I'm going to lose 256MB when I go over 2GB ram, the BIOS sees all 4GB of RAM but Ubuntu is still stuck at 2.7GB. I don't get it.

If I'm really stuck at 2.7GB, It doesn't pay to upgrade the RAM over 2GB. Even with 64bit Ubuntu. I'll just pull out the 2 extra sticks. Are there know issues with 64bit Ubuntu with over 4GB RAM?

Thanks.

---

### Post by babooka on 2006-11-06
I do not know how about X64, but generic kernel supports only < 4 gb. You will have to recompile the kernel and select a HIGH ram support.

---

### Post by Case_f on 2006-11-06
I think the question is, does your board support the memory configuration you're using? Some boards have limitations as to how you can combine memory modules in them.

---

### Post by bper on 2006-11-06
Thanks for your responses.

Case_f, if there is an issue with the combination would it only show with 4GB or more? If I use 1 of each module, the system works flawlessly. If I use 2 Kingstons & 1 PNY the system works, but at reduced speed and minus 256 MB. When I use 4GB, as far as Ubuntu is concerned, it seems to behave like I'm using 3GB.

babooka, I would have thought that x64 would've supported high memory by default. Do you know if the behavior is different with Edgy? (later kernel) I'm currently using Dapper, but I plan to upgrade. No sense recompiling the kernel for my Dapper if my Edgy would resolve it. If it won't, I might as well upgrade first then recompile since I will run into this problem again.

---

### Post by Case_f on 2006-11-06
> **bper said:**
> Case_f, if there is an issue with the combination would it only show with 4GB or more? If I use 1 of each module, the system works flawlessly. If I use 2 Kingstons & 1 PNY the system works, but at reduced speed and minus 256 MB. When I use 4GB, as far as Ubuntu is concerned, it seems to behave like I'm using 3GB.


Memory module combinations are pain in the *** sometimes, and to top that, many newer boards can be quite picky as to what works and what does not. I'd say this is definitely HW issue. There could be pairing problems for dual mode and quite a few other possibilities, which are hard to diagnose this way. Try different modules, if you can (another two Kingstons like you already have would probably be best). Also, the manual states that 'DIMM modules with 128Mb memory chips or double sided x16 memory chips are nor supported in this motherboard' - I'm somewhat fuzzy on DIMM architectures, but I think there could very well be your answer - 'not supported' may not explicitly mean 'do not work at all' - it can sometimes mean that it somehow works, but acts 'funny' - like in your case.

---

### Post by RAOF on 2006-11-06
Just for the record, the x86-64 kernel should support the full 64GB (or whatever it is) of RAM that x86-64 supports natively.

Another thing to check might be where various things are being mapped into your address space.  From what you describe about your 3GB experiences, it sounds like there's some device, probably the graphics card, getting mapped into the address space there.  It's possible that the kernel hits this space and assumes there's no more RAM above it.

I'd check with your motherboard manual/documentation/google to see what you need to do to have access to all 4GB of memory.

---

### Post by bper on 2006-11-07
Thanks for your response, RAOF. I've been checking Mobo & Bios settings from the start, but I'll continue to look into it.

Pardon the simple question, but is it possible that the system monitor is not reporting accurately? Is there another way to check the allocated and in-use memory?

---

### Post by RAOF on 2006-11-07
> **bper said:**
> ...
Pardon the simple question, but is it possible that the system monitor is not reporting accurately? Is there another way to check the allocated and in-use memory?

Unlikely.  You could also check around the /proc directory - the stuff in there is what the kernel thinks of your hardware :)

---

### Post by joshuapurcell on 2006-12-20
I'm having this same issue. I'm not using Edgy 64-bit though... I'm using Edgy 32-bit. I originally had 2GB of RAM, and then I decided to buy two additional (and identical to the original two) RAM sticks to make a total of 4GB. Inside the BIOS it gives me 4GB, and the very first thing I did after unwrapping the memory was run Memtest for 3 hours to make sure everything was stable. Once I was satisfied there (since there were no errors) I booted into Edgy and didn't notice that the OS only saw 3.2GB until just now. That's a huge difference.

I'm going to boot into Windows and see what it says there... haven't done that yet.

---

### Post by Azakus on 2006-12-20
A 32-bit processor can't address more than 4Gb of RAM directly.

---

### Post by joshuapurcell on 2006-12-20
> **Azakus said:**
> A 32-bit processor can't address more than 4Gb of RAM directly.I'm aware of this. I'm using a 64-bit processor. Here are my specs (copied from my sig on another forum):
Ubuntu Edgy 32-bit on DFI LanParty UT nF590 SLI-M2R/G
CPU:AMD Athlon64 X2 5200+ Windsor 2612MHz
Cooler:Zalman CNPS9500 AM2
RAM:4x 1GB OCZ Gold PC2 8000
Video:1x eVGA 8800GTS 500MHz 640MB
Display:Acer AL2423Wdr 24" Widescreen
Sound:Chaintech AV-710
Disk:2x Seagate Barracuda 7200.10 320GB SATA 3Gb/s
PSU:Antec True Power Trio 650W
Case:Antec P180

I've made some notes on what different OSes see as far as memory goes on my system. I should say the BIOS always says 4193216K unless I disable 'Memory Hole Remapping' (which it then reports 3327MB some reason). The following numbers are all taken from within the OS while the BIOS says 4GB:
**Edgy 64-bit**: 4047512K
**Edgy 32-bit**: 3369216K
**WinXP 32-bit**: 3406252K

Edgy64 shows the most memory at around 3.8GB (still not the full 4GB for some reason), but Edgy32 doesn't even see as much as WinXP! I didn't have WinXP 64-bit to test... I may find that soon and try it out. I also want to see what other Linux distributions with different kernels detect at some point.

---

### Post by RAOF on 2006-12-20
I **think** that in order to be able to address the full 4GB of ram, the kernel needs to be built with PAE support - the server kernels almost certainly are, so maybe you should try one of those.

Your "Memory Hole Remapping" thing is probably the reason that the 32bit kernels aren't able to address the full 4GB of memory.  While you have a 4GB address space with 32bits, quite a lot of that address space is taken up by memory-mapped devices (like the AGP/PCI-E stuff, this, that, and the other).  I'm *pretty sure* that's what the "memory hole" thing is.  So, the upshot is that your processor can address 4GB of ram.  But some of that ram is masked by the memory-mapped devices, leaving you with... 3.2GBish.

---

### Post by manngar on 2006-12-20
I'm running x86_64 version of Edgy (6.10) and couldn't get the generic 2.6.17 kernel to work with 4Gb installed. I pulled two sticks out (leaving 2Gb) and everything is now stable. Previously I was getting random lockups.

I've just built and installed 2.6.19.1, and noticed that there is no HIGHMEM option in the Processor configuration group. Is this because I'm on x86_64, or is it because 2.6.19 no longer has it? Incidentally, the box feels much quicker after installing the 2.6.19 I built myself (optimised for AMD x2).

Gary

---

### Post by enopepsoo on 2006-12-21
I have been wanting to go up to 4gb for a few months now.  

Note to anyone using Windows with => 2gb ram that you should look into changing your boot.ini file to take advantage (on 32 bit).  I have seen this cause problems at work.

---

### Post by derGhostrider on 2006-12-22
Hi!

1. I am using 64bit Kubuntu 6.10 with a dual-Opteron and 4GB of memory. I can see the full 4GB of my memory. :D 
2. A 32bit OS can access up to 4GB of memory directly BUT: PCI-Option ROMs reserve some space at the upper end of the 4GB boundary. So you will never be able to use the full 4GB with a 32bit OS except that there is some strange remapping that has to be supported by the BIOS and the OS.
Windows Server 2003 Enterprise Edition can do it. (I have it as well and tested it) Windows XP (32bit) can't do these tricks. If I check my memory with XP it tells me that there are just 3.2 or 3.0GB memory installed. That's pretty normal and nothing to worry about.

If you need an OS that offer access to the full 4GB I'd recommend to use 6.10 Edgy (64bit) or, if Windows is an alternative for you, XP x64 (if you don't have driver issues) or Win2003 R2 EE.

The effect is NOT caused by incompatible memory modules. It's a hardware design issue of the 32bit x86 platform.

---

### Post by mattyj on 2006-12-24
Yep,

I have dual opterons and 4GB of RAM on 64 bit Dapper 6.06 and it works great.

---

### Post by RAOF on 2006-12-24
> **derGhostrider said:**
> ...
The effect is NOT caused by incompatible memory modules. It's a hardware design issue of the 32bit x86 platform.

Which Intel worked around with the PAE extension, allowing the 32bit processor to access 64GB (IIRC) of memory, at the cost of slightly slower memory access.  The -server kernels would have this enabled.

There would be no HIGHMEM option for x86-64 kernels - no extra doodads are required to access the full 48bit addresses the bus supports.

---

### Post by thoughts on 2006-12-27
Hello,

I have an Intel Core 2 Duo system with 2GB of RAM, and Ubuntu recognizes it properly: "free -m" shows 2001 MB.  But I just bought 2 more GB and installed them; now the BIOS reports 4GB, but "free -m" only reports 3281 MB instead of ~4000 MB.  (All 4 RAM sticks are identical.)

Looking at the output of the "dmesg" command, I have:

```
Warning only 4GB will be used.
Use a PAE enabled kernel.
3200MB HIGHMEM available.
896MB LOWMEM available.
```

So apparently I do have PAE enabled.  Is there something else I can do to make my system recognize all 4 GB, other than switching to a 64bit kernel?  I'm running the stock 32bit desktop kernel; if I decide to upgrade to 64bit, do I need to do a complete reinstall of Ubuntu, or is it just a kernel change?

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

