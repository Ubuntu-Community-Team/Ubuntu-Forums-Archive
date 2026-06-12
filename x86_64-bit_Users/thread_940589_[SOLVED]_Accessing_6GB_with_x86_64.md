---
title: "[SOLVED] Accessing 6GB with x86_64"
date: 2008-10-07
forum: x86 64-bit Users
---

### Post by craig.taverner on 2008-10-07
I upgraded from 3GB to 6GB, but available memory only moved from 3.0GB to 3.2GB. I have hardy-heron 64bit and have spent the last week reading a huge number of forum archives with no solution found. My bios sees all 6GB, as does 'lshw', but free, top and 'system monitor' only see 3.2GB. The bios has no option like 'memory remaping' or similar, and I tried almost every option I could fiddle anyway.

uname -a
[INDENT]**2.6.24-19-generic** #1 SMP Aug 20 2008 **x86_64** GNU/Linux[/INDENT]
free -t
[INDENT]          total       used       free     shared    buffers     cached
Mem:    **3354552**    3314656      39896          0     220092     171544
[/INDENT]
Key info from lshw:
[INDENT]    product: IMEDIA W1607
    vendor: PACKARD BELL BV
    version: PB80X05291
    firmware:
[INDENT]          vendor: Phoenix Technologies, LTD
          version: **PBCLR0.P10** (08/20/2007)[/INDENT]
    CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
    *-memory
[INDENT]          description: System Memory
          slot: System board or motherboard
          size: **6GiB**[/INDENT]
    (memory seen as 4 banks, 2x2GB and 2x1GB, matching bios view)
     *-display
[INDENT]          description: VGA compatible controller
          product: GeForce 8600 GS
          vendor: nVidia Corporation[/INDENT]
[/INDENT]
The vendor [hardware description page]("http://support.packardbell.com/se/item/index.php?i=spec_motherboard_clara&psn=101294750371") claims this motherboard can handle up to 8GB memory, and since both the bios and lshw see all 6GB, I'm at a loss as to why the kernel cannot. It is a 64bit kernel after all. I've even tried installing and rebooting to the server kernel (which again saw only 3.2GB and introduced a bunch of other problems, so I took it out again). I've also tried using mem=4096M and mem=6144M options in the kernel boot, with no effect.

What else can I try? It is possible that the vendor lied about this system supporting 8GB? Am I missing something? I'm even considering (shudder) re-installing vista to see if that works.

---

### Post by dabl on 2008-10-07
These specs from your vendor's site may be significant:

> # Support for up to 8GB of system memory (using 512 and 1GB modules)
# Supports only un-buffered non-ECC DDR2 DIMMs.

What model of DIMMs are you using?

One would not think that using both 2GB and 1GB modules would be a source of problems, but ... ???

Did you try it with just the 2GB DIMMs installed?  How about with just the 1GB DIMMs installed?  That experiment might yield clues to what's going on there.  :)


p.s. Oddly, the photo on the Packard Bell site shows a motherboard with only TWO DIMM slots.

---

### Post by craig.taverner on 2008-10-07
The photo of the motherboard is deceptive, but if you look carefully there are four slots, two yellow and two blue. The blue ones are hard to see as they are nearly the same color as the board itself. The reason for the colors is that you are supposed to put identical DDR2 boards in similarly colored slots to achieve 'Dual Channel' performance gains. The bios confirmed I got the right boards in the right slots (reported 'dual channel' instead of 'single channel').

The quote is also strange, as it contradicts itself. How can you get 8GB in 4 slots if you cannot use 2GB DIMMS? However, since the bios could see all 6GB, I choose to believe that 8GB is possible (and I also note that lshw in linux saw all 6GB too).

I did try using only the 2GB DIMMS, in matching and mismatching slots, and the bios always got the right total, but linux always only saw 3.2GB.

---

### Post by craig.taverner on 2008-10-07
Solved!

I did a bios update and viola! Linux could see all 6GB.

Of the dozens of things I thought to try, the only one I missed was this one. I thought I had the latest update, since the bios could see all 6GB before and because the release notes of the bios downloads said the latest bios was for quad core support, which my current bios clearly did support. However, on a second pass of the bios updates site today, I noted that the version numbers did not match the lshw output (which said v10, while the download was v13). So I downloaded it, installed it, rebooted and am now a much happier ubuntu user :guitar:

What have I learned from all this? You never can tell, and you simply have to try every option possible. Since both the bios and lshw could see the 6GB, and since the bios update release notes were quite deceptive, it really looked like a bios update was a pointless exercise, and yet it was the necessary trick.

---

### Post by dabl on 2008-10-07
Cool.   :popcorn:

---

