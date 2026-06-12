---
title: "Endless loop of errors on Live CD boot."
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by rnawky on 2008-07-25
When I boot with the 64 bit Ubuntu live CD. I get the following errors

[####.######] Buffer I/O error on device sr0, logical block 51341
[####.######] Buffer I/O error on device sr0, logical block 51343
[####.######] Buffer I/O error on device sr0, logical block 51342
[####.######] Buffer I/O error on device sr0, logical block 51344
[####.######] Buffer I/O error on device sr0, logical block 51344
[####.######] Buffer I/O error on device sr0, logical block 51346
[####.######] Buffer I/O error on device sr0, logical block 51346

[####.######] SQUASHFS error: sb_bread failed reading block 0x18871
[####.######] SQUASHFS error: Unable to read fragment cache block [6217dc5]
[####.######] SQUASHFS error: Unable to read page, block 6217dc5. size 47ed


And it repeats over and over until I restart. Does anyone have an clue as to how to fix this. I have checked the iso and cd for faults and none were found, so I doubt it's the media.

Thanks.

**EDIT:**
The errors start after the boot progress bar reaches ~90% and the console reads

hardware abstraction layer hald

without a [fail] or [ok]

**EDIT:**
I was using 8.04 and I downloaded 8.04.1 and this time I got the same thing, however after just a few loops of errors I got a desktop with nothing on it (basically just a background) Then I restarted the x server and it came back after a few MORE cycles of errors and then I was presented with a dialog box saying "failed to initialize hal"

---

### Post by Rocket2DMn on 2008-07-25
Sounds like a bad image download or a bad burn.  At this point I would suggest using the altnernate install cd which uses a text based installer rather than a live session - it is still easy to use.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.
Don't forget to check the md5sum, then burn at a slow speed like 4x to help prevent write errors.
[uhelp]community/HowToMD5SUM[/uhelp]
[uhelp]community/UbuntuHashes[/uhelp]

---

### Post by rnawky on 2008-07-27
> **Rocket2DMn said:**
> Sounds like a bad image download or a bad burn.  At this point I would suggest using the altnernate install cd which uses a text based installer rather than a live session - it is still easy to use.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.
Don't forget to check the md5sum, then burn at a slow speed like 4x to help prevent write errors.
[uhelp]community/HowToMD5SUM[/uhelp]
[uhelp]community/UbuntuHashes[/uhelp]

Hmmmm. According to uTorrent, they passed the hash check. I'll try the alternate cd though and see how that goes.

---

### Post by Sef on 2008-07-27
Did you burn at 4x or less? If you did more, that may be the reason for the bad burn.

---

### Post by roadrash on 2008-08-07
I had this problem and the way I solved it was to change the DMA mode settings for the CD/DVD drive in the PC's BIOS from auto to SWDMA0 (single word dma). my systems bios has options for Auto, SWDMA0 to SWDMA2, MWDMA0 to SWDMA2 and UDMA0 to UDMA5.

SWDMA = Single Word DMA
MWDMA = Multi Word DMA
UDMA = Ultra DMA

hope this helps

---

### Post by yotam on 2008-08-20
While trying to install Xubuntu Intrepid 8.10 alpha-4 
I got similar errors. See my report 
[http://bugs.launchpad.net/bugs/259901]("http://bugs.launchpad.net/bugs/259901")

---

### Post by alamuru420123 on 2008-08-20
This might work for you:

[http://ubuntuforums.org/showpost.php?p=5633091&postcount=7](http://ubuntuforums.org/showpost.php?p=5633091&postcount=7)

---

### Post by yotam on 2008-08-22
> **alamuru420123 said:**
> This might work for you:

[http://ubuntuforums.org/showpost.php?p=5633091&postcount=7](http://ubuntuforums.org/showpost.php?p=5633091&postcount=7)

Indeed! that solved the Live-CD problem. 
Namely, adding **all_generic_ide** to the boot parameters.
Thanks!

---

### Post by tekorei on 2008-08-23
I think it's a Hardware problem, I got the same SQUASHFS error during my installation, I swapt my DVD-DRIVE and it worked, good luck

---

