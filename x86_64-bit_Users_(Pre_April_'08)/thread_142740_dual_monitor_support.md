---
title: "dual monitor support?"
date: 2006-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by blech on 2006-03-11
Hi,

Can anyone give me tips on dual monitor support? I haven't seen anything in the ubuntu guide's. something to do with x11's xorg.cnfg 

thanks.

---

### Post by ssam on 2006-03-11
if you are using an ATI card then [Dual Monitors G4 ti-book]("http://ubuntuforums.org/showthread.php?t=140598") may help. it is writen asuming that you know how to make a back up of your old /etc/X11/xorg.conf and how to edit system files. if thats not the case let us know and someone can help you through it.

---

### Post by pstracha on 2006-03-13
Just got this working for my ATI Radeon 9600 \\:D/  so I thought I'd share with you my xorg.conf settings. Also, I tried to follow the instructions that ssam links to (and for the most part I did follow them almost exactly) but I had to make some minor changes to make it work for my system. The differences appear in the (primary) Device,  ServerFlags, and ServerLayout sections.

By the way, you're correct in that you should only need to modify X11's xorg.conf file.

This is what worked for me ...
[B]
Device Section:[/B]

```
Section "Device"
	Identifier 	"ATI Radeon 9600 (Primary)"
	Driver		"radeon"
	BusID 		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"ATI Radeon 9600 (Secondary)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"	#same as primary, b/c same card
	Screen		1
EndSection
```

**Monitor Section:**

```
Section "Monitor"
	Identifier	"SyncMaster (Primary)"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"SyncMaster (Secondary)"
	Option		"DPMS"
EndSection

```

**Screen Section:**

```
Section "Screen"
	Identifier 	"Primary Screen"
	Device		"ATI Radeon 9600 (Primary)"
	Monitor		"SyncMaster (Primary)"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Screen"
        Device          "ATI Radeon 9600 (Secondary)"
        Monitor         "SyncMaster (Secondary)"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection
```

**ServerFlags Section (needed to add this section):**

```
Section "ServerFlags"
	Option	"Xinerama" "ON"
EndSection
```

**ServerLayout Section:**

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Primary Screen" 0 0
	Screen 1	"Secondary Screen" LeftOf "Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

Good Luck!

---

### Post by blech on 2006-03-15
[QUOTE=pstracha]Just got this working for my ATI Radeon 9600 \\:D/  so I thought I'd share with you my xorg.conf settings. Also, I tried to follow the instructions that ssam links to (and for the most part I did follow them almost exactly) but I had to make some minor changes to make it work for my system. The differences appear in the (primary) Device,  ServerFlags, and ServerLayout sections.

By the way, you're correct in that you should only need to modify X11's xorg.conf file.

This is what worked for me ...
[B]
Device Section:[/B]

```
Section "Device"
	Identifier 	"ATI Radeon 9600 (Primary)"
	Driver		"radeon"
	BusID 		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"ATI Radeon 9600 (Secondary)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"	#same as primary, b/c same card
	Screen		1
EndSection
```

**Monitor Section:**

```
Section "Monitor"
	Identifier	"SyncMaster (Primary)"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"SyncMaster (Secondary)"
	Option		"DPMS"
EndSection

```

**Screen Section:**

```
Section "Screen"
	Identifier 	"Primary Screen"
	Device		"ATI Radeon 9600 (Primary)"
	Monitor		"SyncMaster (Primary)"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Screen"
        Device          "ATI Radeon 9600 (Secondary)"
        Monitor         "SyncMaster (Secondary)"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection
```

**ServerFlags Section (needed to add this section):**

```
Section "ServerFlags"
	Option	"Xinerama" "ON"
EndSection
```

**ServerLayout Section:**

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Primary Screen" 0 0
	Screen 1	"Secondary Screen" LeftOf "Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

Good Luck![/QUOTE]

my card is nvidia GeForce FX Go5200. can i still copy your xorg.conf and just change the ATI info to nvidia info?

---

### Post by thegnark on 2006-03-17
This setup (srota) works. I get a single wide display (the mouse can move from one screne to another), but the content iteslf (sans mouse) is mirrored.

Any ideas?

---

### Post by hentaidan on 2006-03-18
Managed to get mirroring working on my iBook G4 (Breezy, Radeon 9550). Followed the mergefb link, but needed to comment out [Option “UseFBDev” “true”], else nothing shows up.

My xorg.conf is over at [http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/]("http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/")

Had a go at merging, but only the mouse was moving across the screen, and the desktop right click menu was appearing on the lappy screen. I'll post here if I get it working.

Dan

---

### Post by hentaidan on 2006-03-18
Quicker than I expected :)

Just adding
```
Option          "CRT2Position" "LeftOf"
```

to the primary device section seems to work. I.E:

```
Section "Device"
        Identifier      "ATI Radeon 9600 (Primary)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Option          "MergedFB" "true"
        Option          "MetaModes" "1280x854 1280x854-1280x1024"
        Option          "MergedDPI" "100 100"
        Option          "CRT2Position" "LeftOf"
EndSection
```

So UseFBDev was causing my troubles at least.

A bit of googling turns up this:
> Option "UseFBDev" "boolean"
    Enable or disable use of an OS-specific framebuffer device interface (which is not supported on all OSs). **MergedFB does not work when this option is in use.** See fbdevhw(4x) for further information.
    The default is off. 

Edit:
Cloning and merging is working fine, except for VLC movies. The movie only shows up on the laptop screen in clone mode, but is fine in merged.

---

