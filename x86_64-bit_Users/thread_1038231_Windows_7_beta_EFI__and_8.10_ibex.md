---
title: "Windows 7 beta EFI  and 8.10 ibex"
date: 2009-01-12
forum: x86 64-bit Users
---

### Post by ravepants on 2009-01-12
Hi there,

I have today installed the beta of windows 7, along with my favourite distro ubuntu and I have a problem.
I have had a few double and triple boot systems in the past.
Usually windows alongside ubuntu, or OS X along side ubuntu and windows.
I am reasonably familiar with and have used grub.
I did a fresh install of Win7beta today and enabled the uefi option in the bios, the installer graciously created the 200mb uefi partition, and the os partition, and installed, booted and worked fine.
I created some unpartitioned space for the linux install as well.
After installation I tried to boot from cd to install ubuntu, but it appears that the uefi overides everything and just boots windows.
Not taking no for an answer I conned the pc into a failed pxe network boot, then got it to boot from cd, and installed 8.10.
Now after restart I merrily got the grub menu, and ibex boot fine.
However I have now apparently lost my windows boot loader.
Grub comes up with the usual linux and memtest options but not windows.
I tried using the supergrub disk to fix the partitions bootloaders but to no avail, it didnt even see the windows partition.
Now I have a feeling its the EFI causing it, and I have done some research into it, but theres not an aweful amount of documentation out there for win7 yet, and EFI info is all over the place.
I am wondering if I need to implement EFI grub somehow?

Any help appreciated.

Kai :)

---

### Post by djRif on 2009-01-12
Kai

Have you looked at the /boot/grub/menu.lst file to see if Windows is listed in your current grub iteration but perhaps blacklisted? 

I installed Windows 7 beta yesterday over an exisitng dual-boot system with Vista/Ubuntu 8.10 and some problems accessing Ubuntu after windows overwrote the mbr...

I followed links here to re-activate my grub menu.... good luck...
So far I am moderately impressed with Windows 7 but prefer Ubuntu for its infinite customization...

Check here for a very useful starting point...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

cheers

djRif

---

### Post by bcjohnson on 2009-01-12
This link has a tutorial as to how to modify the menu.lst 

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Did it yesterday and it worked fine

---

### Post by JohnL2009 on 2009-01-12
You might find Acronis Disk Director - it has a Boot Manager built in and it works quite well - cost is minimal.

---

### Post by ravepants on 2009-01-14
Hi all,

Thanks for the links.
I have tried many of the suggestions already, unfortunately to no end.
I believ the problem is that I am not using the MBR partition scheme, but instead the new GPT partition method that creates a 200mb UEFI partition from which the os loader binary launches the OS.
I have been on the grub site, and they say grub2 will be UEFI compatible, but there doesnt appear to be a lot of information anywhere about dual booting using UEFI.
On my Mac I have a fantastic bit of foss called rEFIt, which acts as a kind of front end for the apple EFI and allows me to boot OSX from the efi and vista/ubuntu from grub on a seperate partition.
I fear because EFI on the PC is so new (even though it was out quite a few years ago) there is not mush known/documented yet?

---

