---
title: "Installing ubuntu-7.04-desktop-amd64.iso fails"
date: 2007-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by sneakyfox on 2007-07-10
Hi,

Just got my new laptop and downloaded the latest 64-bit Ubuntu. Verified the ISO with md5. Burned (twice) and tried installing, but it aint working.

I get the boot menu, select Install, and wait. The Ubuntu logo pops up with the progress bar. Suddenly the install exits and I'm left at a CLI with the following text: "cant access tty; job control turned off". Google told me this just means that booting failed. So I checked /casper.log and it says** "mounting /dev/sda1 on /cdrom failed: no such device"** over and over.

This also happens if select check CD from the boot menu.

The laptop is brand new with a Santa Rosa platform plus Nvidia 8600 GT graphics, SATA harddrive and PATA dvd-drive. More info about chipset: [http://www.intel.com/products/centrino/duo/index.htm?iid=prod_pt+sc_centrinoduo](http://www.intel.com/products/centrino/duo/index.htm?iid=prod_pt+sc_centrinoduo) (I asume i have the Mobile Intel® PM965 Express Chipset, since I have Nvidia graphics).

So, really don't know what to do next. Hoping one of you guys can help me.

I have some experience running debian as a server. :guitar:


Note: the boot menu selects VGA as default resolution but that results in a blank screen (have 14.1inch widescreen). If I select any other resolution it's displayed fine, although the CLI don't seem to like widescreen - the left margin is anything but vertical. Don't think it has anything to do with the other problem though.

---

### Post by OldAlgis on 2007-07-10
>  I get the boot menu, select Install, and wait. The Ubuntu logo pops up with the progress bar. Suddenly the install exits and I'm left at a CLI with the following text: "cant access tty; job control turned off". Google told me this just means that booting failed. So I checked /casper.log and it says "mounting /dev/sda1 on /cdrom failed: no such device" over and over.
 

Is this a temperature problem? Laptops do get hot.  I had trouble installing Linux on my laptop, as the DVD would read for a while and once the laptop got hot, it would start showing read-errors.  It was an openSUSE 10.2 installation.  I ended up by copying the installation DVD on another PC on my home network, booting cool laptop on DVD and specifying the installation source on the home network.  That worked OK.  Have no idea how to do that with ubuntu.  Neither do I know how hot you laptop is when you read the DVD.

Just a thought that might be of some use.
OldAl.

---

### Post by sneakyfox on 2007-07-10
Thanks for your reply!

It can't be temperature. Took it right out of the box, plugged it in, booted with ubuntu CD in it.

And it doesn't look like it has problems reading from the dvd/cd-drive; it boots from it without problems. It also loads the linux kernel fine. 

I'm no where near an expert, but doesn't the error just mean that linux can't mount the cd-drive?

Hoping someone can solve this, I'm itching to start running Ubuntu on my new hardware!

---

### Post by sneakyfox on 2007-07-11
Just tried installing with 32-bit text based installer, and it worked!

---

### Post by red star on 2007-07-12
Had the same problem with the 64. Had no problem installing the 32bit, but can't get my nividia to work with  the os. Check all the forums and everyone seems to have the same problems. Not really sure how to get the 64 up and going.

---

### Post by Kilz on 2007-07-12
> **sneakyfox said:**
> Just tried installing with 32-bit text based installer, and it worked!

For those wanting to install Ubuntu and not check it out in advance. The text installer IMHO has a better chance of working. In fact I no longer download the live cd's of versions to test (64bit Feisty last time) but the alternate (text based) cd.
You should try the 64bit text based cd, if you have the 64bit hardware.

---

### Post by mattlacey on 2007-07-19
I have the exact same problem on an almost identical machine - I just got a Zepto 6625 yesterday and was quite gutted when the installer failed!

I'll try the alternate one next week!

---

### Post by cprofitt on 2007-07-19
> **red star said:**
> Had the same problem with the 64. Had no problem installing the 32bit, but can't get my nividia to work with  the os. Check all the forums and everyone seems to have the same problems. Not really sure how to get the 64 up and going.

Tell me more about your problems... I just got 64bitt to work, but had to change the menu.lst settings for GRUB.

---

### Post by Number6 on 2007-07-30
Well I'm trying to run Ubuntu 7.04 AMD64 on my system :
AMD64 X2, 
ASUS A8N5X Mobo, 
SATA Drives,
ATi X850 Vid Card, 

 and while I did manage to install it, I find I can't boot the standard image because the screen blanks with a No Signal, and thats it!!!
I can however boot the recovery image, and If I exit from the root shell, every else (GDM etc) boots OK from then and I can use the system normally!!

---

### Post by jespdj on 2007-07-30
> **mattlacey said:**
> I have the exact same problem on an almost identical machine - I just got a Zepto 6625 yesterday and was quite gutted when the installer failed!

I'll try the alternate one next week!
Well, the Zepto 6625WD is one of those brand new Intel Santa Rosa laptops, full of brand new hardware, so you can expect that there aren't out-of-the-box working drivers included in Ubuntu 7.04, which is older than the hardware.

Here's an interesting topic: [Ubuntu on 6224W/6324W](http://ubuntuforums.org/showthread.php?t=490187) (those Zepto laptops have hardware very similar to the 6625WD).

Let us know what your experience is getting 64-bit Ubuntu to work on your 6625WD, I'm interested in that laptop too. :)

---

