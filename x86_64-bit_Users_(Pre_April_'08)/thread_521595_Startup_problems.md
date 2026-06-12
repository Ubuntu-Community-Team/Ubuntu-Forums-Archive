---
title: "Startup problems"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thunderhit on 2007-08-09
Hi, gave ubuntu 32bit a try and now changed to 64bit. The first problem was already after the installation: there was a black screen, thats it. I get into the bootloader and select the non recovery kernel, see at the bottom "kernel alive kernel mapping (some numbers now) and then there is a new line of text at the top, but its too fast and the screen is black. Thought it might be problem with the gfx card (nvidia 8800gts) so I used the recovery mode and installed the latest version (100.14.11). Even so, after reboot, the problem is still there. This problem wasnt there with the 32bit version. Anyone where I have to check logs or any other tips?
To get ubuntu starting, I now start in recovery mode, "sudo init 3" and then see the nvidia screen and then the login, but I want to normally start!

---

### Post by John.Michael.Kane on 2007-08-09
> **Thunderhit said:**
> Hi, gave ubuntu 32bit a try and now changed to 64bit. The first problem was already after the installation: there was a black screen, thats it. I get into the bootloader and select the non recovery kernel, see at the bottom "kernel alive kernel mapping (some numbers now) and then there is a new line of text at the top, but its too fast and the screen is black. Thought it might be problem with the gfx card (nvidia 8800gts) so I used the recovery mode and installed the latest version (100.14.11). Even so, after reboot, the problem is still there. This problem wasnt there with the 32bit version. Anyone where I have to check logs or any other tips?
To get ubuntu starting, I now start in recovery mode, "sudo init 3" and then see the nvidia screen and then the login, but I want to normally start!

There is a couple things you can try.

1) letting the machine boot as normal, and it's finish, and your at the black screen you can try.

Pressing ctrl alt f1, and editing your xorg so that it uses vesa. to do that you would use the command below.
```
sudo nano /etc/X11/xorg.conf
```

The other option is to reinstall ubuntu applying the boot parameter listed (make sure to hit F6 first). 
```
nosplash noapic nolapic
```
note: do not remove any of the commands already shown in the boot line. just add the above commands to it

---

### Post by Thunderhit on 2007-08-09
And how do I tell it to use vesa? Like I wrote, I get into ubuntu and can login, so I can do changes like that without problems, but where to tell it to use vesa?
Wanted to copy/paste my file in here, but I cant select everything on the site... ctrl+a doesn't work to select everything.

---

### Post by John.Michael.Kane on 2007-08-09
> **Thunderhit said:**
> And how do I tell it to use vesa? Like I wrote, I get into ubuntu and can login, so I can do changes like that without problems, but where to tell it to use vesa?
Wanted to copy/paste my file in here, but I cant select everything on the site... ctrl+a doesn't work to select everything.

You would open your xorg config using nano. 

Then scroll down to
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"** change this to vesa**
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
```

Then ctrl x followed by ctrl m 

then you can try running the following command.
```
startx
```

Should this still not allow you to reach an ubuntu desktop your other option is to reinstall using the other method list in the above post.

---

