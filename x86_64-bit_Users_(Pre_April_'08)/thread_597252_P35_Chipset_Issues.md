---
title: "P35 Chipset Issues"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by netbandit on 2007-10-30
Howdy.  First off, let me say that Ubuntu has truly been the best distro I have used, and I've been using linux since 1993.

Next, let me brag about my system:
Core2Quad Q6600 (Quadcore 2.4GHz)
8GB Dual Channel DDR2 800MHz (PC6400) RAM
ATi x300 w/128MB RAM (Yes, it is garbage)
Dual 500GB SATAII Drives (Software RAID 1)
Generic POS Recycled DVD-ROM (Not a burner)
Abit IP35-E Motherboard
575W Power Supply

Anyway, here is my problem.  In Ubuntu 7.10 (and 7.04) x86_64 I have to use the acpi=off setting in order for it to boot ok (both from CD and Hard Drive). Is there some sort of problem with the Intel P35 Chipset?  Is there another work around that doesn't disable ACPI completely?  I'd like to be able to throttle the CPU back to conserve power and more importantly heat.  Anyone else running a P35 Chipset board with similar experiences?

-nb

---

### Post by Modred on 2007-10-30
My system is remarkably similar to yours

2 GB Dual Channel DDR2 1066 MHz
EVGA GeForce 8600 GTS 256 MB
Gigabyte P35-DS3P mobo

Otherwise almost exactly the same.  Just built it last week and haven't had a single problem, so I would guess it isn't something with the P35 chipset alone.  I don't know enough about acpi to have any idea what it could be, but I know my computer boots fine without disabling acpi.

---

### Post by netbandit on 2007-10-30
64Bit Ubuntu?

Oh, i forgot to mention one piece of hardware
Adaptec 2940UW (for my Sony SDT10000 Tape drive, only SCSI device, BIOS doesn't load)

-nb

---

### Post by Modred on 2007-10-30
Yes, Gutsy x86_64.  I've been quite surprised at just how well it has worked, given some of the troubles people reported on the forums.

---

### Post by netbandit on 2007-10-30
I wonder if the memory addressing is the issue.  I don't want to yank out RAM to find out.

There are some BIOS updates available for my mobo... i just hate having to put Windows or DOS on it to get them.  I guess I might as well do it now before I am fully vested and have VMWare on it.

thanks,
-nb

---

### Post by Tlon on 2007-10-30
I think I've got the same mobo as Modred, and I didn't have to disable ACPI.  I'm curious: how do you *know* that you had to disable it?  I DID get the BSOD (black screen of death) after first installing the OS, but that went away once I disabled the splash screen.

---

### Post by Desslok on 2007-10-30
I'm running a similar motherboard here as well.  No major issues with Feisty Fawn X86_64:

Asus P5K Deluxe/WiFi-AP
8GB PC2 6400 G.SKILL
Intel Core 2 Quad Q6600 2.6 GHz
Asus EN8800GTS 640M PCIe Video
4x Seagate 500GB SATA 3.0Gb/s HDD in mixed RAID 1/5 (boot RAID 1 w 2 spare parts, Data RAID 5 using all 4 Disks)  using Linux Software RAID
1000W PSU
2x Lite-On SATA DVD Burners

     Only issue I ran into was having to put the Disks into AHCI mode to get things to boot up right.  I'm actually just been "Burning In" on the feisty install for a few weeks waiting for Gusty to release.  WIll probably re-install over the next few days and then "Move in"

Clif

---

### Post by Arkainium on 2007-10-30
Same motherboard here, and there is a problem when booting.  For me it's pretty random.  Either the system boots up fine and everything works great or it won't boot up at all.  It doesn't actually cause a hard lock up though (caps works and I can restart with the 3 finger salute).  Getting Gutsy installed was quite a feat as it seems to not boot more often with the Live CD.  Once installed though it doesn't seem so bad.

Sounds like this bug, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132776](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132776)

---

### Post by netbandit on 2007-10-31
Well, at least it is good to know that it is not something inherent to the P35 Chipset that is causing this problem.  I managed to buy a POS motherboard.  I still need to try those BIOS updates as that could solve the problem.

And my issue is the same as what was described in the link:  If i boot without acpi=off, it will just choke on the hard drive controllers and eventually quit doing anything.  Having the SCSI card in there probably doesn't make things any better either.

Thanks for everyone's help and input!
-nb

---

### Post by phcahill on 2007-11-01
Have you tried running your SATA in IDE mode?

My gigabyte board allows the ICH9 controller to run in IDE, AHCI or RAID modes. At the moment I am running in IDE mode with a triple boot of XP, Vista and Gutsy. No problems so far. 

I may swap to AHCI to get hot swap enabled although this motherboard has a couple of SATA ports connected to a JMicron JMB36X controller.

---

### Post by netbandit on 2007-11-01
I'm not sure if my motherboard supports running SATA in IDE mode... but I did notice that it says the SATA  drives are at 133MB/s during bootup.  

This is the output of:  dmesg | grep 133
```

[   75.461714] ata1: SATA max UDMA/133 cmd 0x000000000001f900 ctl 0x000000000001f802 bmdma 0x000000000001f500 irq 19
[   75.461717] ata2: SATA max UDMA/133 cmd 0x000000000001f700 ctl 0x000000000001f602 bmdma 0x000000000001f508 irq 19
[   75.674960] ata1.00: ATA-7: MAXTOR STM3500630AS, 3.AAE, max UDMA/133
[   75.758196] ata1.00: configured for UDMA/133
[   75.978750] ata2.00: ATA-7: MAXTOR STM3500630AS, 3.AAE, max UDMA/133
[   76.070286] ata2.00: configured for UDMA/133
[   79.158763] ata3: SATA max UDMA/133 cmd 0x000000000001f200 ctl 0x000000000001f102 bmdma 0x000000000001ee00 irq 19
[   79.158766] ata4: SATA max UDMA/133 cmd 0x000000000001f000 ctl 0x000000000001ef02 bmdma 0x000000000001ee08 irq 19

```

Now that we are talking about IDE mode, I would hope to get more than 133MB/s out of my drive's interface.. even if the drives can only sustain about 50-100MB/s I'd at least like small chunks (that could fit in their 16MB cache) to go at full speed 300MB/s.

Any ideas, or should i post something else?

-nb

---

### Post by Desslok on 2007-11-07
All,

     Just an update, re-installed with Gutsy Gibbon X86_64 and no major issues thus far.  However did note that the Marvell 88E8056 does not seem to work at all.  Seems that the system sees it, but whenever I attach the cable there it never gets an IP from my local DHCP server.   The Realtek 8169 seems to work just fine though.
     I initially tried Envy to install the NVidia drivers, however the system was unstable.  Went ahead and re-installed again and just used the restricted drivers and have had no issues since.  Have advanced effects and such turned on.

Clif

---

### Post by kanatu on 2007-11-20
I've been dealing with this acpi issue as well, on one of my client's computers.

system information:

Motherboard:  ABIT IP35-E LGA 775 Intel P35 ATX
Processor: Intel Core 2 Duo E6600 Conroe 2.4GHz LGA 775
Memory: CORSAIR XMS2 (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)
Case/PSU: Antec Sonata III Black 0.8mm cold rolled steel ATX Mid Tower,  500W
Graphics Card: ASUS EN7200GS/HTD/256M GeForce 7200GS 256MB 64-bit GDDR2 PCIx x16

Hard Drive: Western Digital Caviar SE16 WD3200AAKS 320GB 7200 RPM SATA 3.0Gb/s
Optical: ASUS 18X DVD±R DVD Burner with LightScribe and 14X DVD-RAM Write Black SATA Model DRW-1814BLT

With x86_32, the board reliably boots with acpi=off in the kernel's commandline, and fails roughly 30% of the time with ACPI enabled.

I'm currently running my test suites on x86_64.

I was also having a weird problem with the system failing to obtain DHCP leases on it's own, and me needing to restart networking one or more times for it to fix.  It looks like it was some sort of disagreement between the clients networking stack and the hub I have on my bench, as plugging it directly into my switch seems to have fixed it.

---

### Post by kanatu on 2007-11-21
Update:

I've finished testing x86_64, and I've got some interesting results.

First of all, I tested with acpi=off in the kernel's command line.  No errors at all.

Then I tried it without, and got the initramfs, then a successful bootup, initramfs, and boot.  It kept repeating that pattern throughout the test, regardless of warm or cold booting the computer.  Suffusive to say, failure rate under x86_64 was 50%.

Interesting.

---

### Post by Maintech on 2007-11-22
I have an Abit IP35 motherboard also and have never been able to get any version of Ubuntu to boot. I've tried the ACPI=off and I still get a kernel panic. It doesn't see my drive controller. I've been told it is because I am using IDE setting in bios, running an IDE cd/dvd-rw drive and SATA 2 drives. I've also been told that if I had bought SATA cd/dvd-rw instead of IDE it would boot. I have it set up dual boot with Vista. Not sure I can change the bios setting from IDE now that I have Vista installed. The funny thing is I can (and have) installed SuSE 10.3 and Fedora 8 with no issues. Both run fine and everything works. I just prefer a debian based linux. I have Fedora 8 dualbooting on it now. Any ideas when Ubuntu is going to get their software fixed/updated so it works like SuSE and Fedora?? (All OS's are running in 64 bit)

Abit IP35 motherboad
Intel Q6600 Quad-Core
4 x 1Gig Market DDR2 800
4 x 250 Gig Maxtor SATA 2
Lite-On CD/DVD-RW
Nvidia GeForce 8800 GTS
850 watt Thermaltake power supply

---

### Post by fjf on 2007-11-22
My abit ip35 pro works fine with Gutsy.  All SATA (HDD & DVD-RW).

---

### Post by fjgaude on 2007-11-22
> **fjf said:**
> My abit ip35 pro works fine with Gutsy.  All SATA (HDD & DVD-RW).

Can you suspend, hibernate, recover successfully?

---

### Post by dj1120 on 2007-11-23
Hi all I just built a new pc with an Abit IP35 MB  I cannot install Linux (Fedora 8 or Ubuntu 7.10) on this pc But was able to install Vista Home premium can someone point me toward a fix.

  My specs 

 Abit IP35 Pro
Intel Core2Duo E6750
 2 GB Crucial Ballistix Ram

3 sata HD 250,300,400 GB (vista running on the 250 gb drive)

I wish to do a triple boot with an os on each drive    DJ1120

---

### Post by dj1120 on 2007-11-24
Hi there , I have an Abit IP35 Pro as well but cannot get any version of Linux to boot what bios version do you have I am stuck with Vista Home premium as that is the only os the machine will install

---

### Post by kanatu on 2007-12-07
Hey all,

Having thought everything was fixed with acpi=off, I sent the (afore mentioned) computer back to my client, only to have him call me a few days later.  Apparently the Marvell gigabit ethernet on it really doesn't like being connected to his netgear brand router (something I found oddly similar when testing with some netgear hardware I had sitting around), and after digging around through the sparse documentation on the subject, apparently the sky2 driver (previously the sk98lin driver) has a long complaint list having to do with spotty performance/randomly locking machines.  Fortunately, I have a spare 10/100 card sitting around (too many systems with on-board ethernet nowadays), but I'm curious if anyone else has gotten far enough to test this.

Basically, the module complains with "link is not ready" randomly and I can't generate or receive packets over that interface.  It is remedied by cold-booting, sometimes more than once.

---

### Post by Radon on 2007-12-09
> **dj1120 said:**
> Hi there , I have an Abit IP35 Pro as well but cannot get any version of Linux to boot
Any Linux distribution or just Ubuntu?  

I just got a MSI NEO2-FR and straight away booted the E6400 at 8*400MHz.  After some tweaking and overnight Memtest 1.70 it's happy at 420MHz.  Since I had 2 similar Seagate HDD's lying around setup RAID0 in the BIOS and then realised that the Ubuntu 7.10 installator wasn't too happy about it and demanded dmraid from the alternative CD download.  Not having the bandwidth to download Ubuntu the second time, I proceeded to install OpenSuSE 10.3 which setup RAID for me automagically.  I would recommend you give it a try.

---

### Post by brainatwork on 2008-01-14
hello there.
I have an abit ip35-e.

and am experiencing pretty much all the issues you guys are describing... dhcp lease lost, random boot up, and somewhat a sluggish performance...

am trying to update the kernel and all to see if there will be any progress.. have you guys found any "solutions" so far ?

---

### Post by fjgaude on 2008-01-14
It seems no one wishes to comment on their experience with the P35 chipset. Really, what does it take to get a MB working fully with one of these Intel chips?

So many of the companies are using Intel instead of nVidia these days for their Northbridge. I'm looking to get a near-topend Gigabyte MB with either the P35 or X38 chipset. Anyone here using such?

---

### Post by tgalati4 on 2008-01-14
I built a machine for a client with an Intel P35 MB and a Dual core E6750, 4 GB of RAM, 2 SATA 500 GB Hitachi Deathstar drives in IDE mode, and nVidia 8600GT.  No problems so far.  It's a dual-boot gaming machine.  Linux Mint 4 (gutsy 32-bit) is installed on a small partition for Windows repair and maintenance and to show my client some neat things in Linux when Windows breaks.  

18 minutes from loading the Live CD to installing to rebooting to surfing the web.  Got to love it.

I've demonstrated googleearth and a few games in 3D, no problems so far (on the Linux side anyway).  

So, I would recommend an Intel brand P35 board, but I ran an overnight memtest to make sure that 4 GB in dual-channel mode would hold up at max speed.  Wonky RAM will certainly cause problems.

I set up the disks as IDE mode because the extra speed (if any) is not needed for gaming and this machine is not set up as an true RAID.  I may play with the higher speed disk modes later, but for now things are working OK.

---

### Post by Yellow Pasque on 2008-01-14
fjgaude, is there a reason you don't want to use an nvidia chipset? It used to be that the nFurnace systems drew significantly more power than the P965, but the P35 is just as bad now. Other than the high heat output, I can't complain too much about my old nF4 board.

---

### Post by fjgaude on 2008-01-14
> **Temüjin said:**
> fjgaude, is there a reason you don't want to use an nvidia chipset? It used to be that the nFurnace systems drew significantly more power than the P965, but the P35 is just as bad now. Other than the high heat output, I can't complain too much about my old nF4 board.

That's like what I have now, A8N Deluxe. I tell you the only reason I would go with P35 and Gigabyte is that it seems more folks have had less problems with such than with Asus and nVidia. That's it. I've watched these forums for about six months and just about ready to do a major upgrade to my main box. I don't wish to go through more issues than I have to to still use 64-bit Ubuntu.

I guess I'm waiting for the Wolfdale, 45nm CPUs to come out this month before I decide what I'm gonna do.

---

### Post by fjgaude on 2008-01-25
Okay, I went and done it: bought a Gigabyte GA-P35-DS4 motherborad. Installed easily. Even booted my old Ubuntu 64-bit install and auto-mounted the raid5 array. Wow! Everything worked...

But, and there always seems to be a "but", "CPU freq scaling" doesn't work in Ubuntu and none of the temp and fan sensors. I loaded lm-sensors, etc. Nothing from them.

Thinking I would have to re-install Ubuntu since I was going from an AMD X2 to an Intel Core 2 Duo, I did not (amazing), but with the same results. No temps or freq control.

Is there a setting in the BIOS that let's Ubuntu see the MB's sensors and speed control of the CPU?

Sure would appreciate any suggestions. Thanks!

---

### Post by LO Matt on 2008-01-25
Did you follow [this]("http://ubuntuforums.org/showthread.php?t=2780") Howto to install lm-sensors?  I have the intel dp35dp board, and I do get cpu sensors but nothing else.  Also, my temp sensors seem rather high.  I don't believe my idle temps of 45-50C on a Q6600 are right.  Under constant load they reach 70c or so . . . :confused:

---

### Post by fjgaude on 2008-01-26
> **LO Matt said:**
> Did you follow [this]("http://ubuntuforums.org/showthread.php?t=2780") Howto to install lm-sensors?  I have the intel dp35dp board, and I do get cpu sensors but nothing else.  Also, my temp sensors seem rather high.  I don't believe my idle temps of 45-50C on a Q6600 are right.  Under constant load they reach 70c or so . . . :confused:

No, I didn't. My cpu is the just-issued Penryn E8400, 45nm at 3.0MHz. The BIOS shows it running at 32C with fan running at 820RPM.

Will take a stab at install lm-sensors post. Will get back with you after.

Thanks for the tip.

---

### Post by fjgaude on 2008-01-26
Well, I did as your post reference stated and got just about everything I ever dreamed of. Fans, temps, voltages, the whole nine yards, wow! Will now go to the sensor.conf file and get the right labels printed for everything, and maybe a scale set here and there. In hogs heaven!

Thanks, man!

---

