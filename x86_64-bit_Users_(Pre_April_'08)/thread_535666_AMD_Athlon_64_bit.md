---
title: "AMD Athlon 64 bit"
date: 2007-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Red-Shield on 2007-08-26
i cant seem to find a version of ubuntu the will load on to my computer it always stops at the point of partition it wont do any thing past that it dose not even give the option to manualy partition it just says "how would you like to partition?" and then there is no option and it will not allow me to go forward i have waited a max of 25 min and still nothing i have a gateway 7510GX with a AMD Athlon 64 bit processor i am currently running windows XP my comp is in good health i have 100GB hard drive and 1GB ram i was wondering if i have not waited long enough of if i need to wipe windows from my hard drive i have used the following versions with the same results ubuntu7.04 desktop amd64 and about 4 other versions that were older i have know idea why it will not partition or allow it to.......  Red-Shield

---

### Post by Paul820 on 2007-08-26
There is no need to wipe windows. Did you burn the cd at a slow speed? You should burn it at around 4x. Did you check the MD5 sum? You should not have to wait 25 minutes for it to partition so there might be something wrong with the CD. Check that first.

---

### Post by LowSky on 2007-08-26
Are you resizing the Hard Drive to fit Ubuntu on to it?
If so please defragment you hard drive under Windows first

Also, please use the x86 version of Ubuntu, not AMD64 version. This way you can have this like flash and such working properly.

---

### Post by Paul820 on 2007-08-26
Flash does work in ubuntu 64 i'm using it thanks to the script that kilz provides here: [http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+64bit]("http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+64bit")
There is nothing wrong with the 64 bit version of ubuntu, everything works exactly the same as 32bit, even the same packages in the repositories.

---

### Post by John.Michael.Kane on 2007-08-26
> **Red-Shield said:**
> i cant seem to find a version of ubuntu the will load on to my computer it always stops at the point of partition it wont do any thing past that it dose not even give the option to manualy partition it just says "how would you like to partition?" and then there is no option and it will not allow me to go forward i have waited a max of 25 min and still nothing i have a gateway 7510GX with a AMD Athlon 64 bit processor i am currently running windows XP my comp is in good health i have 100GB hard drive and 1GB ram i was wondering if i have not waited long enough of if i need to wipe windows from my hard drive i have used the following versions with the same results ubuntu7.04 desktop amd64 and about 4 other versions that were older i have know idea why it will not partition or allow it to.......  Red-Shield

Have read over this sticky thread [Please Read First 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607") it includes links to all the 64bit iso's, and guides.

As for the boot issue. Try rebooting the machine with the ubuntu cd/dvd in the drive. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

### Post by Red-Shield on 2008-01-10
yes thank you this problem was solved by defragmenting the hard drive in windows first.,

---

### Post by Yellow Pasque on 2008-01-10
Please mark thread as [SOLVED]. Thanks.

---

