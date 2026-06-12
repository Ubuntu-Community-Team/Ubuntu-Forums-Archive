---
title: "Yet another Steam + wine thread"
date: 2007-11-07
forum: Wine
---

### Post by FrshMint on 2007-11-07
Okay, be aware that i've extensively researched my problem and found no results.

Here is the problem:
I've installed STEAM fine and downloaded a few days, DOD:S and TF2
Everytime I start a game, it loads up... the "Valve" sumo wrestler somes up, then the "SOURCE" logo, but right when its about to load the game navigation, the game closes completely and my desktop is left running at 800x600.


Here is what ive tried:
1. Running desktop at 800x600 prior tostarting game
2. Running at 1024x768
3. Running at 1280x1024
4. Using the ATI "restricted" drivers
5. Using the normal default drivers

Specs:
AMD X2 3800+
x850xt
1gb ram
other irrelevant crap im too lazy to list.

Im running Ubuntu 7.10

Thanks in advance.

---

### Post by MrFSL on 2007-11-07
Have you tried running the game + wine from the terminal? Posting the output from the terminal might help solve your problem.

---

### Post by Rafadagaffer on 2007-11-08
Ive got the exact same problem. coudln't find a solution to it :(.

I haven't tried running the game from the terminal yet, will try and edit back

EDIT: Ive got an X1600 pro, could this be an ATI specific problem?

---

### Post by Melhisedek on 2007-11-08
I was about to install Steam + TF2 tonight but will probably wait and see if you guys can solve it
Have 1900XT card here

---

### Post by FrshMint on 2007-11-08
> **MrFSL said:**
> Have you tried running the game + wine from the terminal? Posting the output from the terminal might help solve your problem.
I'm linux illiterate i'm still learning. Can you post how i'd do such a thing?

---

### Post by Rafadagaffer on 2007-11-09
Ok just updated to Gutsy, the same thing happens but at least I get an error this time.

failed to lock vertex buffer in cmeshdx8

A quick google search reveals this occurs on Windows machines with the incorrect DirectX version.

Does wine even use DirectX:confused:, I wouldn't think so but better be sure

---

### Post by aoanla on 2007-11-09
Wine, of course, emulates DirectX calls, otherwise you'd not be able to play most Windows games ;)

Try running games from the command line with a -dxlevel 80 switch

