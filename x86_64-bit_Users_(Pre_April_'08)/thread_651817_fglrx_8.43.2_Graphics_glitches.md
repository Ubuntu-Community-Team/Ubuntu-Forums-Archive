---
title: "fglrx 8.43.2 Graphics glitches"
date: 2007-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by sullenx on 2007-12-28
I am using fesity fawn and the latest ATI drivers (fglrx 8.43.2) I'm experiencing graphical glitches when i move my mouse and on the right bottom conner of my screen. When i restart the X server they go away but appears later.  Anyone has a clue? 

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.7059 Release

---

### Post by pay on 2007-12-28
Try updating to fglrx 8.44.3. They shifted to a new codebase so the driver isn't as tested as the old one so theres bound to be a few problems for the next couple of months.

---

### Post by sloggerkhan on 2007-12-28
My computer sometimes gets the same problem with the same driver. It was in the 8.42 release also.

I think it's just a bug, but what is weird is that the graphic glitch doesn't show up in screen shots.

Anycase, I don't know if it happens in 8.44.x 'cause that version doesn't support widescreen so I'm not about to use it.

As a side note, it seems to appear when i'm using a dual monitor layout way more often then when using only 1 screen.

---

### Post by Yellow Pasque on 2007-12-28
There's a way to prevent the corruption glitch that someone told me about. Something like "NoOffscreenPixmaps" or such in your xorg.conf file.

Also, users are reporting that the 8.44 driver does do widescreen if you set it to a lower resolution in the Catalyst Control Center first, and then set it to 1680x1050 or whatever you fancy.

---

### Post by SorinN on 2008-01-18
NoOffscreenPixmaps OR XAANoOffscreenPixmaps will solve the problem

The question is WHY xorg.conf is not writted OK when fglrx is installed ...

so check for those things on your /etc/X11/xorg.conf

////////////////////////////////////////

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option "XAANoOffscreenPixmaps" "true"
	Option "HWCursor" "On"
	Option "DRI" "true"
	Option "VideoOverlay" "on"
	Option "TexturedVideo" "on"
	Option "RenderAccel" "true"
	Option "AllowGLXWithComposite" "true"
	Option "OpenGLOverlay" "off"
	Option "CapabilitiesEx" "0x00000000"
	Option "no_accel" "no"
	Option "mtrr" "off"
	Option "KernelModuleParm" "locked-userpages=0"
	Option "BlockSignalsOnLock" "on"
	Option "UseFastTLS" "0"
EndSection

////////////////////////////////////////////

When I put all lines on my xorg.conf I say Bye Bye to glitches

Hope this will help you too

SorinN

---

### Post by sloggerkhan on 2008-01-18
Can you tell me what each option does or where I can find out? Thanks.

---

### Post by aypnia on 2008-01-18
Guys 8.45.4 drivers are out and are solving the desktop artifacts go get them from ati-amd

---

### Post by sloggerkhan on 2008-01-18
Have already. But I still wonder the explicit effect of those options.

---

### Post by cadavari on 2008-01-19
Just added this to my xorg.conf. Appears to work. Time will tell...so if I don't reply to this post, it means this works! Thanks for the solution

---

### Post by XplOzIOn on 2008-01-22
So this working?

Hope it its! SOLVED then

---

