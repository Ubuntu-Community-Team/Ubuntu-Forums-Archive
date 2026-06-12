---
title: "Ubuntu x64 does not see all my ram"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by jrharvey on 2008-05-23
Specs:
Intel core2 Quad 2.4 GO 
Intel motherboard(not sure which one right not)
4G ddr2 PC2 5300 Ram
Nvidia 8600gt
Ubuntu 8.04 x64

So the problem is that it only sees 3.8G
Is this normal? This is my first machine to really take full advantage of 64 bit and i wanna make sure its ready to go.

And it is weird that the Kernal does not say x64 like gutsy did. I know its x64 because when i try to install 32 bit apps it tells me that its the wrong architecture. Do i have to load a special kernal or something?

---

### Post by Vadi on 2008-05-23
I think it's some weird rounding or something else that contributes. I got 4 gigs too but it says 3.9 in the system monitor for me.

---

### Post by Yellow Pasque on 2008-05-23
Try some commands for us, please:
```
free -m
uname -a
```

---

### Post by friendofpugs on 2008-05-23
Your lower figure is perfectly acceptable. When I ran 4G on a 32 bit, I only saw 3.1G available; when I switched to x64, I see 3.8G. I agree, I thinks it's some rounding nonsense or other.

---

### Post by Joeb454 on 2008-05-23
I think I read somewhere that your graphics card has to be mapped to the RAM (not sure if this is true for 64 bit systems however).

So it could be this :)

---

### Post by jrharvey on 2008-05-23
> **Temüjin said:**
> Try some commands for us, please:
```
free -m
uname -a
```

```
jrharvey@jrharvey-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3891        650       3241          0         13        291
-/+ buffers/cache:        345       3546
Swap:         8001          0       8001
jrharvey@jrharvey-desktop:~$ uname -a
Linux jrharvey-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
jrharvey@jrharvey-desktop:~$ 
```

---

### Post by dcstar on 2008-05-24
> **friendofpugs said:**
> Your lower figure is perfectly acceptable. When I ran 4G on a 32 bit, I only saw 3.1G available; when I switched to x64, I see 3.8G. I agree, I thinks it's some rounding nonsense or other.

Do some research into the definitions of GiB and GB and it will be explained.

---

### Post by felker2 on 2008-05-24
3.8 GiB? Lucky you: my system monitor only sees 3.7 GiB on my 64-bit 4GB system. See attachment.


BTW: you can check the 'usable' parts of your RAM yourself:

```

sander@ubuntu804:~$ dmesg | grep e820 | grep -i usable
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7ee0000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
sander@ubuntu804:~$

```

---

### Post by cdtech on 2008-05-24
The kernel needs to load, and that takes a fairly small but fixed amount  of memory and is determined by the compilation of the kernel. After that all the memory left over is available.

---

### Post by jespdj on 2008-05-24
3.8 GB sounds normal. Some memory is most likely reserved for devices such as your graphics card and I/O devices.

You could have a look in the BIOS settings of your computer. Especially look for a setting called "Memory Remapping" or something similar, and make sure it is enabled.

On my computer, I get this:
```
jesper@jesper-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3961        924       3037          0         17        387
-/+ buffers/cache:        519       3442
Swap:         8205          0       8205

jesper@jesper-laptop:~$ dmesg | grep e820 | grep -i usable
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe72000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)

```

---

### Post by jrharvey on 2008-05-27
> **cdtech said:**
> The kernel needs to load, and that takes a fairly small but fixed amount  of memory and is determined by the compilation of the kernel. After that all the memory left over is available.

Well the reason i asked was because on my 3 gig system, Ubuntu saw all 3 gigs of ram. I didnt think it would be different with more.

---

### Post by Yellow Pasque on 2008-05-28
> The kernel needs to load, and that takes a fairly small but fixed amount of memory and is determined by the compilation of the kernel. After that all the memory left over is available.
That's not true. See [http://ubuntuforums.org/showthread.php?t=783707](http://ubuntuforums.org/showthread.php?t=783707) for more info.

---

### Post by Eniak on 2008-05-29
I'd b happy if it was telling me i have 3.8 or 3.7

I also got 4gb of ram... in ubuntu 32 it was sayin I had 3.1
now I got ubuntu 64 and it says I have 2.9gb :/

Can it b the fact that I didn't install d video driver in 64 bits yet?

---

