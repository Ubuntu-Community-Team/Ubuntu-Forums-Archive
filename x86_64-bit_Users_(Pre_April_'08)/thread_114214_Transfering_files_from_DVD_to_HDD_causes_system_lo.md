---
title: "Transfering files from DVD to HDD causes system lock-up."
date: 2006-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bandit on 2006-01-08
Hello Everyone,
I been using Ubuntu and linux for a long time.
I just recently over the past few days built a AMD64 System.
Now for some reason when I copy files from my DVD+RW to the hard drive it cuases everthing to lock-up except my mouse.
I cant switch to another terminal or force x to close.
My system specs are listed on my signature.
Is there something I need to know about 64bit Ubuntu 5.10 thats any diferent the the 32bit version.
I have been running this setting in hdparm.conf if this matters.
/dev/cdrom {
   dma = on
}
command_line {
   hdparm -X66 /dev/cdrom
}
That setting worked great in 5.04 and 5.10 32bit versions.
I just removed -X66 to see if there is a glitch in the kernel by chance.
My DVD is a ATA66 drive tho. 400% poisitive, its detected by the BIOS as ATA66 as well.

Any Ideas?
I most of the time doesnt crash on the first file. It can be file #200 or anything in between or after.
It just random...

Cheers,
Joey

---

