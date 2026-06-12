---
title: "Only 3.1 Gigs of ram"
date: 2009-02-20
forum: x86 64-bit Users
---

### Post by shade11 on 2009-02-20
I recently upgraded my processor to a Core 2 Duo from a Pentium 4 (550) on my new motherboard. To take full advantage of my 4 gigs of ram I reinstalled Ubuntu using the 64-bit version. Everything seemed to go by smoothly.

When I opened System Monitor I noticed that it does not show my 4 full gigs of ram. An approximate 3.1 gigs are shown.

The ram sticks are not bad, Windows recognizes all of my ram. I am not using an integrated graphics card at all.

The only thing that might be a culprit is the fact that when I reinstalled, I had a separate large partition allocated for /home which was used in my previous installation.

Any help would be appreciated.

---

### Post by knight187 on 2009-02-20
I had the same thing, not sure how but its your video card, if your new mobo has another pci-x slot in it move your card to that one.

my mobo has 3 x pci-x and with my vid card in the wrong slot I only have 3gig of mem show up out of my 4gig

Cheers.

---

### Post by Kevbert on 2009-02-20
What version of Ubuntu are you using ? You can get this via
```
uname -a
``` 
in terminal. Is your version of Windows 64 bit ? If not, it may see 4Gb, but will probably only use 3.2Gb.
You need to use the 64 bit version or 32 bit server version of Ubuntu to see your 4Gb. With
```
free -m
```
it will see just over 3.95Gb of RAM

---

### Post by shade11 on 2009-02-20
> **knight187 said:**
> I had the same thing, not sure how but its your video card, if your new mobo has another pci-x slot in it move your card to that one.

my mobo has 3 x pci-x and with my vid card in the wrong slot I only have 3gig of mem show up out of my 4gig

Cheers.

I only have one PCI-E 16x 2.0 slot which is used for my graphics card, there is no other place to stick it in.

> **Kevbert said:**
> What version of Ubuntu are you using ? You can get this via
```
uname -a
``` 
in terminal. Is your version of Windows 64 bit ? If not, it may see 4Gb, but will probably only use 3.2Gb.
You need to use the 64 bit version or 32 bit server version of Ubuntu to see your 4Gb. With
```
free -m
```
it will see just over 3.95Gb of RAM

uname -a returns this

```
Linux Stageira 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```

free -m returns this

```
             total       used       free     shared    buffers     cached
Mem:          3204       1080       2123          0         17        399
-/+ buffers/cache:        664       2539
Swap:         2800          0       2800

```

I am currently using the Windows 7 Beta, x86-64 version. It detects and uses all of my ram. Ubuntu x86-64 does not.

---

### Post by lensman3 on 2009-02-20
Do a "dmesg | more" just after you boot up.  What does the kernel report during boot?  There might be more info there.

Go snoop around in /proc.  Three are a lot of files that have to do with memory mapping into devices.  There might be a hint there.

---

### Post by sanderj on 2009-02-21
> **shade11 said:**
> Windows recognizes all of my ram.

Even a 32-bit Windows will report "4GB RAM". That doesn't say it can use it.

Anyway: post the output of "dmesg | head -25" here.

And post the output "dmesg | grep e820" here. Here's mine:

```
sander@ubuntu810-on-athlon64:~$ dmesg | grep e820
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
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
sander@ubuntu810-on-athlon64:~$ 
```

The important part is the "0000000100000000 - 0000000120000000 (usable)": that's the above the 3.2/4GB barrier. If you haven't got that line, upgrade your BIOS to the newest version and look in your BIOS for an option "memory (hole) remapping" or "memory hoisting": that should be on.
If that doesn't work, search your mobo/laptop supplier's site for the maximum amount of RAM your mobo/laptop can handle.

HTH

---

