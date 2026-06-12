---
title: "Problem installing 5.10 64bit"
date: 2005-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dr.Balagopal on 2005-12-14
Hi, I was using Ubuntu 5.04 64 bit as a multiboot with my Windows XP. In fact I had fallen in love with it. But yesterday I recieved my 5.10 64bit ship-it CD and was installing it after reformatting the drive in which 5.04 was present. The install proceeded as usual in the expert mode. I made a swap(2GB) and a \ . But on trying to install there was a bug and the whole system crashed. I had to recover my XP using FIXMBR. Tried many times in different ways but with no success.The whole process used to be flawless with 5.04 64 bit. Is the 5.01 64 bit ubuntu buggy? My configuration AMD 64 3200+,
Asus A8N Sli Deluxe motherboard,1 GB DDR RAM, Nvidia 6600 graphics card . Seagate Barracuda 200GB  SATA Hard disc,

---

### Post by tburns on 2005-12-14
[QUOTE=Dr.Balagopal]Hi, I was using Ubuntu 5.04 64 bit as a multiboot with my Windows XP. In fact I had fallen in love with it. But yesterday I recieved my 5.10 64bit ship-it CD and was installing it after reformatting the drive in which 5.04 was present. The install proceeded as usual in the expert mode. I made a swap(2GB) and a \ . But on trying to install there was a bug and the whole system crashed. I had to recover my XP using FIXMBR. Tried many times in different ways but with no success.The whole process used to be flawless with 5.04 64 bit. Is the 5.01 64 bit ubuntu buggy? My configuration AMD 64 3200+,
Asus A8N Sli Deluxe motherboard,1 GB DDR RAM, Nvidia 6600 graphics card . Seagate Barracuda 200GB  SATA Hard disc,[/QUOTE]


Every time I have installed it, it has been fine. Are you using the partitioner included with the installer? Also make sure root directory is /.

---

### Post by Hoop on 2005-12-15
I always have trouble installing any linux , but find I can load any linux by starting with the base system and then building it up. I also install grub to floppy disk, you can do this on ubuntu. When it asks 'Do you want to install Grub to Boot Drive' say no. It will then ask where you want to install grub ? Use (fd0) including brackets. Then set your bios boot order to 1. floppy 2. Hard Drive and anytime you want to boot grub you can put the floppy in. When grub installs to the MBR it only installs a pointer to your /boot partition anyway. This also has the added advantage of not putting your Windows drive at risk. If anything goes wrong just remove floppy and you'll boot straight to windows. A good tip is to install ubuntu base system by typing server at the install prompt and complete installation. Then apt-get install x-window-system-core .Now edit xorg.conf to suit. Edit /etc/apt/sources.list . Remove rem('#')   marks from 'deb' statements. You can then 'apt-get install gnome'. then reboot. You will have a basic system with gdm and gnome desktop installed and set-up for you. You won't have all the packages that ubuntu includes in its distro but you can add the ones you want, you'll also be missing some lib files which you can add to suit your requirements. Use synaptic is easiest. If you want all the packages and lib files of the stansard distro then  you can get them with 'aptitude -y install ubuntu-standard ubuntu-desktop' as listed in the manual on your install cd.

Hope this helps. Have fun.

---

### Post by Totzo on 2005-12-15
I have a 64bit athlon cpu and didn't notice any improvement in performance using the 64bit system over the 386 version, however, I did notice a lack of usability with it (flash, gaming etc), don't see the point really.

---

### Post by MighMoS on 2005-12-15
[QUOTE=Dr.Balagopal]I made a swap(2GB) and a \ .[/QUOTE]
You said you did the this in expert mode, something I haven't done before, so I'm not sure if this applies, but make sure that your room partition is "/" (forward slash) and not "\" (a backslash).  If you manually put in a backslash ("\"), then that may have caused the installer to fail.  Backslashes are used only on Microsoft Windows.

---

### Post by nortoncillo on 2005-12-16
in expert/sever installation you must load some extra modules, to detect LAN, PCI, and more....

are you sure you load those "extra modules", i've installed warty, Hoary and breezy, and never have a problem, but i've loaded the extra modules.....

---

### Post by cochingeek on 2006-01-06
well I managed to install over a vitual machine and the problem is solved

---

