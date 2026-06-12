---
title: "[SOLVED] Gutsy ATI Driver Boot Hang"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by n1418 on 2007-10-20
Gutsy works fine until I enable the restricted ATI driver.  After the mandatory reboot, Kubuntu hangs on a  text screen with "loading boot scripts" being the last line on the screen.

I'm not very concerned about recovering this Ubuntu install, as it's fresh and I have nothing I can't lose on it, but I really want to resolve this issue.  It's happened now both with the Release Candidate and the Final version of Gutsy.

My hardware is:

Athlon 3600+ 
Asrock ATI 1600 motherboard
Radeon HD 2600 pro
2GB OCZ DDR2-800
OCZ 700W GameXstream PSU

---

### Post by blueglow on 2007-10-21
Same problem here with Asus X1600 card.

Vesa works fine but after installing the ATI driver (using restricted driver manager OR Envy OR getting/installing the latest from the ATI website) I get a black screen crash on startup before x starts.

uname -a:
 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

---

### Post by n1418 on 2007-10-21
Any ideas anyone?  This is a pretty serious issue considering ATI accounts for 30% of the graphics market share.  

If its any help, my second computer with IGP ATI X1250 works fine with the restricted driver on Gutsy Kubuntu AMD64.

---

### Post by intel on 2007-10-22
bootup using the recovery kernel

OR

remove the splash options from bootline

then we can know what is the error(google the error)

---

### Post by Jouke74 on 2007-10-22
I have an Asus EAX1600Pro and I installed the restricted ATI driver through the restricted drivers manager (8.37 I think). I disabled my splash by turning splash into nosplash in the grub menu.lst. This is something I always do, as I like to see what's happening during boot. Anyway, my computer goes fine with the X1600 card. 

AMD X2 4200
Asus A8N SLI Premium
Asus EAX1600pro
2 GB Corsair memory and still some disks.

---

### Post by n1418 on 2007-10-22
intel:

I'll post back with what I find.

---

### Post by SKiFF on 2007-10-23
> **blueglow said:**
> Same problem here with Asus X1600 card.

Vesa works fine but after installing the ATI driver (using restricted driver manager OR Envy OR getting/installing the latest from the ATI website) I get a black screen crash on startup before x starts.

uname -a:
 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

Yeah tried all of the above mentioned as well and the same result...black screen after the UBUNTU loading bar...

Im running ATI x1950pro

---

### Post by Turas on 2007-10-23
I am having the same problem here.  I did load into the recovery console but had no idea what to do from there. I have a 2900XT.  This is my first real attmpt on Linux as I am a Primary windows user.  I still drop out into a command line every chance I get so I thought I would take a stab at Ubuntu and and use wine or codeweaver to run the ferw things I need through windows. 

How can I disable the driver in recovery console?

---

### Post by SKiFF on 2007-10-23
> **Turas said:**
> I am having the same problem here.  I did load into the recovery console but had no idea what to do from there. I have a 2900XT.  This is my first real attmpt on Linux as I am a Primary windows user.  I still drop out into a command line every chance I get so I thought I would take a stab at Ubuntu and and use wine or codeweaver to run the ferw things I need through windows. 

How can I disable the driver in recovery console?

I just copy over the backed up xorg.conf file to deal with that issue, but if you want I think you can try to do the following: nano -w /etc/X11/xorg.conf
that will edit the file, and there you replace VESA or FLGRX with ati so it uses a different driver, it should start up but will give you a shitty resolution ...

---

### Post by Lweek on 2007-10-24
Hello everyone!
I have same problem with MSI Ati HD 2600PRO. I tried to install absolutely new drivers {8.41.7 x86_64} which should be working specialy fox X2000 product line but it doesn't help.

---

### Post by Saint Angeles on 2007-10-24
check out my post here:

