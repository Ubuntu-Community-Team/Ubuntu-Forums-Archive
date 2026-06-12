---
title: "mouse stops working after suspend to ram"
date: 2006-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by sharkbird on 2006-01-24
Hello,

I have a g4 ibook on which I have installed ubuntu.  I am having a problem with the appletouch kernel module becoming unresponsive after I suspend to ram by closing the lid of the laptop.  When I resume, everything works except for the mouse.  I am using pbbuttons for the resume feature.

Thanks,

sharkbird

---

### Post by sharkbird on 2006-01-25
I figured out a workaround for this.  If anyone else comes across the same problem, here is what I did to re-enable the appletouch mouse after suspend (need to be root to run these):


modprobe -r appletouch
modprobe -r usbhid
modprobe -r ehci_hcd
modprobe -r ohci_hcd
modprobe  ohci_hcd
modprobe  ehci_hcd
modprobe  usbhid
modprobe appletouch


I put all of the commands into a bash shell script for easy execution.

sharkbird

---

### Post by callipeo on 2006-01-25
You may want to put those commands in a script under /etc/power/scripts.d/, so that pbbuttonsd can automatically execute it for you. See [http://ubuntuforums.org/showpost.php?p=624598&postcount=3](http://ubuntuforums.org/showpost.php?p=624598&postcount=3)

---

### Post by sharkbird on 2006-01-25
Thanks callipeo,

I was going to research how to do that this evening.  You have saved me some time.

sharkbird

---

