---
title: "Matrox g650 driver"
date: 2005-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by bitsmith on 2005-05-12
hi,

i'm new to ubuntu. just installed on a new amd-64 3200 cpu with a matrox g650 dual-dvi video card and a samsung 910T lcd (dvi, 25ms refresh). i'm disappointed with the video quality -- especially, when i move windows around, it leaves a trail. 

by default, my xorg.conf uses a "vesa" driver (please see below). i found a link to 
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) which mentions a beta driver for the matrox g650, but it is unavailable for amd-64.

does anybody have advice on how i can improve the performance of my current setup. if not, can anybody recommend a sub $150 video card setup (possibly using two identical video cards, with one being pci) that will definitely support dual monitors (both dvi inputs). i am not a gamer, but would like to play dvd with high quality.

thank you.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

---

### Post by JonahRowley on 2005-05-12
I use a G450, though not on 64-bit.  Did you check Matrox's site?  They have Linux drivers for all their recent cards, and in my experience, they're decent.  I think the problem here might be 64-bit though, is everything running in native 64-bit mode?  And if so, is a 32-bit module going to work with a 64-bit X?

---

### Post by FluffyElmo on 2005-05-12
Your best bet for information is probably the Matrox Linux support forum here:
[http://forum.matrox.com/mga/viewforum.php?f=2](http://forum.matrox.com/mga/viewforum.php?f=2)

At the moment, I don't think they have a 64bit Linux driver for your card. They just came out with a 64bit Windows driver though so that may change. XIG also makes a 3rd party commercial driver for it, you might want to check if it will do what you want before investing in more hardware. 

Otherwise, you can get a Nvidea 6600GT with dual DVI outputs for ~$150-$175US. They have a 64bit Linux driver that supports dual-head. Myself I have a G400, and will probably upgrade to the 6600GT in the near future.

---

### Post by Gunmarster on 2007-05-31
i have tryed to play fable but it said that my video card were not matching the minnium requirements for the game.

in use matrox millenium G550./

what shall i do

---

