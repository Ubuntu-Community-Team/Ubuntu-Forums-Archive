---
title: "Not booting into Ubuntu (dual-boot with XP)"
date: 2005-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cynetix on 2005-06-17
Hello!

I have been wanting to get back into Linux so I may give myself one more feather in the ol' PC knowledge cap. After many comparisons (Red Hat, Mandrake (now Mandriva), etc.) I was convinced to go with Ubuntu. The install seemed to be pretty flawless and grub saw that I have XP Pro installed as well. It ejected the CD and then said it would reboot into Ubuntu to continue the installation process...

Didn't happen.  ](*,) 

PC boots into XP ok still so not a complete loss at this point.  I check my boot.ini just for grins, no new entries there and I have no grub boot menu when I restart the PC. 

I rebooted to the CD and checked via shell with fdisk -l and /dev/sdb1 contains Ubuntu and /dev/sdb5 contains the swap. Is there anything I can do manually to fix this? Any help will be truly appreciated.

Side note: I am using the AMD 64 version of Ubuntu and the install is on a SATA drive. 

Thanks in advance,
~C

---

### Post by jerrykenny on 2005-06-17
Are Ubuntu and XP on separate disks then ?

Maybe you've just installed grub onto the mbr of the second drive,   try changing your boot order in the bios to see if thats happened . . . .

---

### Post by Cynetix on 2005-06-17
[QUOTE=jerrykenny]Are Ubuntu and XP on separate disks then ?

Maybe you've just installed grub onto the mbr of the second drive,   try changing your boot order in the bios to see if thats happened . . . .[/QUOTE]


Thanks for the quick post! Yes, they are on seperate disks. XP is HD 0 and Ubuntu is HD 1 of the SATA controller. 

I'll give it a try but if that's the case, how do I fix this? I really don't want to swap them permanently.

---

### Post by Cynetix on 2005-06-17
No luck there. When I did that, it gives me "Error loading operating system."  :???:

---

### Post by Cynetix on 2005-06-19
Any ideas? Anyone?

---

### Post by estel on 2005-06-19
Do you have a boot disk of any sort?

---

### Post by Cynetix on 2005-06-19
I don't know how to make a Ubuntu boot disk from within Windows.

---

### Post by ::DoGG:: on 2005-06-21
the easiest way is to run any distro that have a live cd or just would give you a basic shell and install grub by hand on the mbr ( not sure, think it`s gub install /dev/hda1 or grub-install /dev/hda1). Then when you install grub you can try to boot into ubuntu or with the minimal shell-like grub commandline you are able to change the boot parameters so it`s way more easy to find the problem and eliminate it.

---

### Post by Anaqreon on 2005-06-21
[QUOTE=Cynetix]Hello!

I have been wanting to get back into Linux so I may give myself one more feather in the ol' PC knowledge cap. After many comparisons (Red Hat, Mandrake (now Mandriva), etc.) I was convinced to go with Ubuntu. The install seemed to be pretty flawless and grub saw that I have XP Pro installed as well. It ejected the CD and then said it would reboot into Ubuntu to continue the installation process...

Didn't happen.  ](*,) 

PC boots into XP ok still so not a complete loss at this point.  I check my boot.ini just for grins, no new entries there and I have no grub boot menu when I restart the PC. 

I rebooted to the CD and checked via shell with fdisk -l and /dev/sdb1 contains Ubuntu and /dev/sdb5 contains the swap. Is there anything I can do manually to fix this? Any help will be truly appreciated.

Side note: I am using the AMD 64 version of Ubuntu and the install is on a SATA drive. 

Thanks in advance,
~C[/QUOTE]
 Cynetix:

I had a similar problem installing Ubuntu. It ends up being easier to put Windows on the second hard drive. As we all know, Windows overwrites the MBR without warning, it seems, and I found it was easier to install Windows while it was hooked up as my first drive, and then put it as the second drive and install Ubuntu. 

Ubuntu will then put GRUB on the Linux drive's MBR and you are almost done! The last thing to do is add two lines to the "/boot/grub/menu.lst" to your Windows boot entry. Mine looks like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
savedefault
rootnoverify (hd1,0)
chainloader	+1
# The next two lines make Windows think it is the head-honcho first drive ;-)
map (hd0) (hd1)
map (hd1) (hd0)

The last two lines allow Windows to think it is the first hard drive in the system. I don't know why this should be necessary but there you have it.

I hope this helps. This was the first time I have every posted anything in a user forum before! If it helps you at all then I'll feel better about having relied on these kinds of forums for years :-)

Note: I use PATA hard disks, not SATA as it appears you do.

---

### Post by Cynetix on 2005-06-21
Your advice seems pretty sound but I think I'm done with this. I started out with Mandrake 10.1 (or Mandriva as it's called now) with the same results. I can't access the install because every premade Linux bootdisk I try using for access locks up during hardware detection. I can't use the shell from the CD because it doesn't see any partitions except temporary ones and the CD itself.

I now have Ubuntu on HD 0 and XP is on SD 1. Still no luck. I tried a boot commander and it didn't see the install of Ubuntu either.

I appreciate everyone's help but the hours I've spent on this, while educational, haven't proven fruitful, so I will probably stop trying. I don't have a spare PC to install it on for me to use. Thanks for your time. *Puts Advil bottle back in cabinet*

---

