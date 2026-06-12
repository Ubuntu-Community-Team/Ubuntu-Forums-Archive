---
title: "Reinstalling Yaboot from CD"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by FelixAlias on 2005-12-11
Hey everybody,
I (stupidly) wrecked my second stage bootstrap by not following the instructions and reinstalling the bootloader the way I had always done with every other linux distribution: I booted off the cd, chrooted into my drive, and ran ybin. It gave an error message that the kernel was not new enough for a certain type of device support, (The drive had breezy on it, I booted from a Hoary install disc) and then quit without another error. I rebooted to find the first stage bootstrap had indeed reappeared; however, if I pressed any of the options, it just went to a white screen with the line pattern (the mac os x non-brushed window background). When I zapped the PRAM, instead of going to the white screen, it blacked the screen, and then jumped right back to the first stage bootstrap.

PLEASE HELP!

Thanks,
Felix

---

### Post by FelixAlias on 2005-12-11
FIXED! If anyone cares, here's the exact steps I took:
-Burned a breezy CD
-Booted from it with rescue mode
-Mount proc:
#mount /proc
-Loaded the HFS module
cd /lib/modules/kernel-version/kernel/fs/hfs/
insmod hfs.ko
-Ran Ybin as such (the hd:2 may be a little off; it might be hd,2):
#ybin --ofboot hd:2 --boot /dev/hda2
#ybin -M --ofboot hd:2 --boot /dev/hda2
#ybin --ofboot hd:2 --boot /dev/hda2
(as you can see, I did it a few times for good luck)
rebooted. Works great!!

---

### Post by computer geek on 2007-11-27
Would this also work with 7.04?

Thanks

---

### Post by Kilz on 2007-11-27
You have replied to a post that is about 2 years old , for a version of Ubuntu (Breezy Badger) that is 5 versions old. You may want to post a question about this in the[ Apple section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=133") as you will get more (and up to date) answers there.

---

