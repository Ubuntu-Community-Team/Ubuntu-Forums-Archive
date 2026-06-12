---
title: "BIOS hiding 4th gig of 4 gig installation?"
date: 2008-07-02
forum: x86 64-bit Users
---

### Post by richiethom on 2008-07-02
Hi,

I have just put 2 2gig sticks into my laptop (Core2DUO T5300), but only 3 gigs is seen in Ubuntu.

I have both 32-bit and 64-bit versions of Ubuntu 8.04 installed, and both report the same. Vista Home Premium 32-bit also only sees 3 gigs. The 64-bit Ubuntu 8.04 live CD is the same.

However, the BIOS sees all 4 gigs, but doesn't offer any settings to change the memory allocation (it's very locked down).

If I run the lshw command on either the 32 or 64 bit Ubuntus, I get:

```
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             serial: D531600A
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 1
             serial: D531600B
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
```

So the deeper probing and the BIOS can see the 4 gigs of ram, but neither 32-bit nor 64-bit OSs can see it.

My guess is that I need to upgrade the BIOS, but the problem is that it is a Phoenix TrustedCore BIOS and the laptop manufacturer (Gateway UK) says there is no upgraded BIOS available for the laptop.

Does anyone have any suggestions about the way forward for this?

Thanks in advance for any help!

Rich

---

### Post by movieman on 2008-07-02
Check the BIOS settings to see if there's a 'memory remapping' option. The BIOS has to allocate space in the top 1GB for memory-mapped 32-bit PCI hardware, and that hides the system RAM that exists at those addresses... typically it's only 512MB that vanishes, but there could be situations where the whole 1GB goes. The BIOS should remap that missing RAM so that it's visible at >4GB addresses, but some won't do that by default without enabling the special settings, and some won't do it at all.

---

### Post by Yellow Pasque on 2008-07-02
What does *free -m* show?

---

### Post by richiethom on 2008-07-02
free -m shows (I had a few apps running at the time):
```
             total       used       free     shared    buffers     cached
Mem:          3033       2936         97          0         18       1027
-/+ buffers/cache:       1890       1143
Swap:         3208        307       2900

```

I've looked a few times at the BIOS, and it really is heavily locked down (I think that the Phoenix TrustedCore BIOSes are particularly bad for this); even the option to change the amount of memory available to the graphics card is greyed out at 8 megs.

---

### Post by kuja on 2008-07-02
Are you sure the motherboard supports 4GB of memory? I've looked around and it looks like some boards only support up to 3GB (which is odd, but look around and you'll see what I mean)

---

### Post by richiethom on 2008-07-02
I must admit, I'm not certain the board supports 4 gigs, but if the Bios can see it, then doesn't that mean that it does?

---

### Post by Joshuwa on 2008-07-02
If I remember correctly, the default kernel can only recognize ~3.6gb of RAM.

To get it to acknowledge the full 4g, I believe a kernel recompile is necessary.

I've just added my 2nd 2gb stick, and logged on to see if I could find the instructions for that, and what specifically needed to  be changed during the recompile.


**EDIT:** After some reading, I've discovered this:
1) That's just the way it is, a recompile will not help. The system reserves some ram for system processes, which is around 800-900mb, which accounts for our difference.

2)You *can* get a linux box to recognize the full 4gb, but it requires using a server kernel, which might require even more work-arounds for other things (graphics drivers, etc).

See: [http://sudan.ubuntuforums.com/showthread.php?t=484222](http://sudan.ubuntuforums.com/showthread.php?t=484222)
and [http://www.linuxquestions.org/questions/linux-hardware-18/4gb-ram-not-showing-300277/](http://www.linuxquestions.org/questions/linux-hardware-18/4gb-ram-not-showing-300277/)

---

### Post by slowcoach on 2008-07-02
As stated, standard 64bit kernel will access >4GB of ram but you have to set “map around memory hole” to enabled in the BIOS, with the setting disabled I only have 3.2GB available.
If your BIOS does not have such a setting  then the manufacturer assumed users would be using a normal 32bit OS where the standard kernel is limited to 3GB of memory.

---

### Post by richiethom on 2008-07-03
So I'm guessing that the only options are:

[LIST=1]
[*]Try and get my money back on one of the 2gig sticks, and put one of the 1gig sticks back (assuming the speeds are appropriate).
[*]Upgrade the BIOS somehow, probably unofficially, seeing as the manufacturer says there are no BIOS updates for that model.
[*]Hack the BIOS - I think there are some tools in the darker corners of the net that let you edit certain properties of Phoenix TrustedCore BIOSes.
[/LIST]

---

### Post by techstop on 2008-07-03
> **Joshuwa said:**
> If I remember correctly, the default kernel can only recognize ~3.6gb of RAM.

To get it to acknowledge the full 4g, I believe a kernel recompile is necessary.

I've just added my 2nd 2gb stick, and logged on to see if I could find the instructions for that, and what specifically needed to  be changed during the recompile.


**EDIT:** After some reading, I've discovered this:
1) That's just the way it is, a recompile will not help. The system reserves some ram for system processes, which is around 800-900mb, which accounts for our difference.

2)You *can* get a linux box to recognize the full 4gb, but it requires using a server kernel, which might require even more work-arounds for other things (graphics drivers, etc).

See: [http://sudan.ubuntuforums.com/showthread.php?t=484222](http://sudan.ubuntuforums.com/showthread.php?t=484222)
and [http://www.linuxquestions.org/questions/linux-hardware-18/4gb-ram-not-showing-300277/](http://www.linuxquestions.org/questions/linux-hardware-18/4gb-ram-not-showing-300277/)

That's not true at all. This is with a EP35-DS3P motherboard (Intel P35 chipset) with 4GB of RAM and the default 64-bit Hardy kernel;

```
techstop@office:~$ uname -a
Linux office 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux
techstop@office:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3936         25          0          7       3055
-/+ buffers/cache:        874       3088
Swap:         1592         15       1576
techstop@office:~$ 

```

ie. I haven't compiled a custom kernel or done anything except install Hardy 64-bit and it can see (almost) the full 4GB. The reason some users can't see the full 4GB is purely and simply a hardware limitation of their motherboard.

---

### Post by Guilden_NL on 2008-09-05
I turned it on and it went from 3.1GB to 3.9GB. All of the discussion around use by PCI-E etc was excellent, no need to chase that 100MB when it is being used by video etc.

Two thumbs up for the excellent insights here! :guitar:

---

### Post by richiethom on 2008-09-05
Sorry Guilden_NL, what did you turn on?

---

### Post by IntuitiveNipple on 2008-09-05
Be wary of some systems, especially laptops and notebooks, that may have 64-bit CPUs *but* only have a **32-bit Northbridge** (that's the interface to memory, etc.).

For example, the Intel 945GM/PM/GMS, 943/940GML and 945GT.

---

