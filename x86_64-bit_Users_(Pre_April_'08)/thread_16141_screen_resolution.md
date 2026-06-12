---
title: "screen resolution"
date: 2005-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by pwe on 2005-02-19
Hello!

I have the newest hoary, nvidia pci-e card and it works:) 
but:
1. i have only 1280x1024 screen resolution. in my xorg.conf is: 

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

what is wrong?? 

2. why isnt 'sudo' working on startup? i do "su" "password" what is normally but only in the other systems:)

thanks!

---

### Post by grj on 2005-02-19
To get to a root window you can click
Applications->System Tools->Root Terminal
When asked for a password enter your user password(not a root password)
or
in a terminal window type
sudo su
When prompted for a password enter your user password.

Once you are in a terminal window edit 
Modes "1024x768" "800x600" "640x480" to
Modes "1280x1024" "1024x768" "800x600"

Then restart X.

---

