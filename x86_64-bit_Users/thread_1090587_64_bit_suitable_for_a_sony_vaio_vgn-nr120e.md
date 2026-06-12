---
title: "64 bit suitable for a sony vaio vgn-nr120e?"
date: 2009-03-08
forum: x86 64-bit Users
---

### Post by tomasaur on 2009-03-08
Brand spanking newbie to Ubuntu here..
.
I bought my sweetie a used sony vaio vgn-nr120e laptop and am trying out linux on it.  She and I have been very frustrated with her old windows xp box and we both love my macbook.  So, not having the resources to buy another mac, and to satisfy my curiosity about the linux experience, I picked up this laptop cheap.  I have a few questions about using the 32 vs 64 bit distros on this machine.

First, I have the 64 bit distro of ubuntu 8.10 installed on the machine now and am using it for this message, so clearly it will install.  The question really is, should I be using this or the 32 bit version?

Second, this machine can only accept (it says) 2 gb ram.  I understand from other threads that one of the primary advantages of the 64 bit distro is the ability to access >3gb ram.  If this isn't an issue for me, are there any performance advantages to going to the 32 bit version?  She will be using this machine primarily for simple photo processing (resizing, cropping and such) as well as word processing and browsing.

Third, and this may be suitable for a 2nd thread, is the issue of the wireless card.  I can get the wireless card to run using the instructions posted here [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html) but each time I shut down or hibernate, I have to go through the whole "make install" "make unload" "make load" process again.  That can't be right.  Any suggestions as to how to get this puppy to retain its recognition of my card would be most appreciated.  

Thanks,
Tom

---

### Post by marcelkoopman on 2009-03-08
I would keep the 64 bit version. Much better than i386. 
I dont know what you mean by the wireless card problem (i'm guessing you are plugging it in or something?)
Maybe run an update and see if this problem still persists.

---

### Post by Chibone on 2009-03-08
Keep 64-bit - your hardware is utilized better.

Second, if it's 64-bit capable, it likely can support more RAM than 2 GB.  The 2 GB limit might be a 32 bit OS limit.

Did you try the first method for wireless on that page or the second?  

You might want to edit the file /etc/modules and add "ath5k" to the list so it loads on startup. 

Also edit /etc/default/acpi-support and add "ath5k" on the MODULES line so it looks like " MODULES="ath5k" " (this is so it will unload when hibernating and reload when resuming)

---

### Post by tomasaur on 2009-03-08
> **Chibone said:**
> Keep 64-bit - your hardware is utilized better.

Did you try the first method for wireless on that page or the second?  

You might want to edit the file /etc/modules and add "ath5k" to the list so it loads on startup. 

Also edit /etc/default/acpi-support and add "ath5k" on the MODULES line so it looks like " MODULES="ath5k" " (this is so it will unload when hibernating and reload when resuming)

Thanks for the speedy replies folks.  

I used the first method.  This leaves me with the folder that I downloaded and unpacked on my desktop.  

Do I need to place any module files (is there such a thing?) from the downloaded folder (compat-wireless-2009-03-08 ) in a particular location?  I've gotten used to installation programs in Windows moving things around for me, or simply placing applications in the Applications folder on my mac.

---

### Post by Yellow Pasque on 2009-03-09
> **Chibone said:**
> Also edit /etc/default/acpi-support and add "ath5k" on the MODULES line so it looks like " MODULES="ath5k" " (this is so it will unload when hibernating and reload when resuming)
I don't know if that will work. Ubuntu 8.10 will use dbus (instead of acpi) to suspend by default, rendering that option useless. I would suggest looking in the BIOS to see if there are any power management options for the wireless card. Also, consider trying the "madwifi" driver method.

BTW, Photoshop/GIMP is one of the applications that benefits from the use of 64-bit CPU registers/instructions.

---

