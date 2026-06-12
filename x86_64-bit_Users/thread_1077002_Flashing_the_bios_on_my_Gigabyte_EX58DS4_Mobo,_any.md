---
title: "Flashing the bios on my Gigabyte EX58DS4 Mobo, any problems?"
date: 2009-02-21
forum: x86 64-bit Users
---

### Post by Col-1023 on 2009-02-21
I'm running Ubuntu 8.10.amd64 exclusively,and I'm going to be upgrading my motherboards bios from F3 to F4 using the Gigabyte Q-Flash utility, so I want to know if there is anything that may cause a problem.

Does Q-Flash work well with UBuntu 64 bit, I Know gigabyte says it is OS independent?

I'll use a USB memory stick, are these usually formatted in FAT32, or NTFS, since gigabyte says q-flash needs FAT32 or FAT16?

Gigabyte also says to load optimised defaults once the bios is flashed, does that mean to flash the bios let the pc reboot, then go back into the bios and load optimised defaults, or will q-flash send me back to the bios screen once it's finish so I can do it from there, and once I do this, will I need to choose the option "save and quit", or the option "quit WITHOUT saving" to exit the bios?

How long does it take the q-flash problem to flash a bios, and if there is a problem does the Backup Bios (Dual Bios) load automatically, or will I have to manually enable it?

Thanks In Advance.

---

### Post by Arup on 2009-02-21
You can't use Qflash on Ubuntu, it follows a totally different structure for flashing BIOS unlike in Windows, what you need to do is create a boot disk and then burn the Qflash file to it, then boot off that CD and in DOS prompt, enter qflash and thats how your BIOS would be renewed.

---

### Post by sanderj on 2009-02-22
> **Col-1023 said:**
> I'm running Ubuntu 8.10.amd64 exclusively,and I'm going to be upgrading my motherboards bios from F3 to F4 using the Gigabyte Q-Flash utility, so I want to know if there is anything that may cause a problem.

Does Q-Flash work well with UBuntu 64 bit, I Know gigabyte says it is OS independent?

<snip>

Have you just tried it yourself instead of asking? Just download the BIOS with firefox, put it on a FAT-formatted USB-stick, reboot the system, and then follow the instructions on [http://www.gigabyte.com.tw/FileList/NewTech/old_motherboard_newtech/tech_qflash.htm](http://www.gigabyte.com.tw/FileList/NewTech/old_motherboard_newtech/tech_qflash.htm)

I've an Asus mobo and I've done this a few times without problems.

---

### Post by Col-1023 on 2009-02-22
Thanks for your replies.

Thanks SjanderJ for the link. I haven't flashed the bios yet, I've downloaded it, but I thought I'd ask on the forum before I flashed it just in case there were any problems associated with Ubuntu and Q-flash.


I've never flashed a bios, so I want it to go smoothly.

---

### Post by IanW on 2009-02-23
> **Col-1023 said:**
> I've never flashed a bios, so I want it to go smoothly.

As long as you have the correct bios for your mobo & don't have a power outage during the procedure it will all go fine.
(Edit: See my sig)

---

### Post by Col-1023 on 2009-02-24
I flashed the bios and everything seems fine, it seems to have fixed my unstable LAN problem.

Thanks everyone for your replies.

---