(or, alternatively, add -dxlevel 80 to the launch options for the game in question in Steam (that is, select the game, choose "Properties" and then "Launch Options" and enter "-dxlevel 80" without the quotes)

You might also like to try setting hl2.exe to run in Windows 98 mode in winecfg (run that from the command line).

---

### Post by element8 on 2007-11-10
running steam from the console instead of clicking the icon it makes on your desktop after you install it with wine, i used this command for tf2:
```
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe \
    -width 1280 -height 800 -applaunch 440 \
    -heapsize 512000 +map_background none -opengl
```

with -fullscreen after Steam.exe if you want it full, i think you can still set the width and height in fullscreen but you can change that in the options of the game then restart the program to get it going

here's a link that i got the command from and a walkthrough that worked for me: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam")

and here's a list of the applaunch numbers for all the different steam games (not all are going to work in wine without some extra work, some need extra fonts, etc):
[http://developer.valvesoftware.com/wiki/Steam_Applaunch_IDs#Source_Engine_Games]("http://developer.valvesoftware.com/wiki/Steam_Applaunch_IDs#Source_Engine_Games")

if it's still crashing you can copy the stuff in the terminal to here to see what's causing it to not work, i think instead of -opengl you can use something like -dx9 or -dxlevel 80 or something like that to get it working too like aoanla said

---

### Post by Rafadagaffer on 2007-11-10
Thanks I tried setting the dxlevel to 80 and using a win98 cfg for hl2.exe, still no luck :(.

This is what I use to launch it and what errors it threw up

```
derek@derek-desktop:~$ cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 320 -dx level 80 -novid - height 1280 -width 1024
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Win32 MiniDump Helper version 1.0.0.0 (c) Copyright 2000-2003 Valve Corporation All rights reserved.

Expected argument 'ProcessId'.

Usage: WriteMiniDump [@argfile] [/?|h|help] [/v|version] [/Type <value>] <ProcessId> <DumpFile>

@argfile        Read arguments from a file.
/?              Show usage.
/v              Show version.
/Type <value>   Select dump type values are:
                   normal       
                   full         
ProcessId       Select process id for which to generate a dump
DumpFile        Select path of output dump file

Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
X Error of failed request:  GLXBadCurrentWindow
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  4476
  Current serial number in output stream:  4485

```

Any help would be great :)

---

### Post by aoanla on 2007-11-10
The error dump including complaints about lack of XFree86-DRI suggests strongly that your drivers are not installed correctly for your graphics card. (As it's an ATI card, this is unsurprising...)

Can you try typing "glxinfo | grep render" into a terminal, and tell us if it says "Yes"? If it doesn't, the issue is that your drivers are not set up correctly - in which case, can you post the contents of /var/log/Xorg.0.log so we can diagnose the issue?

---

### Post by Rafadagaffer on 2007-11-10
Ok direct rendering returned a no, I was using the ATI driver in the restricted driver manager. Im in the process of getting the latest from their website and installing it, following this tutorial [http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843).

I will report back when Im done. Thanks for your help:)

---

### Post by Rafadagaffer on 2007-11-11
Ok finished installing the driver, still returns a no for direct rendering

The contents of my /var/log/Xorg.o.log is 

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux derek-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 11 20:43:26 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
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
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 8086,29a0 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1462,7235 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1462,7235 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1462,7235 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 8086,284b rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1462,7235 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1462,7235 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1462,7235 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1462,7235 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2810 card 8086,2810 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2820 card 1462,7235 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1462,7235 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2825 card 1462,7235 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 1002,71c2 card 1002,71c2 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e2 card 1002,71c3 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:00:0: chip 197b,2361 card 1462,7235 rev 02 class 01,06,01 hdr 80
(II) PCI: 02:00:1: chip 197b,2361 card 1462,7235 rev 02 class 01,01,85 hdr 00
(II) PCI: 03:06:0: chip 10ec,8167 card 1462,235c rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xd0000000/28, 0xfdef0000/16, I/O @ 0xde00/8
(--) PCI: (1:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xfdee0000/16
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
	[0] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[1] -1	0	0xfdbfe000 - 0xfdbfffff (0x2000) MX[B]
	[2] -1	0	0xfdffd000 - 0xfdffd0ff (0x100) MX[B]
	[3] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[4] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[6] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[10] -1	0	0x0000bb00 - 0x0000bb0f (0x10) IX[B]
	[11] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[12] -1	0	0x0000bd00 - 0x0000bd07 (0x8) IX[B]
	[13] -1	0	0x0000be00 - 0x0000be03 (0x4) IX[B]
	[14] -1	0	0x0000bf00 - 0x0000bf07 (0x8) IX[B]
	[15] -1	0	0x0000ee00 - 0x0000ee0f (0x10) IX[B]
	[16] -1	0	0x0000ef00 - 0x0000ef0f (0x10) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]
	[18] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]
	[19] -1	0	0x0000f200 - 0x0000f203 (0x4) IX[B]
	[20] -1	0	0x0000f300 - 0x0000f307 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[23] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[24] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]
	[25] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]
	[26] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]
	[27] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]
	[28] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[30] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[32] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[33] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[1] -1	0	0xfdbfe000 - 0xfdbfffff (0x2000) MX[B]
	[2] -1	0	0xfdffd000 - 0xfdffd0ff (0x100) MX[B]
	[3] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[4] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[6] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[10] -1	0	0x0000bb00 - 0x0000bb0f (0x10) IX[B]
	[11] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[12] -1	0	0x0000bd00 - 0x0000bd07 (0x8) IX[B]
	[13] -1	0	0x0000be00 - 0x0000be03 (0x4) IX[B]
	[14] -1	0	0x0000bf00 - 0x0000bf07 (0x8) IX[B]
	[15] -1	0	0x0000ee00 - 0x0000ee0f (0x10) IX[B]
	[16] -1	0	0x0000ef00 - 0x0000ef0f (0x10) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]
	[18] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]
	[19] -1	0	0x0000f200 - 0x0000f203 (0x4) IX[B]
	[20] -1	0	0x0000f300 - 0x0000f307 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[23] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[24] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]
	[25] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]
	[26] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]
	[27] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]
	[28] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[30] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[32] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[33] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
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
	[4] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[5] -1	0	0xfdbfe000 - 0xfdbfffff (0x2000) MX[B]
	[6] -1	0	0xfdffd000 - 0xfdffd0ff (0x100) MX[B]
	[7] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[8] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[10] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[11] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[16] -1	0	0x0000bb00 - 0x0000bb0f (0x10) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[18] -1	0	0x0000bd00 - 0x0000bd07 (0x8) IX[B]
	[19] -1	0	0x0000be00 - 0x0000be03 (0x4) IX[B]
	[20] -1	0	0x0000bf00 - 0x0000bf07 (0x8) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000ee0f (0x10) IX[B]
	[22] -1	0	0x0000ef00 - 0x0000ef0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]
	[24] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]
	[25] -1	0	0x0000f200 - 0x0000f203 (0x4) IX[B]
	[26] -1	0	0x0000f300 - 0x0000f307 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[29] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[30] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]
	[31] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]
	[32] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]
	[33] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]
	[34] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[36] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[37] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[38] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[39] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71C2) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[5] -1	0	0xfdbfe000 - 0xfdbfffff (0x2000) MX[B]
	[6] -1	0	0xfdffd000 - 0xfdffd0ff (0x100) MX[B]
	[7] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[8] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[10] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[11] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[16] -1	0	0x0000bb00 - 0x0000bb0f (0x10) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[18] -1	0	0x0000bd00 - 0x0000bd07 (0x8) IX[B]
	[19] -1	0	0x0000be00 - 0x0000be03 (0x4) IX[B]
	[20] -1	0	0x0000bf00 - 0x0000bf07 (0x8) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000ee0f (0x10) IX[B]
	[22] -1	0	0x0000ef00 - 0x0000ef0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]
	[24] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]
	[25] -1	0	0x0000f200 - 0x0000f203 (0x4) IX[B]
	[26] -1	0	0x0000f300 - 0x0000f307 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[29] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[30] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]
	[31] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]
	[32] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]
	[33] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]
	[34] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[36] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[37] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[38] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[39] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8206650
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[5] -1	0	0xfdbfe000 - 0xfdbfffff (0x2000) MX[B]
	[6] -1	0	0xfdffd000 - 0xfdffd0ff (0x100) MX[B]
	[7] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[8] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[10] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[11] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[19] -1	0	0x0000bb00 - 0x0000bb0f (0x10) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[21] -1	0	0x0000bd00 - 0x0000bd07 (0x8) IX[B]
	[22] -1	0	0x0000be00 - 0x0000be03 (0x4) IX[B]
	[23] -1	0	0x0000bf00 - 0x0000bf07 (0x8) IX[B]
	[24] -1	0	0x0000ee00 - 0x0000ee0f (0x10) IX[B]
	[25] -1	0	0x0000ef00 - 0x0000ef0f (0x10) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]
	[27] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]
	[28] -1	0	0x0000f200 - 0x0000f203 (0x4) IX[B]
	[29] -1	0	0x0000f300 - 0x0000f307 (0x8) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[32] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[33] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]
	[34] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]
	[35] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]
	[36] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]
	[37] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[38] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[39] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[40] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[41] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[42] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
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
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1600 Series" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x71c2)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfdef0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
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
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on secondary DAC [crt2]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ACR  Model: ad51  Serial#: 1681941123
(II) fglrx(0): Year: 2006  Week: 44
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.07
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.289 greenY: 0.609
(II) fglrx(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) fglrx(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No: ETL5108197
(II) fglrx(0): Ranges: V min: 55  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: Acer AL1716
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00047251ad83624064
(II) fglrx(0): 	2c10010368221b6b2ac0f5a3574a9c23
(II) fglrx(0): 	114f54a54f00818f8180614f6140454f
(II) fglrx(0): 	454001010101302a009851002a403070
(II) fglrx(0): 	1300540e1100001e000000ff0045544c
(II) fglrx(0): 	353130383139370a2020000000fd0037
(II) fglrx(0): 	4b1e530e000a202020202020000000fc
(II) fglrx(0): 	004163657220414c313731360a20003d
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on secondary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 500/396MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 41 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x576": 11.9 MHz (scaled from 0.0 MHz), 14.9 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "720x576"   11.89  720 696 760 800  576 577 580 595 interlace +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x480": 12.0 MHz (scaled from 0.0 MHz), 15.0 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "720x480"   11.97  720 696 760 800  480 481 484 499 interlace +hsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (340, 270) mm
(--) fglrx(0): DPI set to (95, 96)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x576": 11.9 MHz (scaled from 0.0 MHz), 14.9 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "720x576"   11.89  720 696 760 800  576 577 580 595 interlace +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x480": 12.0 MHz (scaled from 0.0 MHz), 15.0 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "720x480"   11.97  720 696 760 800  480 481 484 499 interlace +hsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) LoadModule: "glesx.so" (glesx)
(WW) LoadModule: given non-canonical module name "glesx.so"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[7] -1	0	0xfdbfe000 - 0xfdbfffff (0x2000) MX[B]
	[8] -1	0	0xfdffd000 - 0xfdffd0ff (0x100) MX[B]
	[9] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[10] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[11] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[12] -1	0	0xfdee0000 - 0xfdeeffff (0x10000) MX[B](B)
	[13] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[22] -1	0	0x0000bb00 - 0x0000bb0f (0x10) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[24] -1	0	0x0000bd00 - 0x0000bd07 (0x8) IX[B]
	[25] -1	0	0x0000be00 - 0x0000be03 (0x4) IX[B]
	[26] -1	0	0x0000bf00 - 0x0000bf07 (0x8) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000ee0f (0x10) IX[B]
	[28] -1	0	0x0000ef00 - 0x0000ef0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]
	[30] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]
	[31] -1	0	0x0000f200 - 0x0000f203 (0x4) IX[B]
	[32] -1	0	0x0000f300 - 0x0000f307 (0x8) IX[B]
	[33] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[34] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[35] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[36] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]
	[37] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]
	[38] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]
	[39] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]
	[40] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[41] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[42] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[43] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[44] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[45] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x46000
