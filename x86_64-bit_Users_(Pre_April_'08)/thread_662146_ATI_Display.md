---
title: "ATI Display"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Origin on 2008-01-08
I downloaded and installed ATI drivers from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) and after I logged out and back in, my widescreen ( 1280x768 ) became 1024x768, and there's no way to change it back. /etc/X11/xorg.conf still has 1280, so what's going on?

1. Can I somehow force the width to be 1280 px? (It's not an option in screen resolutions--why not?)
2. Otherwise, can I just undo what I installed, and go back to what it was before?

Thanks a lot.

According to lspci:

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

---

### Post by tormentum on 2008-01-09
I've got the same issue here.  I've tried getting the resolution back to the native 1280x768, but it wont take.

---

### Post by zipperback on 2008-01-09
Reinstall the restricted ATI driver from the ubuntu repositories using synaptic.

- zipperback
:popcorn:

---

### Post by dr_liu on 2008-01-09
> **zipperback said:**
> Reinstall the restricted ATI driver from the ubuntu repositories using synaptic.

- zipperback
:popcorn:

But this driver doesnot provide any Desktop Effect with my ATI xpress 1250 Graphic card

---

### Post by homerhomer on 2008-01-09
Short short answer:
The ATI driver on threre website doesn't work with widescreen. 

I hope that there next driver will, since i have the same issue with my lappy

Easiest and best solution (my opinion) is to use the one from the Ubuntu repositories
or
you can install 7.11, which works with widescreen and compiz, but has other beta like issues like 7.12

The good news is that ATI have been pretty good about releasing a driver every month
and
The open source driver is getting better everyday ( not quite there yet though )

later

---

### Post by tormentum on 2008-01-09
i'll try the previous version and report back.

My big problem is the restricted repos drivers that come with ubuntu cause World of Warcraft to hang when starting.  I've tried the most recent, and they work, but don't give me the native resolution of my LCD.

Updates to come.

---

