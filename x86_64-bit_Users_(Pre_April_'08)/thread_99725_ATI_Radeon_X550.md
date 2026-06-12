---
title: "ATI Radeon X550"
date: 2005-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by rengens on 2005-12-06
Hi

I am using <title> and I have a problem with drivers. Could anybody help me?
Tried fglrx and Ati drivers, XOrg can not be started.
Can't be that vesa is the only option, can it?

I am beginer on linux...

Thank you indeed

---

### Post by korakde on 2005-12-08
Welcome to the gang of ATI sufferers. I've got a thread going at [http://www.ubuntuforums.org/showthread.php?t=95776](http://www.ubuntuforums.org/showthread.php?t=95776) dealing with a similar problem. Hope we find a solution soon. I don't even know how I'll load Linux on the Hard disk with this problem of Xserver.

---

### Post by aok on 2005-12-09
I also have an AMD-64 and the X550. I have the instructions on my work PC (which is running Breezy) so hopefully I'll remember tomorrow and post the instructions here. Although, I basically waded through one of the previous threads and picked and choosed what made sense.

---

### Post by aok on 2005-12-09
Please look at this thread since that's essentially what I did and I think it's where I got my instructions: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

Since I already pasted what I had saved, I'll just leave it below:

---

I am running the AMD-64 Breezy port with the ATI x550 running dual-head.

I did this twice, the first time I did it from booting up into the Recovery mode so it was text-mode console only. The second time, I think I was using an older set of drivers...but not the default detected one from Ubuntu since that one would cause me to lock up while logging in.

[LIST=1]
[*]sudo sh ./ati-driver-installer-8.19.10-i386.run --buildpkg Ubuntu/breezy
[*]sudo dpkg -i fglrx-control_8.19.10-1_i386.deb
[*]sudo dpkg -i fglrx-kernel-source_8.19.10-1_i386.deb
[*]sudo dpkg -i xorg-driver-fglrx_8.19.10-1_i386.deb
[*]sudo module-assistant prepare
[*]sudo module-assistant update
[*]sudo module-assistant a-i fglrx
[*]sudo aticonfig --initial
[*]sudo cp /usr/X11R6/lib/modules/extensions/libdri.a libdri.a.old
[*]sudo cp libdri.a /usr/X11R6/lib/modules/extensions/
[*]fglrxinfo
[/LIST]

---

### Post by Ferrat on 2005-12-09
x550 is that a PCI-E?? 
I have a x850 (AGP) and I haven't had any trubbles getting it started

---

### Post by aok on 2005-12-09
Yep, PCI-Express

---

### Post by Ferrat on 2005-12-09
Hmm ok guessing that's the problem then, should be a "simple" change of the portmapping in the xorg.conf because guessing the problem is that X doesn't find the card. 

On my Win part now and I'm just freebasing with ideas

First locate the /dev that is your PCI-E card (should be able to find 

Setup X with the standard ATi drivers then do a 

**$ sudo gedit ./xorg.conf**

-----FIND THIS PART
```

# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    [COLOR="Blue"]Option "UseInternalAGPGART"         "yes"[/COLOR]
    Option "ForceGenericCPU"            "no"
    [COLOR="Red"]**BusID "PCI:1:0:0"    # vendor=1002, device=514c**[/COLOR]
    Screen 0
EndSection

```

The bold red part is the part that I belive needs to be changed to point at the right PCI-E port and the card there. (The blue line might also need to be changed, I think since it says USE AGP ^^)

This is just a general knowhow stab in the dark, but might help you guys out :)

(If the code looks different to to you guys on your machines please post them)

---

### Post by rengens on 2005-12-12
Cant write PCI-E there can I? What should be written over there? Thanks a lot guys

---

