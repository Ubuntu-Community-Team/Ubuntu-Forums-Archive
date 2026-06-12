---
title: "Video Problem: Mac AGP ATI Radeon 7000 32MB"
date: 2006-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by zpro on 2006-05-02
Got Ubuntu install on my Desktop Mac, however, there is a serius problem with video display of texts, its garbage.

did download all the updates, and restarted, however, there no-improvement,
in video quality.

note: running a LCD display as well: LCD1700v (NEC) MultiSync
ati radeon 7000 32MB AGP video card.

What needs to be fix? ( please note: newibe) on linux
coming from Mac OS X.



Thanks-
:-?

---

### Post by davygravy on 2006-05-02
can you be more specific?

can you use your desktop (.ie see files, etc on your desktop)?

do you mean that just text is garbled, or is everything garbled?

screenshot?

---

### Post by zpro on 2006-05-02
Yes, I can make out some characters, butit not as clear when typing.
but when moving anc clicking in other areas, makes the other screen clearer..
very odd.

right now, the smilies icons are missing part of there grahics, to the right of me,
when typing this reply.

---

### Post by davygravy on 2006-05-02
Is it a genuine **ATI** Radeon 7k, or a flashed AGP PC card?  

If that is the case, then it could be mildly overclocked, and this could cause some artifacting. (I have this problem just a *tiny* bit on some of the buttons in Firefox - no where else.  My card is a flashed ATI knock-off ( but a PCI version) - it say Radeon on it, but it was made by PowerColor.



It sounds like you can read text on your screen, but there is a clarity issue, right?  Did you try a CRT monitor?  Did you try lower resolutions (System>Preferences>Screen Resolutions )?

I can't remember how to lower the number of colors , the bit depth.  Anyone care to tell that?

---

### Post by zpro on 2006-05-02
I did notice some error messages, on start up, point to the video driver.
thinking the driver is not right, for the card.
FYI 1280 x 1024 @ 75Hz is normal for this LCD.

And no on the CRT.
](*,)

---

### Post by zpro on 2006-05-02
Just wanted to add, found on my laptop (PC) there where major problems on the net with this video board.

Here is a copy of my xorg.conf file.
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7200 (R100 QD)"
	Monitor		"NEC LCD1700V"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by zpro on 2006-05-02
ll, I found a nvida Gx2 card? and now my video is much better,
however, I still notice error message, with the startup of ubuntu
barking about the kernal no directory for driver.. something like that.
then another one about the pci 49.9056xxx can;t allocate resource..

Where would all this error be listed? ( want to make sure, there nothing else going wrong.)

TKS-
:neutral:

---

### Post by zpro on 2006-05-03
All is working since removing the ATI video card.
--
TKS

---