(II) fglrx(0): [drm] mapped SAREA 0x46000 to 0xb7f43000
(II) fglrx(0): [drm] framebuffer handle = 0x47000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00048000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x0004c000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ie"
(**) Generic Keyboard: XkbLayout: "ie"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
SetClientVersion: 0 9
```

Thanks for any help given

EDIT: I got the ATI Driver working with 3d acceleration, steam games still crash back to the desktop with the same error

---

### Post by aoanla on 2007-11-12
Yes, - this may be a problem with recent versions of the ATI driver. I've certainly noticed that 8.42.3 is less stable with Wine than 8.41.7 was...

(So, try downgrading to 8.41.7 and see if that works, I suppose?)

---

### Post by Rafadagaffer on 2007-11-12
Ok I'll give that a try thanks

---

### Post by Melhisedek on 2007-11-12
I'm lurking here, can just say that I went through exact same problems :( Haven't downgraded to 8.41 yet though. Should upgrading to latest version of wine make it somewhat better?

---

### Post by aoanla on 2007-11-12
> **Melhisedek said:**
> I'm lurking here, can just say that I went through exact same problems :( Haven't downgraded to 8.41 yet though. Should upgrading to latest version of wine make it somewhat better?

Apparently, yes. There was a regression in <i>wine</i> for versions 0.9.46 and 0.9.47 which meant that those didn't like Source-engine games at all.

0.9.48 and 0.9.49 are increasingly back to (and surpassing) the quality of 0.9.45, though.

As far as the ATI drivers go, I've found that 8.40 and 8.41 are pretty good, and 8.42 is faster but horribly unstable with Wine. 

So, I'd go for Wine 0.9.49 and fglrx 8.41 or 8.40, personally.

---

### Post by Rafadagaffer on 2007-11-12
Ok downgraded to 8.40.2., glxinfo | grep render returns a yes, still get the same error as before :(.

I'm using the latest version of wine too

I copied my steam apps folder over from my vista partition, ill try download the games through wine see if that helps

---

### Post by Rafadagaffer on 2007-11-12
EDIT Double post:oops:

---

### Post by Rafadagaffer on 2007-11-12
Ok I downloaded the games again still no luck. I then went and searched the wine application database and found a fix for my problem.
I had to set the VideoMemorySize in the registry because wine couldnt detect my graphics cards memory, Heres how I did it

Open regedit, navigate to HKEY_CURRENT_USER>>Software>>Wine>>Direct3D. Create a new registry entry "VideoMemorySize" and then in the Data column add your video memory in mbs.

I can naviagate the ingame menus, change options etc, but as soon as I try to start a game/join a server, it locks up.

Im now getting the bug described here [http://bugs.winehq.org/show_bug.cgi?id=9878](http://bugs.winehq.org/show_bug.cgi?id=9878), I see there is a patch available which fixes the issue. This is the patch I'm talking about.

Code:

diff --git a/dlls/ntdll/heap.c b/dlls/ntdll/heap.c
index e6ba48c..9f26401 100644
--- a/dlls/ntdll/heap.c
+++ b/dlls/ntdll/heap.c
@@ -82,6 +82,8 @@ typedef struct tagARENA_FREE
 #define QUIET                  1           /* Suppress messages  */
 #define NOISY                  0           /* Report all errors  */
 
+#define ALIGN_PADDING          8
+
 /* minimum data size (without arenas) of an allocated block */
 /* make sure that it's larger than a free list entry */
 #define HEAP_MIN_DATA_SIZE    (2 * sizeof(struct list))
@@ -611,6 +613,13 @@ static SUBHEAP *HEAP_InitSubHeap( HEAP *heap, LPVOID address, DWORD flags,
         subheap->magic      = SUBHEAP_MAGIC;
         subheap->headerSize = ROUND_SIZE( sizeof(SUBHEAP) );
         list_add_head( &heap->subheap_list, &subheap->entry );
+
+        if (flags & HEAP_TESTALIGN)
+        {
+            subheap->headerSize += ALIGN_PADDING;
+            FIXME("aligning first block of subheap, first block will be at %p\n",
+                  (char*)subheap->base + subheap->headerSize + sizeof(ARENA_INUSE));
+        }
     }
     else
     {
@@ -727,7 +736,7 @@ static SUBHEAP *HEAP_CreateSubHeap( HEAP *heap, void *base, DWORD flags,
  * the requested size is committed.
  */
 static ARENA_FREE *HEAP_FindFreeBlock( HEAP *heap, SIZE_T size,
-                                       SUBHEAP **ppSubHeap )
+                                       SUBHEAP **ppSubHeap, ULONG flags )
 {
     SUBHEAP *subheap;
     struct list *ptr;
@@ -764,9 +773,13 @@ static ARENA_FREE *HEAP_FindFreeBlock( HEAP *heap, SIZE_T size,
      * get used, and a second free arena that might get assigned all remaining
      * free space in HEAP_ShrinkBlock() */
     total_size = size + ROUND_SIZE(sizeof(SUBHEAP)) + sizeof(ARENA_INUSE) + sizeof(ARENA_FREE);
+
+    if (flags & HEAP_TESTALIGN)
+        total_size += ALIGN_PADDING;
+
     if (total_size < size) return NULL;  /* overflow */
 
-    if (!(subheap = HEAP_CreateSubHeap( heap, NULL, heap->flags, total_size,
+    if (!(subheap = HEAP_CreateSubHeap( heap, NULL, heap->flags | flags, total_size,
                                         max( HEAP_DEF_SIZE, total_size ) )))
         return NULL;
 
@@ -1180,7 +1193,7 @@ PVOID WINAPI RtlAllocateHeap( HANDLE heap, ULONG flags, SIZE_T size )
     /* Validate the parameters */
 
     if (!heapPtr) return NULL;
-    flags &= HEAP_GENERATE_EXCEPTIONS | HEAP_NO_SERIALIZE | HEAP_ZERO_MEMORY;
+    flags &= HEAP_GENERATE_EXCEPTIONS | HEAP_NO_SERIALIZE | HEAP_ZERO_MEMORY | HEAP_TESTALIGN;
     flags |= heapPtr->flags;
     rounded_size = ROUND_SIZE(size);
     if (rounded_size < size)  /* overflow */
@@ -1193,7 +1206,7 @@ PVOID WINAPI RtlAllocateHeap( HANDLE heap, ULONG flags, SIZE_T size )
     if (!(flags & HEAP_NO_SERIALIZE)) RtlEnterCriticalSection( &heapPtr->critSection );
     /* Locate a suitable free block */
 
-    if (!(pArena = HEAP_FindFreeBlock( heapPtr, rounded_size, &subheap )))
+    if (!(pArena = HEAP_FindFreeBlock( heapPtr, rounded_size, &subheap, flags )))
     {
         TRACE("(%p,%08x,%08lx): returning NULL\n",
                   heap, flags, size  );
@@ -1379,7 +1392,7 @@ PVOID WINAPI RtlReAllocateHeap( HANDLE heap, ULONG flags, PVOID ptr, SIZE_T size
             SUBHEAP *newsubheap;
 
             if ((flags & HEAP_REALLOC_IN_PLACE_ONLY) ||
-                !(pNew = HEAP_FindFreeBlock( heapPtr, rounded_size, &newsubheap )))
+                !(pNew = HEAP_FindFreeBlock( heapPtr, rounded_size, &newsubheap, flags )))
             {
                 if (!(flags & HEAP_NO_SERIALIZE)) RtlLeaveCriticalSection( &heapPtr->critSection );
                 if (flags & HEAP_GENERATE_EXCEPTIONS) RtlRaiseStatus( STATUS_NO_MEMORY );
diff --git a/dlls/wined3d/device.c b/dlls/wined3d/device.c
index 056186c..f873aaf 100644
--- a/dlls/wined3d/device.c
+++ b/dlls/wined3d/device.c
@@ -311,7 +311,7 @@ static HRESULT WINAPI IWineD3DDeviceImpl_CreateVertexBuffer(IWineD3DDevice *ifac
     *ppVertexBuffer = (IWineD3DVertexBuffer *)object;
 
     if (Pool == WINED3DPOOL_DEFAULT ) { /* Allocate some system memory for now */
-        object->resource.allocatedMemory  = HeapAlloc(GetProcessHeap(), HEAP_ZERO_MEMORY, object->resource.size);
+        object->resource.allocatedMemory  = HeapAlloc(GetProcessHeap(), HEAP_ZERO_MEMORY | HEAP_TESTALIGN, object->resource.size);
     }
     object->fvf = FVF;
 
diff --git a/include/winnt.h b/include/winnt.h
index aecc2af..482ec31 100644
--- a/include/winnt.h
+++ b/include/winnt.h
@@ -676,6 +676,8 @@ WORD         WINAPI RtlQueryDepthSList(PSLIST_HEADER);
    FIXME: correct name */
 #define HEAP_SHARED                     0x04000000
 
+#define HEAP_TESTALIGN                  0x10000000
+
 typedef enum _HEAP_INFORMATION_CLASS {
     HeapCompatibilityInformation,
 } HEAP_INFORMATION_CLASS;

Could someone please tell me how to apply this patch. I know I have to download the source files and then compile them, but I dont know how to do compile source code or what to do with the patch itself. A Google search revealed very little for patching wine, neither did the wine website.

---

### Post by KillerJoe on 2007-11-13
No, I do not know how to apply this patch - another suggestion:

Do the same problems occur when running the games at different DZ levels? i.e. 70/81/90?

The heapsize command actually is another one:

-heapsize 524288

---

### Post by krak on 2007-11-14
> **Rafadagaffer said:**
> Ok just updated to Gutsy, the same thing happens but at least I get an error this time.

failed to lock vertex buffer in cmeshdx8

A quick google search reveals this occurs on Windows machines with the incorrect DirectX version.

Does wine even use DirectX:confused:, I wouldn't think so but better be sure

In steam set this launch options for your game

-windowed -width 640 -height 480 heapsize 2097152 -dxlevel 70

this has helped me my cs:s runs but still i get 20-30 fps
my card Radeon 9600Pro ;(

---

### Post by andrewoftheelves on 2007-12-26
i cant get steam to work at all under wine. i downloaded the steam installer (SteamInstall.msi) and when i run it + wine in the terminal i get this:
andrew@andrew-laptop:~$ wine SteamInstall.msi
wine: could not load L"Z:\\home\\andrew\\SteamInstall.msi": Bad EXE format for 
andrew@andrew-laptop:~$ 

is there any way to convert the .msi to .exe? any  help would be greatly appreciated.

nvm

---

### Post by bazooka on 2007-12-26
wine msiexec /i SteamInstall.msi

got from [here]("http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/")

---

### Post by ScottKidder on 2008-01-23
I'm having the same issue with Geforce 7600 GS. I ran CS 1.6 fine, just got CSS and Have played for almost an hour without having any crashes, then sometimes I get them almost 5 minutes in. After some searching I thought it might be a sound issue so  I switched to OSS and got no sound, and still crash, went back ALSA and crashed in 5 minutes. I'm going to try to dxlevel and see if I have any luck.

---

