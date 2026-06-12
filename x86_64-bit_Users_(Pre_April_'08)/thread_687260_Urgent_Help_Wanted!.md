---
title: "Urgent Help Wanted!"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by CYANIDE-2600 on 2008-02-04
Hello all, I need some urgent help.
I have an AMD 64 based machine running windows vista on a raid setup (2 500gb drives)
I tried to install ubuntu to a usb hdd, installed correctly to the usb drive so restarted the machine, the machine didnt boot from the usb drive so i restarted and tried to boot into windows using the main drives, nada, not a thing!

Grub loading 1.5.
Error 21

What on earth is this error 21 and why is it leeching my internal hdds??
I don't even have a windows restore cd because it was an oem install and i cannot lose the data on the drives it has all my work on it.
Please help.

I know nothing of RAID but atm, i cannot boot into windows, the "Press F9 for expressrecovery" does not work the only thing i can do is get into CMOS (no good) and get into RAID utility (which all it does is tell me the drives are ok)

---

### Post by CYANIDE-2600 on 2008-02-04
ps, this is my first experience with ubuntu :(

---

### Post by prince_niceguy on 2008-02-04
I know this is not a pleasant experience to start off with.

Found some bug and some resolution too on this thread. Hope that helps.

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978)

PS: I am no grub expert but I have got grub errors previously but mostly related to vista screwing up my grub.

---

### Post by crjackson on 2008-02-04
Try booting into windows with the USB drive still plugged into your system.  Good chance your getting the grub error because the grub boot loader is expecting to see that drive as well.

---

### Post by CYANIDE-2600 on 2008-02-04
Hello people!
PANIC OVER! :D
Thanks niceguy, I followed the link and ended up downloading the supergrub program and used it to fix the MBR.

Now working perfectly!

I have an iQon gamer and a new Commodore xx but both use raid and I think that may have been part of the problem, as much as I like Ubuntu and how it reminds me of the AmigaOS on my 2000, 1200 and 4000 it just isn't ever going to be allowed anywhere near either of my desktop machines, to be fair, Windows Vista is lovely I just wanted the simplicity of Ubuntu so I'll install it on my Toshiba laptop instead. 

Anyone else who experiences GRUB 1.5. Error 21: Download SuperGRUB and boot from the CD, when it loads it presents you with a menu. Select FIXMBR & RunWIN and away you go, unless you want to continue to install Linux.

Should someone make SuperGRUB part of the next release of Ubuntu as I think it's damn valuable as it's saved me stress.

---

### Post by prince_niceguy on 2008-02-04
Actually the same can be done using the live cd. So, there is no need for the super grub disk.

Is your ubuntu install working though? Probably you can give another, I am sure you would have looked up some wiki/guide before installing on USB. If not, then  check out the wiki or forum on the usb install. I am using it on the hard disk as it will give maximum performance on disk install. Give it a shot.

---

### Post by shane2peru on 2008-02-04
Installing on an external hdd is not the best experience for first time Ubuntu'ers  or newbies to Linux, I have played around with it, and have read many many posts on it with much difficulty people do get it to work.  If you must use Linux on a USB hdd, then do yourself a favor and use an easier distro like, DSL, or Puppy, those are setup to install on USB, they are very lightweight.  Or if you want to use Ubuntu, then read, read, read before attempting.  Perhaps it has gotten easier, but read.  :)  That is my 2 cents worth. 

Shane

---

### Post by CYANIDE-2600 on 2008-02-23
Ubuntu seems like a nice OS, just not as easy as Windows to set up.

I got a laptop running XP, can it be dual booted to run Ubuntu easily?

---

### Post by marvelljones on 2008-02-23
> **CYANIDE-2600 said:**
> Ubuntu seems like a nice OS, just not as easy as Windows to set up.

I got a laptop running XP, can it be dual booted to run Ubuntu easily?

Sure.  I found this link:

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

It mentions a prior version of Ubuntu, but the same method still works.  I haven't used this dual boot method recently since my XP machine died on me, and I replaced it with a HP a6110n running Vista I picked up on clearance.  I used this method (using EasyBCD):

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

I threw in the last link just in case you decide to someday upgrade the laptop to Vista.  There are definitely other ways to do it, but those of us who just can't let go of Windows might find this easier.:twisted:

---

