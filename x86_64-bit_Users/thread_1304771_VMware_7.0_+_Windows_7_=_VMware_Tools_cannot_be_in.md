---
title: "VMware 7.0 + Windows 7 = VMware Tools cannot be installed."
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by jackharvest on 2009-10-29
I saw this issue one other time on some forums elsewhere, but it was never solved. Granted, this deals strictly with VMware, but I figured I'd come to my favorite place to get an answer.

I'm running Linux Ubuntu x64 9.04 Jaunty. Installed the x64 version of VMware just fine, and installed a 32-bit version of Windows 7 perfectly.

However, when trying to install VMware tools from the "VM >> Install VMware Tools" menu - I get the following error:

" VMware Tools installation cannot be started manually while Easy Install is in progress. "

Granted, I DID end up using the easy install method for installing Windows 7, but I have never seen this issue before. Is there a way to force Easy Install "off" after the installation has completed? I'd love to get this fixed, since my video quality blows chunks without the VMware tools installed. heh

Thanks.

---

### Post by jackharvest on 2009-10-29
Solved my own problem after 3 hours of meddling. Seems it was the floppy drive settings.

My settings during issue:

Plugged in?: unchecked
Plugged in at startup?: unchecked

Use hardware device?:
no (unchecked)

Use image?:
yes (checked with some file name in there).

....

I changed the checkmark boxes to say "use hard ware device". EVEN THOUGH I have "plugged in" and "startup" both unchecked, it seems it was subconsciously effected by it.

Hope that helps somebody. Go ahead and close this.

---

