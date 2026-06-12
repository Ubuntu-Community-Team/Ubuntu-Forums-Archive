---
title: "OpenFirmware - yaboot Situation"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by fl1pper on 2006-03-02
I had debian running, on the desktop, dual-bootable, 18 months ago (on my first try, heheh), followed by consecutive ubuntu installations, none of which exist now. I reformatted the drive a while back. Bummer.

So, I'm in OpenFirmware, with the four yaboot files on the / drive, typing: boot hd:disk0s2,yaboot at the prompt, and OF declares that all my partition addresses are "invalid". The main / drive is disk0s2, and I have another partition, disk0s4, that I want to install ubuntu onto.

But I cannot get past OpenFirmware. I did all the reset-nvram, reset-all stuff, tried all kinds of 'wrong' partition numbers, same response from OF. Tried the 'ide' style, instead of disk0sx, no go. I am completely stumped. I've helped complete newbies with their first Linux on Mac installs, from long distance [phone or email] and they're all up and running, but not me.

If anyone has seen this, and knows the way out, I am all ears, er, eyes. :)

Thanks

---

### Post by ssam on 2006-03-02
i am not completely sure what you are trying to do.

is that you have a completely fromated disk and you want to install ubuntu? or do you have an ubuntu install on the disk but it wont boot?

can you boot the ubuntu live cd by holding 'C' at boot?

---

### Post by BoneKracker on 2006-03-02
I assume you have checked the syntax you are using.  I seem to recall booting from OF with something along the lines of hd:3:/boot/vmlinux.  But it sounds like you know a lot more about this than I.  Just the suggestion that you check syntax if you haven't.  Good luck.

---

### Post by fl1pper on 2006-03-02
[QUOTE=ssam]i am not completely sure what you are trying to do.

is that you have a completely fromated disk and you want to install ubuntu? or do you have an ubuntu install on the disk but it wont boot?

can you boot the ubuntu live cd by holding 'C' at boot?[/QUOTE]

No, I don't have the Live CD, and my internal optical drive, the SuperDrive is dead. I have a 13GB partition, empty on the powerbook's internal drive. I have an external optical drive that can boot the Mac.

It's frustrating because i've done this easily, before. The problem is simply that when I boot into OpenFirmware, which has to be done the first time, in order to give the bootloader the proper address to grab yaboot, the proper syntax results in an "Invalid partition number". The partition number is correct, hence the huge drag of it all. The "invalid partition" can't be 'worked around', so my only choice at that point is to type in:

mac-boot

and sure enough, the Mac reboots, right into the main drive, which has the exact same partition [BSD number] as the one that was called 'Invalid' in OpenFirware. It's a crazy situation.

---

### Post by fl1pper on 2006-03-02
[QUOTE=ssam]i am not completely sure what you are trying to do.

is that you have a completely fromated disk and you want to install ubuntu? or do you have an ubuntu install on the disk but it wont boot?

can you boot the ubuntu live cd by holding 'C' at boot?[/QUOTE]

No LiveCD, only the installer. No blank CDs, and besides, the LiveCD requires that you do some sort of boot block thing unless you always want to boot from the CD. I want to boot into the drive, but the install won't even start until I can figure out why the proper syntax in OpenFirmware isn't resulting in the usual boot into the yaboot cli, from which point the install [i've done a bunch] is smooth all the way through.

---

### Post by Ptero-4 on 2006-03-02
Have you used the "option" bootloader? It's quite capable of locating misplaced yaboots.

---

### Post by fl1pper on 2006-03-03
[QUOTE=Ptero-4]Have you used the "option" bootloader? It's quite capable of locating misplaced yaboots.[/QUOTE]

I don't have the install happening yet.

To do an install on the Mac, one has to boot into OF with yaboot, yaboot.conf, initrd.gz, AND the vmlinux files already parked on the main drive, i.e. /

Those files are on my drive.

But going into OpenFirmware, and entering

boot hd:disk0s2,yaboot

instead of booting into yaboot, and then being able to do the install, i get an error saying "Invalid partition number" meaning, OpenFirmware doesn't recognize the valid mountpoint of my main internal drive, and therefor will not boot using those four files. The ubuntu Install CD is NOT a bootable CD, it does not show up on the "Option-key" bootloader window, at all...if it did, then PPC users would never have to load the four initial files on their drives, in the first place.

How in the world is Option key booting going to show an ubuntu install that hasn't even been done yet? The prob is OpenFirmware, the same thing you guys probably call BIOS... OF isn''t recognizing the partition number [the BSD number] of the same partition I boot into [for OS X] all the time. it's nuts, like I said.

---

### Post by jdp on 2006-03-03
To clear this up a bit, are you sayign that you've copied the YaBoot files to the root of your OS X install, or to the root of the partition that you plan to install Ubuntu to?

---