### Post by Kevbert on 2008-05-29
Interesting.  If I enter free mem I get 4052140 bytes.  If I enter free -m I get 3957Mb which is approx 4052140/1024.  Using an AMD2 x64 and Gutsy x64.
If you get a lot less than this you need to set something for memory in the bios (I think its a memory hole patch or something like that).

---

### Post by Eniak on 2008-05-29
the problem is I'm having this problem on a macbook pro, have no idea of how to access such functions on it.... damn....how I miss my PC....

---

### Post by Kevbert on 2008-05-29
Hi.  Apparently Macs don't have bios they have EFI (?) instead.  It looks like it's possible to update the firmware, that may be your best bet as you may not have direct access to patching the memory hole.  If you google macbook+EFI you may find a firmware solution.

---

### Post by Skeorx13 on 2008-05-29
I'm running Hardy 64bit on a Pentium D (830), 4GB (4x1GB) DDR2, 7600GT XXX, and an intel D945pvslkr mobo. For some reason it only lists my RAM at 3.2GB. I updated the bios and couldn't find a remap option at all, before or after updating it. Is there a way to remap the memory through the OS at all?

---

### Post by Kevbert on 2008-05-29
> **Skeorx13 said:**
> I'm running Hardy 64bit on a Pentium D (830), 4GB (4x1GB) DDR2, 7600GT XXX, and an intel D945pvslkr mobo. For some reason it only lists my RAM at 3.2GB. I updated the bios and couldn't find a remap option at all, before or after updating it. Is there a way to remap the memory through the OS at all?

I've had a look at the bios data on the Intel website.  You've certainly got a load of configurable options, but nothing about plugging the memory hole.
One thing I did notice is that some of the memory is shared and so it doesn't look as if you can use all of it for the OS.  It looks like 3.2Gb is all your going to get.  Sorry.

---

### Post by Novega on 2008-05-29
> **dcstar said:**
> Do some research into the definitions of GiB and GB and it will be explained.

From [http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)
> a gigabyte is just over 93% as much as a gibibyte
Doing the rough calculation 4096 (4GB of RAM) X .93 = 3809.28 GiB

So there's nothing wrong...unless my math is bad :p

---

### Post by Eniak on 2008-05-30
> **Kevbert said:**
> Hi.  Apparently Macs don't have bios they have EFI (?) instead.  It looks like it's possible to update the firmware, that may be your best bet as you may not have direct access to patching the memory hole.  If you google macbook+EFI you may find a firmware solution.

Hey, first thanx for the attention and support...

Ya I thought about EFI as well, but Im 99% sure I have the last update and other thing, correct me if Im wrong, If it was an EFI firmware problem I would have problems to read the whole 4gb at OS X as well no? Leopard is reading them flawlessly. Im gonna install vista64 tonight to see what it says as well... Which is the most odd part for me is, Ubuntu 32 is reading more ram then the 64 or Server

Ubuntu 32 desktop: 3.0
Ubuntu 32 server: 2.9
Ubuntu 64 desktop: 2.9

Oh...wait Im re-reading what u wrote, by "updating efi firmware" u mean installing a new version or updating it in the sense of telling it I added more ram?

Thanx for the attention and support again :)

---

### Post by Kevbert on 2008-05-30
> **Eniak said:**
> Hey, first thanx for the attention and support...

Ya I thought about EFI as well, but Im 99% sure I have the last update and other thing, correct me if Im wrong, If it was an EFI firmware problem I would have problems to read the whole 4gb at OS X as well no? Leopard is reading them flawlessly. Im gonna install vista64 tonight to see what it says as well... Which is the most odd part for me is, Ubuntu 32 is reading more ram then the 64 or Server

Ubuntu 32 desktop: 3.0
Ubuntu 32 server: 2.9
Ubuntu 64 desktop: 2.9

Oh...wait Im re-reading what u wrote, by "updating efi firmware" u mean installing a new version or updating it in the sense of telling it I added more ram?

Thanx for the attention and support again :)

If Leopard is seeing 4Gb then it can't be an EFI problem.  Ubuntu 32 won't see much more than 3Gb.  Ubuntu 64 will see nearly 4 Gb on an AMD 64 bit PC, maybe it has a problem with Intel processors and Macbook.  I couldn't see anything on Launchpad.  It may be worth raising a bug report to make others aware of this: [https://bugs.launchpad.net/]("https://bugs.launchpad.net/")

---

