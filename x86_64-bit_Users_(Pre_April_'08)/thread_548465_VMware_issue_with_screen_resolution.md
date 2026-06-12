---
title: "VMware issue with screen resolution"
date: 2007-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Christobevii3 on 2007-09-11
I run ubuntu x86-64 with windows xp 32 bit inside it.  My laptop runs 1280x800 but for some reason vmware won't see this for windows xp and let me run it.  Is there a problem with vmware reading my ubuntu config for 1280x800 or is this an xp/vmware limitation?

---

### Post by overkillm on 2007-09-11
Do you have VMWare Tools installed?  It improves things like video performance and mouse synchronization.  I wasn't able to get my usual resolution in VMWare until I installed that.

---

### Post by Christobevii3 on 2007-09-11
Yes I do have vmware tools installed

---

### Post by Mariano Oliveto on 2007-11-15
Something similar happened to me. What I did was, within Windows XP opened in VMWare Server I uninstalled VMWare Tools and removed the video card device from the control panel.

Then I rebooted (or not, I can't remember exactly if I did) and reinstalled VMWare Tools using the menu VM -> Install VMWare Tools in VMWare Server (while you are running your WinXP Virtual Machine).

Then what did the trick was that I followed this instructions: [http://ubuntuforums.org/showthread.php?t=300968&highlight=VMWare+resolution](http://ubuntuforums.org/showthread.php?t=300968&highlight=VMWare+resolution)

but in "View" I only selected "Autofit Guest" and not  "Autofit window" and "Autofit Guest" as the instruction said.

I hope this helps you!

---

