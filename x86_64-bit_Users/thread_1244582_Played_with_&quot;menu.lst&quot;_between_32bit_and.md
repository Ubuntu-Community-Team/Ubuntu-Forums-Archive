---
title: "Played with &quot;menu.lst&quot; between 32bit and 64bit of 9.04"
date: 2009-08-19
forum: x86 64-bit Users
---

### Post by uncleV on 2009-08-19
Wanted to compare 64bit 9.04 with 32bit 9.04 on my new

EP31-DS3L motherboard
Pentium E5400 processor (2x2.7 GHz 64bit)
4 MB RAM
9600 GT graphics card

computer to see the difference.

So had installed 9.04 32bit (on primary partition 30 GB + 2GB swap) on a fresh empty 320 GB disk. It worked fine.
Now installed on the same disk 9.04 64bit.
For that purpose downloaded from ubuntu.com the .iso for 64bit version, md5sum it, burned it at the lowest speed of 24, booted from it, checked the LiveCDx64 for errors - all fine.
Loaded Ubuntu 9.04x64 from that disk ("Without any changes to your computer") to see what's going on - fine.
Gparted from the live session the fresh disk. The remaining space of the disk after 9.04x32 was NTFS formatted by me. Resised it by Gparted and gave it a free unallocated space of 50 GB at the end of disk. Didn't wait the end of resising because the space was empty and clicked Cancel. Warning of possible severe loss of data. Never mind - cancel! Had after that resised NTFS with free space of 50 GB unallocated on disk.
Now under the same live session chose Install. Installed 9.04x64 manually on the unallocated space giving 4.5 GB swap and the rest as primary ext4 mounted on "/". The installation went without errors and at the end I proudly said "reboot" and waited to see boot option of BOTH 64b and 32b 9.04...
;-)
Booting gave me the option only to the previous installed 32b 9.04... Well, booted to it, saw the partition of the new 64b 9.04.
Hmm... Copied the boot/grub/menu.lst of 64bit version over the same of 32bit version. Now I waited the reboot with half a proud...
;-)
Yeah, there were the two versions - the 64b loading after Enter and the 32bit choices telling me "cannot mount partition".

Meanwhile I saw 64bit works for me grate!

Well, not so proudly I tried some combinations of pasting to the different "menu.lst" of parts of the other file and came to working situation with the combination of pasting the boot lines from 64bit version menu.lst to the one of 32bit. Now I could boot either to 32 or 64bit version. And I was again proud of myself;-)

But now that I saw the 64 bit satisfies me I deleted the partition of 32bit and reformatted it to NTFS so I had again two parts on my disk - NTFS and the new 64bit on ext4 at the end of the disk (I fully don't understand which is the "start" or the "end" of the disc like Gparted says. The disc is a circle isn't it?..)

You probably know what followed - no booting.
Heh, simply deleted all partitions on the disk under live session and then freshly installed manually the 64bit Ubuntu Jaunty Jackalope 9.04 and it works now at about 50% boost as compared with the previous 32bit version.

So want to ask - why I couldn't boot to 9.04x64 in both cases described above?
Thank you in advance people!

---

### Post by lemming465 on 2009-08-20
> ... which is the "start" or the "end" of the disc ... [it's] a circle isn't it?
A typical hard drive has a fairly complicated geometry these days.  You may have multiple double-sided platters stacked on a single spindle, usually with a comb of read/write heads.  Usually the bottommost surface is dedicated to servo tracks and is read-only, no data.  The remaining surfaces are divided into circular data tracks, yes.  Probably each track has some spare sectors reserved for error relocations, and probably some entire cylinders (same track on all surfaces of all platters) are also reserved for error relocations.  This lets the disk firmware present the illusion of a perfect drive to the OS, as long as any read failures are detected at write time and immediately remmapped. Since the outer tracks are longer than the inner ones, usually the disk is broken up into 16 or so "zones", where each zone has a different number of sectors per track.  The outer zones tend to have about twice the data transfer rate of the inner zones, as a result.  The "start" of the disk is the first data sector in linear addressing, which will be the first sector of the outermost track on the first data surface.  The "end" of the disk will be the last sector of the innermost track on the last data surface.  To minimize seeks between cylinders, when a track is full the next block comes from the next surface in the same cylinder.

> ... Booting gave me the option only to the previous installed 32b 9.04.
Probably the MBR (master boot record) of the disk had the 32-bit grub, and the 64-bit grub was hidden away on the ext4 partition with no reference to it from the previous 32-bit install.  One workaround in this scenario is to have a chainloader entry pointing at the secondary grub, e.g.```

title 64-bit ubuntu grub menu
rootnoverify (hd0,3)
chainloader +1
```

> I deleted the partition of 32bit and reformatted it to NTFS ... no booting.
That's because the 32-bit install's secondary boot loader and /boot contents being pointed to by the MBR were gone.  This could be evaded by booting a live CD, modifying the 64-bit /boot/grub/menu.lst file to install to the MBR, and running grub-install with the --root-directory option to fix up the boot loader situation.

>  ... about 50% boost as compared with the previous 32bit version
That's unsually good; most people only get about 15% from going from 32-bit to 64-bit, but as you have found, it varies a lot depending on CPU workload and disk geometry.

---

### Post by uncleV on 2009-08-21
Thank you very much for your comprehensive answer and effort!

Now it's clearer to me the nowadays hard-disk structure and also the booting process.

---

### Post by uncleV on 2009-08-21
Thank you, [lemming465]("http://ubuntuforums.org/member.php?u=194283")!

---

