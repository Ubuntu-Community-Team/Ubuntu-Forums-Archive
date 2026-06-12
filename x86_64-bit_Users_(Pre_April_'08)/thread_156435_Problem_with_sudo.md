---
title: "Problem with sudo"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by zjwagner on 2006-04-07
I'm a linux noobie and I cannot get sudo or gksudo to work for editing some readonly config files.  The specific file in this case is: /boot/grub/menu.lst.  The way i have tried so far is:

gksudo gedit /boot/grub/menu.lst
sudo gedit /boot/grub/menu.lst

and i have tried

gksudo chmod ugo+w /boot/grub/menu.lst
sudo "   "  

I cant even get gedit to launch when sudo is in front of it, for example

gksudo gedit or
sudo gedit

I dont know whats wrong, other things that require admin permissions dont work either like changin some preferences.  For example i cannot access the windows partion from linux nor can i configure my ethernet adapter, which was working before.  The "configure" button is grayed out, so internet from linux is impossible as well.

Any help would be appreicated.  My specs are:

HP Pavilion zv6000
AMD64 4000+
Ati radion xpress 200M (128 mb)
512 mb memory
80 gig HD with 60 gig winxp partition and 20 gig ubuntu (64bit)

---

### Post by codejunkie on 2006-04-07
[QUOTE=zjwagner]I'm a linux noobie and I cannot get sudo or gksudo to work for editing some readonly config files.  The specific file in this case is: /boot/grub/menu.lst.  The way i have tried so far is:

gksudo gedit /boot/grub/menu.lst
sudo gedit /boot/grub/menu.lst

and i have tried

gksudo chmod ugo+w /boot/grub/menu.lst
sudo "   "  

I cant even get gedit to launch when sudo is in front of it, for example

gksudo gedit or
sudo gedit

I dont know whats wrong, other things that require admin permissions dont work either like changin some preferences.  For example i cannot access the windows partion from linux nor can i configure my ethernet adapter, which was working before.  The "configure" button is grayed out, so internet from linux is impossible as well.

Any help would be appreicated.  My specs are:

HP Pavilion zv6000
AMD64 4000+
Ati radion xpress 200M (128 mb)
512 mb memory
80 gig HD with 60 gig winxp partition and 20 gig ubuntu (64bit)[/QUOTE]
I'm guessing you chose expert install, when installing ubuntu. but even if you didn't and sudo isn't working, this [**[COLOR="Red"]Post[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=841225&postcount=12")  should help you get sudo working.

---

### Post by zjwagner on 2006-04-07
Cool, works fine now thanks a lot.

---

