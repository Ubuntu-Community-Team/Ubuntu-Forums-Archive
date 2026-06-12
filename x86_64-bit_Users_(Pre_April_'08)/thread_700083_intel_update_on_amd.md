---
title: "intel update on amd?"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Grone1985 on 2008-02-18
Hi,
Didn't really knew where to post this but... here we go...

I am running Gutsy 64x on a Dell Inspiron 1501 with an AMD Turion 64x2 and a ATI graphic card and all of the sudden tonight I got this prompt for an update from the update manager that offered me this update:

[B]
xserver-xorg-video-intel[/B]
X.Org X server -- Intel i8xx, i9xx display driver
From version 2:2.1.1-0ubuntu9 to 2:2.1.1-0ubuntu9.1 (Size: 183 KB)

Description:
This package provides the driver for the Intel i8xx and i9xx family of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965 series chips.
This package also provides an XvMC (XVideo Motion Compensation) driver for the same chipsets.
More information about X.Org can be found at: <URL:http://www.X.org> <URL:http://xorg.freedesktop.org> <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
This package is built from the X.org xf86-video-intel driver module.


My questions... Should I be getting this update offered given that I don't have any Intel anything in my machine? Is there anything wrong with the update system that is sending me this update when I don't need it? or does the update have something that I do need from it even if I don't have Intel hardware on my computer?

Thanks

---

### Post by Jouke74 on 2008-02-18
I also got that. Same system : ATI X1600 card using FGLRX and AMD 4200 X2 processor. It might be a dependency for something, therefore I am not so sure whether you need it or not, namely this part is interesting: "This package also provides an XvMC (XVideo Motion Compensation) driver for the same chipsets."

---

### Post by Grone1985 on 2008-02-18
> **Jouke74 said:**
> I also got that. Same system : ATI X1600 card using FGLRX and AMD 4200 X2 processor. It might be a dependency for something, therefore I am not so sure whether you need it or not, namely this part is interesting: "This package also provides an XvMC (XVideo Motion Compensation) driver for the same chipsets."

Yeah... I was thinking the same thing, but it also says "for the same chipsets" so I'm not sure. I just won't install it for now and see if someone figures this out or we hear anything more official.

Cheers!

---

### Post by Yellow Pasque on 2008-02-18
The xorg-video-intel package comes installed by default on Ubuntu. The update won't affect anything if you're not using the "intel" video driver, so go ahead and install the update if you don't want to be bothered by it anymore. A more permanent solution would be to uninstall the xorg-video-intel package through Synaptic, but as someone said, make sure Synaptic doesn't want to uninstall important dependencies (like base gnome or X packages) before you go through with that.

---

### Post by Grone1985 on 2008-02-19
Is there a way to eliminate any sing of intel whatever from the system so it won't offer me updates for things that i won't ever need?

---

### Post by Yellow Pasque on 2008-02-19
> **Grone1985 said:**
> Is there a way to eliminate any sing of intel whatever from the system so it won't offer me updates for things that i won't ever need?
**A more permanent solution would be to uninstall the xorg-video-intel package through Synaptic**, but as someone said, make sure Synaptic doesn't want to uninstall important dependencies (like base gnome or X packages) before you go through with that.

---

### Post by tooferson5 on 2008-05-13
> **Temüjin said:**
> **A more permanent solution would be to uninstall the xorg-video-intel package through Synaptic**, but as someone said, make sure Synaptic doesn't want to uninstall important dependencies (like base gnome or X packages) before you go through with that.
Well when trying this synaptic is warning me that its dependencies, xserver-xorg-video-all would be removed too.  guess i will just be installing it then removing it unless someone else has an idea.

---

### Post by utUtu on 2008-05-14
> **tooferson5 said:**
> Well when trying this synaptic is warning me that its dependencies, xserver-xorg-video-all would be removed too.  guess i will just be installing it then removing it unless someone else has an idea.
It's safe to remove xserver-xorg-video-all. What's important in your case is the xserver-xorg-video-ati.

---