[http://ubuntuforums.org/showthread.php?t=588636]("http://ubuntuforums.org/showthread.php?t=588636")

---

### Post by Saint Angeles on 2007-10-24
> **Lweek said:**
> Hello everyone!
I have same problem with MSI Ati HD 2600PRO. I tried to install absolutely new drivers {8.41.7 x86_64} which should be working specialy fox X2000 product line but it doesn't help.

ATI released the 8.42... driver today!

no more XGL! (it hogged my CPU)

---

### Post by n1418 on 2007-10-26
> **intel said:**
> bootup using the recovery kernel

OR

remove the splash options from bootline

then we can know what is the error(google the error)

Alright, it took me a few days to get around to trying again.  I blew away the AMD64 install and put on 7.10 Kubuntu x86, in the hopes that it was just a driver issue.

No dice.  I still get the same hang after "Running local boot scripts (/etc/rc.local) line on bootup.

I've tried all the other advice in the forum I've found, to include

--pressing enter
--editing the tty files in /etc/event.d

The only thing I've found that works is to restore my xorg.conf file from the backup I made before enabling the ATI driver.  This of course disables the driver.

Has anyone figured anything new to try?

---

### Post by n1418 on 2007-10-26
Pressing ALT+F2 at the "running local scripts line" gave me a logon prompt

After logging in, I was dumped onto the command line.  

I typed "startx" which crashed X, spilling out some errors.

I've attached the applicable log file that shows the errors.  Look at the end of the file.


[PHP]X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux nick-lin-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 26 05:43:07 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "A-17"
(**) |   |-->Device "ATI Technologies Inc ATI Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 1849,5950 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5a37 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1849,4380 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1849,4387 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1849,4388 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1849,4389 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1849,438a rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1849,438b rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1849,4386 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1849,4385 rev 13 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1849,438c rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1849,0888 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1849,438d rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10ec,8168 card 1849,8168 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 1002,9589 card 17af,2002 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,aa08 card 17af,aa08 rev 00 class 04,03,00 hdr 80
(II) PCI: 03:07:0: chip 10b7,9200 card 10b7,1000 rev 78 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:5:0), (0,1,1), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc unknown chipset (0x9589) rev 0, Mem @ 0xd0000000/28, 0xfeaf0000/16, I/O @ 0xd000/8, BIOS @ 0xfeac0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[1] -1	0	0xfeaec000 - 0xfeaeffff (0x4000) MX[B]
	[2] -1	0	0xfe9ff000 - 0xfe9fffff (0x1000) MX[B]
	[3] -1	0	0xfe8f4000 - 0xfe8f7fff (0x4000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8ff0ff (0x100) MX[B]
	[5] -1	0	0xfe8fa000 - 0xfe8fafff (0x1000) MX[B]
	[6] -1	0	0xfe8fb000 - 0xfe8fbfff (0x1000) MX[B]
	[7] -1	0	0xfe8fc000 - 0xfe8fcfff (0x1000) MX[B]
	[8] -1	0	0xfe8fd000 - 0xfe8fdfff (0x1000) MX[B]
	[9] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[10] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[11] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[12] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[22] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[24] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[1] -1	0	0xfeaec000 - 0xfeaeffff (0x4000) MX[B]
	[2] -1	0	0xfe9ff000 - 0xfe9fffff (0x1000) MX[B]
	[3] -1	0	0xfe8f4000 - 0xfe8f7fff (0x4000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8ff0ff (0x100) MX[B]
	[5] -1	0	0xfe8fa000 - 0xfe8fafff (0x1000) MX[B]
	[6] -1	0	0xfe8fb000 - 0xfe8fbfff (0x1000) MX[B]
	[7] -1	0	0xfe8fc000 - 0xfe8fcfff (0x1000) MX[B]
	[8] -1	0	0xfe8fd000 - 0xfe8fdfff (0x1000) MX[B]
	[9] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[10] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[11] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[12] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[22] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[24] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[5] -1	0	0xfeaec000 - 0xfeaeffff (0x4000) MX[B]
	[6] -1	0	0xfe9ff000 - 0xfe9fffff (0x1000) MX[B]
	[7] -1	0	0xfe8f4000 - 0xfe8f7fff (0x4000) MX[B]
	[8] -1	0	0xfe8ff000 - 0xfe8ff0ff (0x100) MX[B]
	[9] -1	0	0xfe8fa000 - 0xfe8fafff (0x1000) MX[B]
	[10] -1	0	0xfe8fb000 - 0xfe8fbfff (0x1000) MX[B]
	[11] -1	0	0xfe8fc000 - 0xfe8fcfff (0x1000) MX[B]
	[12] -1	0	0xfe8fd000 - 0xfe8fdfff (0x1000) MX[B]
	[13] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[14] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[15] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[16] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[28] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[30] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(--) Chipset Supported AMD Graphics Processor (0x9589) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[5] -1	0	0xfeaec000 - 0xfeaeffff (0x4000) MX[B]
	[6] -1	0	0xfe9ff000 - 0xfe9fffff (0x1000) MX[B]
	[7] -1	0	0xfe8f4000 - 0xfe8f7fff (0x4000) MX[B]
	[8] -1	0	0xfe8ff000 - 0xfe8ff0ff (0x100) MX[B]
	[9] -1	0	0xfe8fa000 - 0xfe8fafff (0x1000) MX[B]
	[10] -1	0	0xfe8fb000 - 0xfe8fbfff (0x1000) MX[B]
	[11] -1	0	0xfe8fc000 - 0xfe8fcfff (0x1000) MX[B]
	[12] -1	0	0xfe8fd000 - 0xfe8fdfff (0x1000) MX[B]
	[13] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[14] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[15] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[16] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[28] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[30] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8208b40
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffc7f (0x80) MX[B]
	[5] -1	0	0xfeaec000 - 0xfeaeffff (0x4000) MX[B]
	[6] -1	0	0xfe9ff000 - 0xfe9fffff (0x1000) MX[B]
	[7] -1	0	0xfe8f4000 - 0xfe8f7fff (0x4000) MX[B]
	[8] -1	0	0xfe8ff000 - 0xfe8ff0ff (0x100) MX[B]
	[9] -1	0	0xfe8fa000 - 0xfe8fafff (0x1000) MX[B]
	[10] -1	0	0xfe8fb000 - 0xfe8fbfff (0x1000) MX[B]
	[11] -1	0	0xfe8fc000 - 0xfe8fcfff (0x1000) MX[B]
	[12] -1	0	0xfe8fd000 - 0xfe8fdfff (0x1000) MX[B]
	[13] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[14] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[15] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[16] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[31] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[32] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[33] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RV630" (Chipset = 0x9589)
(--) fglrx(0): (PciSubVendor = 0x17af, PciSubDevice = 0x2002)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfeaf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.56
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV630
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): === [swlDalHelperPreInit] === DALEnableInstance failed
(EE) fglrx(0): PreInitDAL failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "fglrxdrm"
(II) Unloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
[/PHP]

Anybody know what direction I should head in at this point?

Thanks!

---

### Post by n1418 on 2007-10-26
Also, I noticed it's using the 8.37 driver.  Why not the 8.41, or better yet the 8.42 ??

Bear in mind this is the driver that's automatically d/loaded through restricted-manager on kubuntu

---

### Post by KRavEN on 2007-10-26
I had the same problem with  the GPL ati driver.  I had to install in failsafe mode and when I switched from the vesa driver to the ati driver xorg would peg the CPU and the monitor would go into powersave mode.  I didn't have the same problem with i386 Gutsy.  I tracked it down to a DRI problem.  Once I set DRI off in the xorg.conf everything worked fine.

---

### Post by n1418 on 2007-10-26
Thanks for the info Kraven.

What exactly is DRI, and how do I disable it?

---

### Post by jimminy_kriket on 2007-10-27
If you turn DRI off, doesnt that disable direct rendering? Hence making the driver next to useless?

---

### Post by jimminy_kriket on 2007-10-27
BTW this is happening to me on the 32bit build, i tried installing fglrx via envy, no go but I didnt care because it tried installing an older driver. After that I installed the latest driver using the instructions on the ati wiki. Driver installed like it did with envy but once again it was using mesa. 

From there i tried uninstalling the driver using envy, and now I'm here..

---

### Post by n1418 on 2007-10-28
Well, I installed the latest driver from ati (8.42.3, I believe) using the feisty faun manual install method detailed on the "HOW TO install ATI driver" thread located in the multimedia section of this site. 

It took a minute or two to do it all, but the restricted driver IS WORKING now

glxgears gives me about 4500 fps (with opensource it was only 700fps), so I guess it's working.

---

### Post by Yellow Pasque on 2007-10-28
A lot of people have had success with the 'aticonfig --initial -f' command to set automatically set up their xorg.conf after installing the proprietary driver.

---

### Post by gwhit918 on 2007-11-01
Why is this thread marked [SOLVED]? Am I missing something?  I don't see any resolution to the driver issue mentioned here.  FWIW, my ACER Aspire is doing the same thing (blank/black screen after enabling the ATI driver from the Restricted Driver Manager).  ...worked fine w/Feisty.

---

### Post by brianbarry on 2007-11-02
Try this: ALT-F2 to a command line, login in, and issue the following command.

sudo dpkg-reconfigure xserver-xorg

I've had success in the past with this in similar situations.

Brian

---

### Post by abickerton on 2007-11-03
I had this same problem with my Radeon 9600 Pro, using dual monitors.  

Here's how I solved it.

1 - edit /etc/X11/xorg.conf (Make a copy first) replace flgrx with vesa
2 - restart and login

If your using dual monitors, you can't use compiz because the texture size is too large,  so you'll need to remove it
3 - Completely remove all compiz related packages with synaptic 
4 - (Re)Install metacity
5 - Set your window manager to metacity with 
$gconf-editor
set the key: /desktop/gnome/applications/window_manager/current to /usr/bin/metacity
6 - restart x (reboot or logout and back in)
7 - edit /etc/X11/xorg.conf replace vesa with your driver of choice or try the new AIGLX driver

Single monitor users, that really want compiz. 
2 - Download the 8.42.3 drivers from the amd website. There's a bug reported on lauchpad that details how to install the the drivers. follow them.

3 - edit /etc/X11/xorg.conf add the Option AIGLX "1"and composite "1" in the server section.

_Installing the new ATI driver_ 
Download the 8.42.3 drvers from the amd website. There's a bug reported on lauchpad that details how to install the the drivers. 

[Detailed instructions]("http://www.phoronix.com/forums/showthread.php?t=5947")

(I experienced some issues with openGL due to fast writes being enabled in the bios :( YMMV)

Hope this is of some use.
Alec.

---

