---
title: "Just setup AMD64 and SATA, hope it works"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by berlinbrown on 2005-10-18
I just setup the above, I hope it works ok.  Are there any issues?

---

### Post by Pablo_Escobar on 2005-10-18
Mine AMD64 and SATA drive work flawlessly. I installed 64bit Breezy without a fuss, but sadly had to revert to 32 Breezy - ATI drivers problems :(

---

### Post by berlinbrown on 2005-10-18
So, you can still use 32bit operating system, hmm; good to know.

---

### Post by arunsub on 2005-10-18
I had problem with installing 64 bit with SATA drive. I went back to 32 bit. When i tried to install 64 bit, the first set of installation went fine. The CD ecjected and i then rebooted. The second set of installation/startup after reboot hung after displaying the message "Starting hotplug subsystem <OK>". It didn't progress any further. I didn't have this problem with 32 bit. I had the same problem with 64 bit Hoary also (but it worked with PATA before I changed to SATA). I don't know if it's due to SATA or any USB drives connected to the system. I have 2 USB external hard drives connected, but both were off during installation (both 64 bit and 32 bit installation).

---

### Post by Septor on 2005-10-18
I had the hang at hotplug problem as well... I couldn't work around it, regardless of kernel parameters.  So I booted into my Gentoo partition, copied my good kernel to the yet-to-be-finished-installing Breezy partition, updated grub to use the gentoo kernel and rebooted... after that had no problems (I recommend a 2.6.13 kernel).  Find a bootdisk off the net with a 2.6.13 kernel, boot and copy it (and the kernel modules in /lib/modules/2.6.xxx). BTW, my system is a Shuttle ST20G5 (Radeon Xpress 200 chipset)... I suspect people with Radeon Xpress 200 chipsets are all having similar problems.

Good luck!

---

### Post by arunsub on 2005-10-19
[QUOTE=Septor]I had the hang at hotplug problem as well... I couldn't work around it, regardless of kernel parameters.  So I booted into my Gentoo partition, copied my good kernel to the yet-to-be-finished-installing Breezy partition, updated grub to use the gentoo kernel and rebooted... after that had no problems (I recommend a 2.6.13 kernel).  Find a bootdisk off the net with a 2.6.13 kernel, boot and copy it (and the kernel modules in /lib/modules/2.6.xxx). BTW, my system is a Shuttle ST20G5 (Radeon Xpress 200 chipset)... I suspect people with Radeon Xpress 200 chipsets are all having similar problems.

Good luck![/QUOTE]

I don't think it's worth doing those work arounds. I'll stay with 32bit as of now if there's no direct fix. :o

---

### Post by row1 on 2005-10-19
[QUOTE=Septor]I had the hang at hotplug problem as well... I couldn't work around it, regardless of kernel parameters.  So I booted into my Gentoo partition, copied my good kernel to the yet-to-be-finished-installing Breezy partition, updated grub to use the gentoo kernel and rebooted... after that had no problems (I recommend a 2.6.13 kernel).  Find a bootdisk off the net with a 2.6.13 kernel, boot and copy it (and the kernel modules in /lib/modules/2.6.xxx). BTW, my system is a Shuttle ST20G5 (Radeon Xpress 200 chipset)... I suspect people with Radeon Xpress 200 chipsets are all having similar problems.

Good luck![/QUOTE]
If you disable High Definition Audio in your BIOS you can get past the hotplug hanging.
Although in my ST20G5 i now get hanging while checking the battery state...

---

### Post by ikd69 on 2005-10-20
My amd64 and SATA 200 combo gave me the goosebumps twice at the same spot: when installing grub.  The first time I had to reinstall, then I tried to make both the /home and the / partitions smaller than 100GB.  The installation went smoothly. No more hiccups.  

I don't know if it has something to do with the size of the partitions, but whenever I tried to make either partition larger than 100G, I only got trouble.

IKD

---

