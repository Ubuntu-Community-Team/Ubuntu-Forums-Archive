---
title: "Dual boot 32bit and 64bit???"
date: 2006-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by NoX33 on 2006-10-21
Can I dual boot 32bit and 64bit Ubuntus? If so, how? I've tried and failed a bunch of ways and need help...

---

### Post by pay on 2006-10-21
You sure can, but why? You can just install a 32bit chroot for any reason that you might need the 32bit version. There are a few guides on how to do that on this forum.

---

### Post by NoX33 on 2006-10-22
Well the difficulty with certain programs running on 64bit. 32bit is a lot easier to update and upgrade than 64bit, plus every program is compatible. I want 64bit for the performance upgrades, yet hate the difficulties that some programs have with installs. And the fact that they all don't semm to work. Where are the howtos to dual boot 32bit and 64bit? What do you recommend I do? I originally had 64bit Dapper running pretty good, but upgrade to Edgy and had problems.

---

### Post by pay on 2006-10-22
Heres a guide on how to install a chroot (32bit installation inside of 64bit) [http://ubuntuforums.org/showthread.php?p=904320](http://ubuntuforums.org/showthread.php?p=904320)
What problems are you having with installing both distros? Just install one but leave some space for the other, then install the other into that space and then add a menu entry for the old one into grub. (/boot/grub/menu.lst)

---

### Post by NoX33 on 2006-10-22
Problems: Installed both on separate partitions of course, and with a partition for /boot and a partition for /home, and shared swap. When I installed both, it shows both kernels for 386 and AMD64 in grub, so I presumed it worked. I fully set up 386 with all my modifications, then went on to AMD64. When I selected the AMD64 kernel, it loaded the partition with 32bit, not 64bit (figured this out, because of the different login window I changed 386 to and mouse, touchpad, and internet didn't work). I can't figure out how to get it to work. Then, made a thread on beginners forum to figure it out, and someone said to have different username and password from the two OSs. Reinstalled 64bit, and then couldn't access 386. the problem was like it just switched sides.

---

### Post by pay on 2006-10-22
Are you using the same home partition for both? because that would be why the gdm screen would be the same on both. uname -a will tell you weither it's 64 or 32

---

### Post by NoX33 on 2006-10-22
Yes, I was using the same home partition for both. I thought that might have been the problem, but wasn't a 100% sure and wanted to take it one step at a time and just ask for help. Problem because of the the two different architectures' files on the same home partition? What should I do? Reinstall 64bit only or should I do both? I kind of like having both due to having program compatiblities with 32bit and the easy installs and updates for when I'm lazy, but I manage not to have it at all.

---

### Post by pony-tail on 2006-10-22
Although a little different the principles should be the same .
I currently Tripple boot my AMD64 machine (Win2k/Ubuntu 64 "dapper"/Ubuntu 64"edgy"RC ) I found that I had to muck around (trial and error) With menu.list as the installer mis-detected the drive "edgy" was on.
> title		Ubuntu, kernel 2.6.15-27-amd64-k8
root		(hd0,1)
kernel		/vmlinuz-2.6.15-27-amd64-k8 root=/dev/sdb1 ro quiet splash
initrd		/initrd.img-2.6.15-27-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-k8 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-27-amd64-k8 root=/dev/sdb1 ro single
initrd		/initrd.img-2.6.15-27-amd64-k8
boot

title		Ubuntu, kernel 2.6.15-23-amd64-k8
root		(hd0,1)
kernel		/vmlinuz-2.6.15-23-amd64-k8 root=/dev/sdb1 ro quiet splash
initrd		/initrd.img-2.6.15-23-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-k8 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-23-amd64-k8 root=/dev/sdb1 ro single
initrd		/initrd.img-2.6.15-23-amd64-k8
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu,Edgy 6.10 kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu,Edgy 6.10 kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdc1 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdd1 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdc1 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdc1 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot


It was detected as root (hd3,0) but is in fact root (hd2.0)
I am running 4 hard drives each OS having it's own drive - further I found that I had to use an add in PCI card for the second 2 drives as when I use the onboard second 2 SATA conectors it changes order from bootup to bootup 
sometimes starting as SATA port1 as hd0 sometimes SATA3 as zero resulting in repeated boot failures (NFORCE 4 onboard SATA ) and as for the Sil 3114 that I have onboard Linux is just not an option (except a custom compiled Gentoo kernal I was using prior to migrating the machine to Ubuntu)
I have 8 onboard SATA ports but can only use 2 with Ubuntu - Maybe you have similar issues -

---

### Post by pay on 2006-10-22
Well personally I hate having both. I stick with either 64bit or 32bit. The performace won't be that different with the 32bit one anyway. But if you want to install both you can. I think you can even use the same home folder for both, just don;t get freaked out when they both have the same settings (thats where your settings are stored anyway). You need a / partition (atleast 5 gb) for both, a shared swap (twice the size of ram), either a shared or 2 /home partitions and optionally a /boot partition (100mb)

---

### Post by NoX33 on 2006-10-22
Well I am running this on a single hard drive laptop, so that eliminates the some things. I wasn't freaked out over the same settings with the login window, it was the mouse and touchpad not working, and then when I logged in by switching to tty1 for login and then the wired internet was not working too. I thought that the AMD64 kernel was using the 32bit installation, thats why everything was not working.

---

### Post by pay on 2006-10-22
Come to think of it you might need 2 home paritions after all since that settings would point the programs on the 32bit installation's partitions, like if you installed wine on 32bit, then the settings would be liked to the 32bit install..

---

### Post by NoX33 on 2006-10-22
Yeah. I think that will be my project tomorrow morning. Just start from scratch with two fresh installs with separate home partitions. I in Naples, Florida, U.S. so its 1:15 a.m.. I really appreciate the help. Thanks a lot. I post my results tomorrow. Quick questions..... Should I install 32 Dapper or Edgy? 64 Dapper or Edgy? I heard 32 Edgy is basically the final and very few minor bugs. What about 64 Edgy?

---

### Post by pay on 2006-10-22
Well that would be a up to personal preference. Dapper is older and probably more stable because it's been tested alot more, and edgy is bleeding edgy without as much testing. With 32 or 64 you need to decide wither you think that the performance increase is worth the extra effort setting it up. I'm currently using edgy 32bit, because for some reason that 64 iso of edgy and dapper wouldn't boot.. (though there is an alternate cd, I just don'i want to use up all my bandwidth).

---

### Post by NoX33 on 2006-10-22
Ok. When I updated to 64 Edgy, I had problems from the get go, but that was the beginning of October. Just wanted to check opinions and others' experiences. Thanks again for your help. I'll post my results tomorrow on how the install of both 32bit abd 64bit went. Whether or not it is successful.

---

### Post by kuja on 2006-10-22
Just a note from my experiences. I don't recommend having a single /boot partition. If multiple installations share it things can get really, really, really hairy.

---

### Post by pay on 2006-10-22
Normal installations don't even use the /boot partition though.

---

### Post by kuja on 2006-10-22
Normal is such a vague word.

---

### Post by pony-tail on 2006-10-22
> What about 64 Edgy?
64bit "edgy" is still a little screwy here and there but is useable - But my recomendation would be to stick with "dapper" at present (that is why I am dual booting dapper and edgy - Some things that were working fine in the betas of edgy are now broken in the current release candidate (xorg (ATI only  some X series cards X850XT-PE in my case) for one and support for the two sata controllers on NF4 boards (only an issue if you have more than 2 hard drives ) ) mostly minor but those two both directly affect me - If you are using a laptop niether should be an issue but others may be present that do .
Dapper 64 appears to be solid !

---

### Post by pay on 2006-10-23
> **kuja said:**
> Normal is such a vague word.
A normal install would be a desktop without multiple operating systems.

---

### Post by NoX33 on 2006-10-24
Success. Just have to keep everything separate from one another and I only share the swap. 32 Edgy is pretty much solid as a rock and I have nothing but a few minor bugs (mainly just figuring out the differences from Dapper). I don't recommend 64 Edgy just yet, thats for sure. Its still a little hairy and buggy. Stick with 64 Dapper. Solid and runs smooth.

---

### Post by pay on 2006-10-25
For 32bit cpus I love ubuntu, but for 64bit cpus I prefer Gentoo. Mainly because you don't have to worry about 32/64bit packages because they are all the same.

---

### Post by gawallac on 2006-10-25
> **NoX33 said:**
> Success. Just have to keep everything separate from one another and I only share the swap. 32 Edgy is pretty much solid as a rock and I have nothing but a few minor bugs (mainly just figuring out the differences from Dapper). I don't recommend 64 Edgy just yet, thats for sure. Its still a little hairy and buggy. Stick with 64 Dapper. Solid and runs smooth.

Could you expand on how you were able to get the dual boot setup.  I am currently running Edubuntu 64 Dapper as my only operating system and am interested in adding 32 bit Edgy.  I am not very skilled with these installations and could really use some guidance.

thanks

---