### Post by Kevbert on 2009-02-21
Regarding the bios setting, it's probably unlikely that this needs to be made if you see 4Gb in Windows 64 bit (but is still worth checking). It may be marked as memory hole remapping or something similar.
It may also be worth running memtest to make sure the memory is fine (as older versions of Windows may work but occasionally crash for no apparent reason).
3.2Mb is a historic limit for memory as no-one envisaged that more than this would ever be used. Above this the memory addresses were allocated to other peripherals. Does the display card use shared memory ? (even though free -m suggests otherwise).

---

### Post by shade11 on 2009-02-21
I would like to clarify that both of my operating systems were 64-bit. The computer I am using is fairly new, I only had a Pentium 4 in it due to the fact that I couldn't afford a new core at the time. My video card does not use any of my ram. My board supports up to 8 gigs of DDR2 or DDR3.

I failed memtest86. Individually tested both of my sticks to find out that one of them has a fault. But I am not entirely sure about whether its faulty or not. Memtest detected around 1400 megs of bad ram on both sticks. However, when individually testing, one stick was clean while the other had around 700 megs of bad memory. When using 32-bit Ubuntu on my old Pentium 4 (same everything else), I detected around 3.4 gigs of ram. 32-bit windows 7 detected 4 gigs but only used 3.4. The 64-bit version of windows 7 I am using detects and uses all 4 gigs.

---

### Post by Kevbert on 2009-02-21
If memtest reports failures it suggests you have definitely have a memory problem. Does the memory fail on the first pass or later ? It may just be that the memory chips aren't properly seated in their sockets. Remove and refit the memory (taking antistatic precautions). If this resolves the problem after one pass, let memtest run a few more times as it may be a thermal problem.

---

### Post by shade11 on 2009-02-21
> **Kevbert said:**
> If memtest reports failures it suggests you have definitely have a memory problem. Does the memory fail on the first pass or later ? It may just be that the memory chips aren't properly seated in their sockets. Remove and refit the memory (taking antistatic precautions). If this resolves the problem after one pass, let memtest run a few more times as it may be a thermal problem.

Only one stick fails within the first test. Both sticks are properly seated, I checked and double checked. 3.1 gigs would suggest that they are properly seated since they are both 2 gig sticks.

I might just have to call Gskill and RMA these sticks.

---

### Post by Kevbert on 2009-02-21
If you know which stick fails, try it in the other socket and see if it passes, then it's the socket that's the problem (I hope not!)

---

### Post by shade11 on 2009-02-21
> **Kevbert said:**
> If you know which stick fails, try it in the other socket and see if it passes, then it's the socket that's the problem (I hope not!)

I did this earlier. I tested both sticks in the same slot. Only one stick failed. It fails in both slots.

---

### Post by Kevbert on 2009-02-22
> **shade11 said:**
> I did this earlier. I tested both sticks in the same slot. Only one stick failed. It fails in both slots.

Good, you need a new memory stick.

---

### Post by dcstar on 2009-02-23
> **Kevbert said:**
> Good, you need a new memory stick.

Only if you want it to function in a non-Windows environment... apparently....

Imagine that, an OS that recognises (and uses) obviously faulty memory hardware without complaint or notification - sure inspires confidence in the reliability of Windows - NOT!

---

### Post by cryogenic on 2009-02-26
I'll agree with sanderj above... I would definitely RMA the faulty stick to G.Skill first off.. but also check for a new BIOS update for your motherboard. On my work PC (Intel DQ965GF) the BIOS itself showed 4GB available but Ubuntu only saw 3.2GB. There is no memory remap option in the Intel BIOS. I updated the BIOS to the latest version and instantly saw all 4GB. Strange, but it ended up fixing my problem. Can't hurt to explore that option.

---

### Post by rumblered on 2009-02-27
My laptop with 4GB of RAM generates loads of errors when I run memtest86+, until it causes the system to reboot. I think the version included with Ubuntu has some bugs dealing with large amounts of memory. Of course, if it finds a problem with just 2 GB installed, then you do have a problem.

---

