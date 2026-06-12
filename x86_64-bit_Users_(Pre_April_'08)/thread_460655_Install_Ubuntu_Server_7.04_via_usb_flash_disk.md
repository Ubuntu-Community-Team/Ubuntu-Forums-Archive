---
title: "Install Ubuntu Server 7.04 via usb flash disk"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by kranki on 2007-05-31
I bought a new server with dual quad-core cpus.  I am very new to Ubuntu and have only installed the desktop version on 32-bit computers without modification.  In the past I have successfully installed Gentoo Linux on 32-bit machines which was much more intensive than Ubuntu desktop and much less fun;).

Could someone point me to:

a) directions on how to move the server amd64 iso to a usb flash disk

b) how to set up Ubuntu server in a minimal configuration. (I do not know why, but I have had a really hard time finding the server installation doc online.  Maybe it was just me not looking in the right places! (Ok, I am older and maybe slipping a little bit! ;) )

??

Unfortunately, the new machine does not have a cd/dvd drive, but does support usb.  I can boot both a flash drive and an external harddrive.

My first cut at moving the AMD64 Desktop install iso to a flash disk failed, but I followed instructions for a 32-bit install.  Unfortunately, I just don't know the 64-bit side of things and any help or suggestions would be appreciated.

BTW, I will only running be this machine for the Folding@Home SMP program.  That is why I only need a minimal configuration.

Thank you in advance for your suggestions.

---

### Post by kranki on 2007-06-01
ok, I found the doc on the server edition.  So, I will use it once I can get a usb 1gb drive to work.

I tried all day using various methods to create a usb drive to boot the Ubuntu 7.04 AMD64 version from, but nothing works.  I even tried booting a 32bit Gentoo usb drive that I had previously booted from when I was using it rather than Kubuntu/Ubuntu.  That did not even work.

I reviewed the BIOS settings and they seem to indicate that it should work.

However, I do have a question.  I downloaded syslinux 3.36 on a 32-bit version of Kubuntu.  Compiled it after installing nasm which seemed to go well.  I then did a syslinux -s /dev/sda1 which was the usb flash drive after formatting the drive on Windows XP.

My last try was to copy over the Ubuntu 7.04 AMD64 cdrom onto the flash disk.  Then I copied the isolinux directory to syslinux. and renamed isolinux.bin and isolinux.cfg to syslinux.bin and syslinux.cfg respectively.  Tried to boot that and got a blinking cursor.  I did not change syslinux.cfg.

Mostly, I get a blinking cursor.  Holding down alt does not give me the boot: prompt.

Anyway, any help is appreciated.

---

### Post by kranki on 2007-06-03
Well, I gave up.  I tried 6-7 different techniques to build the flash disk and none worked.  I broke down and bought an external usb cdrom/dvdrom drive and that worked first time.  Oh, well, at least I got it running now.

---

### Post by ensiferum69 on 2007-06-10
yeah... I got usb drive to boot and all, but when it reaches the file transfer I keep getting an undetectable cdrom error... and that makes me a sad panda

edit: just found this info here [http://www.extremetech.com/article2/0,1697,2132614,00.asp](http://www.extremetech.com/article2/0,1697,2132614,00.asp)
seems pretty reasonable, going to try it

---

### Post by inkyblue2 on 2007-06-12
i just stumbled on one thing that might help: you need to do syslinux -smf in order to boot from the usb drive. i don't know anything about when or why or how, i just know that adding the "mf" was what took me from blinking cursor to working USB boot.

... wait, you're using syslinux on a unix machine. i don't think it has the m or f options, but there is some equivalent method out there of writing the MBR. i remember seeing it, but i forget where.

good luck!

---