### Post by Eniak on 2008-05-30
> **Kevbert said:**
> If Leopard is seeing 4Gb then it can't be an EFI problem.  Ubuntu 32 won't see much more than 3Gb.  Ubuntu 64 will see nearly 4 Gb on an AMD 64 bit PC, maybe it has a problem with Intel processors and Macbook.  I couldn't see anything on Launchpad.  It may be worth raising a bug report to make others aware of this: [https://bugs.launchpad.net/]("https://bugs.launchpad.net/")

K... I've been doing some research and found some usefull info and how stupid I am :lolflag:

My mbp is an intel core 2 duo 2,33... which can't adress more then 3gb of ram... ](*,)

It's yet odd, cuz when I go to system monitor or about on leopard it says I have 4gb of ram... well, I think it can see it but not address it... So I researched more, and it confirmed, my kind of processor can see 4gb of ram but can address up to 3... it says if u put 4gb in those kinds of mac the 1 extra gb will b overlaping some system critical functions :confused:

I have no idea of what this overlapping stuff means, not even if its good or bad ehehehe... :/
So is it good or bad? Something tells me it's really bad... But I'm too noob to know that... I'm just waiting/lookin for a confirmation to replace one of the 2gb sticks with the old 1gb one and put it on ebay

I also heard from a friend that is better having 2gb then 3gb in the machine :confused::confused::confused:
is it true???

---

### Post by Kevbert on 2008-05-30
I'm not so sure thats a good idea as memory should normally be installed in pairs.  Doesn't it say anything in the manual ?  
I've just found this: [http://www.dansdata.com/askdan00015.htm]("http://www.dansdata.com/askdan00015.htm")
which tells us that other system devices are likely to use memory addresses above the 3Gb limit.  So the answer to your question is maybe as there could be memory address conflicts.  As the usual mantra goes, try it and see.

---

### Post by Eniak on 2008-05-30
> **Kevbert said:**
> I'm not so sure thats a good idea as memory should normally be installed in pairs.  Doesn't it say anything in the manual ?  
I've just found this: [http://www.dansdata.com/askdan00015.htm]("http://www.dansdata.com/askdan00015.htm")
which tells us that other system devices are likely to use memory addresses above the 3Gb limit.  So the answer to your question is maybe as there could be memory address conflicts.  As the usual mantra goes, try it and see.

I'm digging my stuff here lookin for the damn manual... even though mac manuals just come with an apple and that think different annoying phrase :lolflag: 
Anyway... this site u indicated is very interesting, thank you very much for the reading suggestion... I didn't finish reading the whole article yet but from until what I red I already found it very useful... I'm researching also about the difference of motherboards of my mbp model and of the mbps that came after, cuz just after 1 generation from mine, 4gb ram support has been enabled :/

I asked to a friend to bring his vista64 dvd, I want to test it anyway... The idea of a motherboard and a processor that can read physically 4gb of ram but can't address it yet sounds too odd for me

Again my friend, thank you very much for the help :)

---

### Post by StephenDeli22 on 2008-05-30
> **Skeorx13 said:**
> I'm running Hardy 64bit on a Pentium D (830), 4GB (4x1GB) DDR2, 7600GT XXX, and an intel D945pvslkr mobo. For some reason it only lists my RAM at 3.2GB. I updated the bios and couldn't find a remap option at all, before or after updating it. Is there a way to remap the memory through the OS at all?

I had an interesting thing with my laptop some of you may be noticing.  My intel 945 chipset can see 4gb in my BIOS, however, the mobo can only map/address 3gb of it to my OS. This seems to be an issue that the computer was purchased as a 32bit windows machine (with a 64bit enabled processor) that was probably never intended for a 64bit OS that could utilize more ram.  If you have the 945 chipset, I hate to break it to you, but your OS will not see all of its ram.

It seems to be a 32 bit "cut corner."

---

### Post by gameryoshi600 on 2008-05-31
its your graphics using some ram or its just that no hardware is exact. my 2 gig comes out as 1.9 GB round it and its 2 gigs

---

### Post by Yellow Pasque on 2008-05-31
> **gameryoshi600 said:**
> its your graphics using some ram or its just that no hardware is exact. my 2 gig comes out as 1.9 GB round it and its 2 gigs
Unless it's integrated or a low-end video card with nVidia "TurboCache" or ATI "HyperMemory", the graphics card does not reserve system memory. The BIOS may reserve certain portions of it though.

Again, see: [http://ubuntuforums.org/showthread.php?t=783707](http://ubuntuforums.org/showthread.php?t=783707)

---

