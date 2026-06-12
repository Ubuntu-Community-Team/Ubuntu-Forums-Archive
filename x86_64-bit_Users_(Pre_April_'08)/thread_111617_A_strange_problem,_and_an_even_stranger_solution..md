---
title: "A strange problem, and an even stranger solution."
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by bannerboy on 2006-01-02
I am running Kubuntu 5.10 breezy badger on my AMD Athlon X2 dual-core 64bit processor, and kde3.5, and I have a verry strange problem. openoffice(2.0) will occationally hang my computer, I don't mean that it will slow down, I mean it completely hangs, as in I can't even change the numlock or switch to a different terminal. I thought that this was a openoffice problem and didn't worry too much about it untill the other day when I built cinelerra, and tried some video ripping using my video4linux card. Things were going good for about 20 minutes, when guess what..... it hung. again, I was ready to pass this off as a cinelerra bug, when I got the idea that mabe the two problems weren't isolated issues. so I started to look for similarities between the two peices of software, the similarites that I saw rigth away were:

1. they both draw thier own interface
2. they both require some or all 32bit libraries

In order to try to isolate the problem, I went out on a hunch: mabe KDE is the problem. so I pulled up adept, and installed twm, set up my xinitrc file to use twm as a window manager, and tried cinelerra with that, and my problems stopped. I haven't had another freeze since. then I started thinking back as to when my openoffice problems started, and the only thing I may have changed that could have affected it was installing KDE3.5 back in November.

Here's my question... Have I gone crazy, or should I send a bug report to KDE?

---

### Post by tokyovigilante on 2006-01-03
What video card and driver do you use?

---

### Post by bannerboy on 2006-01-03
Here's my specs, and everything works fine except cinelerra and openoffice.

AMD Athlon 64 X2 3800+ Dual Core
Gigabyte K8U 939 Motherboard
Nvidia GeForce 5900 XT (with official NVidia drivers)
512MB Kingston PC 3200 DDR SDRAM
Segate 80 GB IDE hard drive
Segate 40 GB IDE hard drive
Sony DVD-RW Drive

---

### Post by tokyovigilante on 2006-01-05
Hmm, I've never had any trouble with Oo.o on my (similar) machine (I don't use cinelerra).

If you're sure you don't have a harware issue (running memtest86 might be a good idea), try running both programs from the terminal. This will show you any error messages they generate when crashing. Obviously not much help if the whole system is locking up though. This usually indicates a kernel-panic, as individual applications shouldn't be able to take the system (or even your session) down, because of good memory management.

---

### Post by jyhelle on 2006-01-11
[QUOTE=bannerboy]Here's my specs, and everything works fine except cinelerra and openoffice.

((cut))[/QUOTE]

Nearly the same configuration, (memory is 1GB and the disks are 120 GB) and I have noticed the same especially when running compute-hungry things (cinelerra, transcode), but also sometimes the system locking when several tasks are launched at the same time... I have run memtest for several hours and also some disks transfers exercizers, but your post makes me think that, yes, the beginning of my problems seem to coincide with the KDE 3.5 installation:
from my notes the move to 3.5 was done on december 20, and the first mention of system locking is dated december 23

Since I prefer the 3.5 version, I'll rather move my movie editions to the old single-32bit-proc system, but the random locking eventuality will remain I'm afraid 

edit: tokyovigilante, in my case at least it is a complete lock, the only escape is by pushing either the reset switch or the power supply on-off switch.
I know it is locked when the green led at front of the HF-mouse receiver is off, while it's normally always on or blinking when the mouse is moved. seems to indicate the system is no longer polling the usb port ? or is the power sent to the usb under proc control ?

