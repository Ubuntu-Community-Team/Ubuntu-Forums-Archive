---
title: "AMD Catalyst driver freezes upon starting xserver"
date: 2007-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Progressive on 2007-12-30
I am running 64bit Kubuntu 7.10

Every time I try to install the binary AMD drivers, it freezes when starting X. It will usually show the cursor and the background, and promptly freeze within a few seconds. I can usually wiggle my mouse for those seconds, and after that, nothing. I can't go to console, and I have to completely restart in console mode.

For at least six months to a year, each version of catalyst/fglrx has had this same problem for me on 64 bit.

I remember vaguely someone else having this problem, and I don't know if I'm missing something obvious. I have followed various how-to guides and have used Envy, but all to no avail.

I am using the radeonhd driver right now, and I really like it. I would definitely prefer not to use the binary blob at all, but I very much crave video games. Also it would be nice to show off compiz and KDE4 compositing to people.

Please help. I don't want to install 32 bit, especially since my crappy x-fi soundcard wont even be badly supported under 32 bit.... it wont be supported at all.

---

### Post by AdamG51172 on 2007-12-30
I have always used the guide at The Unofficial Wiki for the ATI Linux Driver here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I am not exactly clear on what specific issue you are having, but would suggest double checking xorg.conf and if you have enabled the restricted drivers section in kcontrol.  For myself, I have not sucessfully used Envy, and KDE 4 left my system in a huge mess, but I do have the latest ATI binary 
and compiz works just fine.

---

### Post by soxs on 2007-12-30
May you plx add your xorg.conf aswell as your system specs.

note: X-fi soundcards, there is a alpha/beta driver out, but you have to compile a new kernel yourself. i'm sure I've seen a howto on ubuntuforums.org...

---

### Post by Progressive on 2007-12-30
> Section "Device"
	Identifier	"ATI RADEON X1800"
	Driver		"fglrx"
	BusID		"PCI:6:0:0"
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
EndSection

Section "Monitor"
	Identifier	"VX2025wm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X1800"
	Monitor		"VX2025wm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


standard stuff

My processor is an Intel Core 2 Duo, my card is a radeon x1800.

As for the Restricted Drivers Manager, it was unchecked because the fglrx version it uses is an older one. Don't worry, I did make sure to put the old one in the disabled modules list.

---

### Post by Progressive on 2007-12-30
It's fine everyone, I'm installing 32 bit now. Considering I don't do any tasks that benefit much from 64 bit, it should be fine. Besides, the original reason I installed it was for the x-fi driver, but it didn't even work. GAAAAAAAAHHHH I hate closed-source!!

---

