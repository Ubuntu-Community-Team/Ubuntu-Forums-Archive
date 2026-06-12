---
title: "which graphics card should i buy ?"
date: 2009-05-21
forum: x86 64-bit Users
---

### Post by geoff.l on 2009-05-21
I have ubuntu 9.04 64bit on an AMD dual core with on-board ATI HD 3200 graphics adapter.

Having wasted hours trying every trick in the book I'm ready to give up on the HD 3200 and buy a separate video card.  My major issue is with 2D performance, 3D is not really important to me, I don't do games, but I move a lot of windows around the screen and the 2D perf is miserable compared to older ubuntus on older hardware.   The best I can get is with the fglrx driver and Xv overlay,  but it's still depressing.  Interestingly running windows under virtualbox actually seems snappier that the ubuntu host.  Amazing!

So ... impossible question I know ... but does anyone have a recommendation?  NVIDIA/ATI/whatever,  who has something that really works well with jaunty in 2D ?  And what drivers are you using ?

---

### Post by googlegot on 2009-05-21
I would purchase an NVIDIA 7300/8300/9300 if you are not worried about graphics performance, though I would suggest the 9300 over the others, just in case NVIDIA drops support for their older cards in the near future.

NVIDIA cards seem to be the best supported out of the manufacturers I have had experience with.

---

### Post by pixel :-) on 2009-05-21
What ever you do, DO NOT BUY AMD/ATI

---

### Post by konqueror7 on 2009-05-21
most nvidia cards will do, it got driver support from nvidia itself already...

---

### Post by Gen2ly on 2009-05-21
Yeah, you're not gonna need a powerhouse of a graphic card for 2D so save yourself some dough and get a third or fourth generation old card.  I use an nvidia one but ATI is good too.  I'd recommend going to newegg and look at their deal section in video-cards.

---

### Post by Arup on 2009-05-22
I understand your peril, I just had to buy a stop gap cheap nvidia 8400GS as my 4850 dual GPU ATI had horrid performance even with their latest drivers.

---

### Post by majamba on 2009-05-22
nvidia my friend had problems with ati card and boxee

---

### Post by grege on 2009-05-22
Just keep using the onboard ATI, just configure it right. I have a Gigabyte MA78GM-S2H and I use it to drive a TV so 3d effects are not wanted anyway.

Do not install fglrx, use the open source ati driver. The trick is to edit xorg.conf to get 2d working properly. If you have installed fglrx make sure you uninstall through Synaptic to clear out all the symlinks it creates.

so

sudo gedit /etc/xorg.conf

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
    Option   "AccelMethod"  "exa"
    Option    "DRI"  "on"
EndSection

I don't think the DRI line is necessary, I was experimenting with trying to get 3d working, however that is what my xorg.conf says and it works.

Restart after editing the xorg.conf

xv-video acceleration works well with no tearing, my system drives a Samsung 32" LCD TV through the vga connector at 1360x768 at 60hz. Power management also works with things sleeping and waking as required. 2d is as fast as any system.

This will only work with Jaunty, earlier Ubuntus have earlier xorg-ati drivers that will not work with newer chipsets. Also make sure you do your updates.

A cheap Nvidia 8400GS will also work, but as you only want 2d it would be a waste of money.

good luck

---