:(

---

### Post by tokyovigilante on 2006-01-12
[QUOTE=jyhelle]
edit: tokyovigilante, in my case at least it is a complete lock, the only escape is by pushing either the reset switch or the power supply on-off switch.
I know it is locked when the green led at front of the HF-mouse receiver is off, while it's normally always on or blinking when the mouse is moved. seems to indicate the system is no longer polling the usb port ? or is the power sent to the usb under proc control ?
:([/QUOTE]
Yeah complete hardware unresponsiveness generally means a hard lock due to a kernel panic. I used to have the occasional ndiswrapper lockup when I was using a USB wireless adapter, and you could always tell it was time for a cold boot when Numlock stopped responding.

To both you guys, it looks like a bug in KDE 3.5 is showing up a 2.6.12 kernel bug. A user-space program like KDE shouldn't be able to take down a linux kernel, and it looks like a 2.6.12 amd64-smp bug is letting it.

The only real solution I can offer, would be an upgrade to Dapper. I've found it's 2.6.15-11 kernel to be rock-solid, and it has a unified SMP/non-SMP kernel now which detects whether you have a dual-core system and enables the appropriate mode. The Flight-2 CD has been very stable for me, and I'm tracking the daily updates without a problem. No hardware issues either, and it has the 1.0-8178 nvidia driver packaged.

I'd stick with amd64 if you can, I've found a substantial performance advantage with 64-bit native code, particularly when doing things like transcoding DVDs (although I use mencoder), in amd64 I can rip and encode a DVD to two-pass Xvid in under an hour.

---

### Post by jyhelle on 2006-01-13
slightly off-topic, but:

[QUOTE=tokyovigilante]and it has a unified SMP/non-SMP kernel[/QUOTE]

Gee, does it mean I could have a single "master" disk to maintain ?

I have 3 systems, one is the dual core mentioned above, the other is a single AMD64 used by my wife and the third is a 32/64 capable motherboard presently equipped with a 32bit AMD but that I could replace by a 64 bit cpu

the idea would be to create a single system disk that I would then triplicate, rather than having to update each system one by one

If that could work, I'm more than willing to be Dapperized !

---

### Post by tokyovigilante on 2006-01-15
Sorry I see what you mean now. Yeah the amd64-generic kernel supports both SMP/non-SMP processors, as does the amd64-k8 kernel, without needing a separate -smp kernel.

---

### Post by elektronaut_no on 2006-01-16
this is a longshot, but.. have you tried installing the latest official nvidia drivers? i've had lots of similar problems (across multiple machines) relating to buggy nvidia drivers, but the current drivers seems stable.

---

### Post by m.musashi on 2006-01-24
[QUOTE=tokyovigilante]I'd stick with amd64 if you can, I've found a substantial performance advantage with 64-bit native code, particularly when doing things like transcoding DVDs (although I use mencoder), in amd64 I can rip and encode a DVD to two-pass Xvid in under an hour.[/QUOTE]

:confused: Can you explain why this is fast? I can rip, shrink and burn a dvd with dvdshrink on a Windows laptop (with only a Celeron processor) in 40min or so depending on the size of the original. I was hoping my AMD64 would run even faster but haven't got it set up yet. Are you doing a different type of process or is Linux actually slower than Windows?:(

---

### Post by tokyovigilante on 2006-01-25
[QUOTE=m.musashi]:confused: Can you explain why this is fast? I can rip, shrink and burn a dvd with dvdshrink on a Windows laptop (with only a Celeron processor) in 40min or so depending on the size of the original. I was hoping my AMD64 would run even faster but haven't got it set up yet. 
[/QUOTE]

Shrinking a DVD is a very different process. MPEG-II (DVD) to MPEG-II **trans**coding is a straightforward relatively computationally-light process, while MPEG-II to MPEG-4 (DivX/Xvid) **en**coding is much more involved due to the substantially increased complexity and compression of MPEG-4, and as such requires much more processing power and time. 

As a comparison, a DVD to Xvid encode using ffmpegX (excellent frontend BTW) using my 1.33Ghz G4 iBook running MacOS X takes ~4-5 hours for a two hour movie.

[QUOTE=m.musashi]Are you doing a different type of process or is Linux actually slower than Windows?:([/QUOTE]
Hardly ;)

---

### Post by m.musashi on 2006-01-25
[QUOTE=tokyovigilante]Shrinking a DVD is a very different process. MPEG-II (DVD) to MPEG-II **trans**coding is a straightforward relatively computationally-light process, while MPEG-II to MPEG-4 (DivX/Xvid) **en**coding is much more involved due to the substantially increased complexity and compression of MPEG-4, and as such requires much more processing power and time. [/QUOTE]

Thanks for the mini lesson. I guess I haven't tried to do any **en**coding. Can you explain the benefit of encoding or a scenario in which MPEG-4 would be preferred? I felt pretty good to just figure out how to copy a DVD but apparently I have a lot to learn still. :KS Also good to know I'm in the right place regarding my choice of OS. ;)

---

### Post by tokyovigilante on 2006-01-26
Hey, no problem.

The main use for the MPEG-4 series codecs (DivX - proprietary, Xvid - OSS, H.264 - Apple) is a much higher compression ratio for comparable quality. A stream almost indistinguishable from MPEG-II, ie DVD quality, can be obtained between 800-1000kbit/sec, whereas DVD streams are in the region of 4200kbit/sec.

In practice you can get a DVD down to ~700MB w/o much quality loss, ideal for backing up to CD, or saving space when archiving to your HDD, or recording from a PVR or TV tuner card.

Don't feel bad, the day you stop learning is the day you kick the bucket. Have fun!

---

### Post by m.musashi on 2006-01-27
Thanks again. It looks like i've kind of hijacked this thread so I'll refrain from asking any more question. Thanks for the info though. I'll try and teach myself how to encode to MPEG-4. Sounds like it could be useful.

---

### Post by Bandit on 2006-01-28
TO answer our question why 64bit is faster, this explanation might help.
if you have bucket that can hold 32 potatoes and you run back and forth from the garden to the house with the potatoes. It will take you a while, but if your bucket can hold 64 potatoes, then you can move more potatoes. Or in the case of computers, if the program is designed for 64bit it can run much faster. Actual results can very, but over all it is technically faster.
Cheers,
Bandit

---

### Post by towsonu2003 on 2006-01-28
ok this is borderline weird but, you have a swap partition right? at least 512MB or more? juuuuust asking ;)

---

### Post by tokyovigilante on 2006-01-28
[QUOTE=Bandit]TO answer our question why 64bit is faster, this explanation might help.
if you have bucket that can hold 32 potatoes and you run back and forth from the garden to the house with the potatoes. It will take you a while, but if your bucket can hold 64 potatoes, then you can move more potatoes. Or in the case of computers, if the program is designed for 64bit it can run much faster. Actual results can very, but over all it is technically faster.
Cheers,
Bandit[/QUOTE]
I love this analogy ;)

I'd just add most of the time you don't need to move more than 32 potatoes at once, so having a bigger bucket won't be such an advantage. But the general trend is for people to need to be moving more potatoes, so having a bigger bucket now will be a much bigger advantage for the future.

---

### Post by bannerboy on 2006-02-03
with the dapper flight-3 cd ready, I'm starting to think that dapper might be a good thing. exactly how do you switch?

when is dapper officially supposed to be released?

and if you'll allow me to continue the analogy.......
Some Programs would be sped up by being able to carry 64 potatoes at a time, but due to the way that the program is written, they can not take advantage of your new ability. and if you have a dual-core processor it's kind of like having 2 seperate 64 potato buckets.

---

