---
title: "Dapper and64 Install CD kernel panic"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by MasonM on 2006-06-07
I'm trying to install Dapper on my box but I just can't get the CD to boot. It gives a kernel panic not syncing error. Anyone know how to get past this?

It's an eMachines with an Athlon +3000 and an ATI SATA drive.

---

### Post by r3st on 2006-06-07
try downloading it again and reburning it.

---

### Post by MasonM on 2006-06-07
[QUOTE=r3st]try downloading it again and reburning it.[/QUOTE]

Did that already.

---

### Post by Kilz on 2006-06-07
[QUOTE=MasonM]I'm trying to install Dapper on my box but I just can't get the CD to boot. It gives a kernel panic not syncing error. Anyone know how to get past this?

It's an eMachines with an Athlon +3000 and an ATI SATA drive.[/QUOTE]

Are you using the live cd to install? If so and you just want to install try the Alternate or text based installer cd. I could never get the live cd to boot.

---

### Post by MasonM on 2006-06-08
[QUOTE=Kilz]Are you using the live cd to install? If so and you just want to install try the Alternate or text based installer cd. I could never get the live cd to boot.[/QUOTE]

Ok, I tried that. Exact same result. I'm suspecting a lack of support for my ATI SATA disk controller in this kernel.

---

### Post by philipt on 2006-06-08
[QUOTE=MasonM]I'm trying to install Dapper on my box but I just can't get the CD to boot. It gives a kernel panic not syncing error. Anyone know how to get past this?

It's an eMachines with an Athlon +3000 and an ATI SATA drive.[/QUOTE]

I had the same problem on my laptop. I upgraded the firmware in bios and it solved the problem.

---

### Post by MasonM on 2006-06-08
[QUOTE=philipt]I had the same problem on my laptop. I upgraded the firmware in bios and it solved the problem.[/QUOTE]

BIOS is the most current.

It's some problem with the amd64 version. The i386 version boots just fine.

---

### Post by skrållarn on 2006-07-06
I have the same problem. cannot boot dapper cd on my amd64 athlon 3000+.
it says:
 CR2: 00000000e0100000
 <0>Kernel panic - not syncing: Attemted to kill init!

---

### Post by skrållarn on 2006-07-06
finally! 
it runs just fine after firmware upgrade.
I have MSI mainboard and used MSI upgrading tool from msicomputer.com/

---

### Post by skegg on 2006-07-06
[QUOTE=MasonM]BIOS is the most current.

It's some problem with the amd64 version. The i386 version boots just fine.[/QUOTE]

I am having the same problem. I'm not using SATA drives and have SATA disabled in BIOS

Gigabye GAK8NF-9 (latest BIOS)
Athlon 64 3200+
2x512MB Generic DDR PC3200
GeForce 6600GT 256MB

---

### Post by Kilz on 2006-07-06
You all might want to do your part to make Ubuntu better by filing a bug report. Otherwise this problem will never go away.

---

### Post by nicko7i on 2006-10-20
My system showed this message when booting AMD64 Dapper Drake.  Looking at the earlier lines revealed the most recent messages came from 'acpi_init'.  

I disabled ACPI in the BIOS and had no further trouble.

I'm running an MSI RS480M2-IL motherboard.

n

---

### Post by paulphillips on 2006-10-31
> **nicko7i said:**
> My system showed this message when booting AMD64 Dapper Drake.  Looking at the earlier lines revealed the most recent messages came from 'acpi_init'.  

I disabled ACPI in the BIOS and had no further trouble.

I'm running an MSI RS480M2-IL motherboard.

n

I'm using the same motherboard as you, and yet, my dapper amd64 dvd panics on bootup, and I'm pretty sure I've tried disabling ACPI in BIOS.  Did you have to pass "acpi=off" to the kernel as well?  Have you updated your BIOS?

Have you tried Edgy yet?  (see my thread on this here: [http://ubuntuforums.org/showthread.php?t=289342](http://ubuntuforums.org/showthread.php?t=289342))

---

### Post by nicko7i on 2006-11-01
I didn't pass any arguments to the kernel. No BIOS update... it's as-shipped circa mid-2005.  Haven't tried Edgy.

I don't see the BIOS displaying a revision number.  If you know where it is, lemme know and I'll let you know what rev I'm running.

---

### Post by paulphillips on 2006-11-01
> **nicko7i said:**
> I didn't pass any arguments to the kernel. No BIOS update... it's as-shipped circa mid-2005.  Haven't tried Edgy.

I don't see the BIOS displaying a revision number.  If you know where it is, lemme know and I'll let you know what rev I'm running.

To see BIOS rev, you need to remove the ATI splash screen you get a boot up.  To do this, go into BIOS settings, and disable it (can't remember where, but you should know it when you see it).

Next time you boot up, you should see it.  Mine is at rev v3.4, and the latest appears to be v3.8, although not much seems to have changed since v3.4.

Now as an update... I tried my dapper DVD again last night, just to make sure.  I disabled ACPI in the BIOS, and rebooted. Panic.  I tried "acpi=off".  Panic.  Then, due to errors telling me that it was failing while disabling dma on hda, I tried booting with my HDDs all removed, leaving only my DVD.  It booted!  (not very useful though :-? )

So what HDD(s) have you got?  SATA or normal IDE (PATA?) ?  Mine are just plain old IDE:
IDE Channel 0: Master - 80GB
IDE Channel 0: Slave - 20GB
IDE Channel 1: Pioneer DVR-109

(so to get it to boot, I just unplugged the HDD cable, and swapped the DVD to channel 0).

---

### Post by nicko7i on 2006-11-01
It goes by pretty fast, but I'll guess the "V3.3B3" is the version number for the BIOS.  

I'm running a DVD on Channel0:Master and a single SATA disk.  I have {Channel0:Slave, Channel1:Master, Channel1:Slave} disabled in the BIOS.  (This was done so that XP would "see" the SATA drive)  The BIOS reports the SATA drive as Channel2.

Just in case it's useful, I'll mention that XP does not see the SATA drives with ACPI turned off.  I have to turn ACPI off to use LiveCD, and back on to use XP (this last bit of knowledge cost me at least a full day of hand-wringing.  Long off-topic story.).

The game is afoot, though I'm not certain which direction it's heading...

n

---

### Post by paulphillips on 2006-11-01
> **nicko7i said:**
> It goes by pretty fast, but I'll guess the "V3.3B3" is the version number for the BIOS.  

I'm running a DVD on Channel0:Master and a single SATA disk.  I have {Channel0:Slave, Channel1:Master, Channel1:Slave} disabled in the BIOS.  (This was done so that XP would "see" the SATA drive)  The BIOS reports the SATA drive as Channel2
n
Well it looks like BIOS version is unlikely to be the problem.

Hmmm... maybe I'll try swapping the channel's around so that the DVD is always on channel 0 and the HDDs on channel 1 &  try disabling the others and see what happens.

Now I don't suppose you could grab an old IDE drive and test it out for me to see if it happens for you also? I know that's a big ask - feel free to ignore :)

Anyway - thanks Nick for your help!

---

