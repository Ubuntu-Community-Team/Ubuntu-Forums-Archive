---
title: "boot loader reinstall"
date: 2005-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by shomi on 2005-04-14
hello, 

I have ubuntu 64 and win 64 on my machine, 
at first, i installed win xp 32 and then ubuntu so that the boot loader would over-write the MBR. Then i got the win x64 and installed it but it over-writed the MBR so that i can't access linux any more, 

How do i reinstall ONLY the boot-loader ???

r there any problems known to anyone ??

cheers and thankx

---

### Post by devil28 on 2005-04-14
you can run any live cd, check if your /boot/grub/sources.list has your linux in it and if so, open console an d type: sudo update grub

---

### Post by shomi on 2005-04-14
no no ... my boot loader isn't even working now....
how do i completely reinstall it or any other one....

---

### Post by shomi on 2005-04-17
bump :(

---

### Post by maqi on 2005-04-17
A live CD is an option as stated above. 

You could also google and find a GRUB bootdisk to download and then google for rawwrite to write it from within windows. Then use the bootdisk to boot linux and then use the command (incorrectly) noted above:
```
sudo update-grub
sudo grub-install (hd0)
```
To restore your linux bootloader/MBR. The above command assumes that your MBR is located on hda or sda.

You will need to do a bit of reading perhaps, so that you know how to use the bootdisk and understand the GRUB numbering for disks - but if you know which partition linux is on you will definitely be able to boot it with one of these babies :)

maqi

---

### Post by shomi on 2005-04-17
thankx!!

---

