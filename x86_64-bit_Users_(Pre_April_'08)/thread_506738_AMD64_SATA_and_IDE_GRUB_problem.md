---
title: "AMD64 SATA and IDE GRUB problem"
date: 2007-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomstockmail on 2007-07-22
Hey all,
I have been having problems installing Ubuntu 7.04 on my AMD Athlon 64 system.  I first tried installing it on half of an IDE 40GB hard drive where the other half held Windows.  This did not work.  So I retried and just got rid of Windows.  GRUB still failed. I soon found it to be a problem with SATA hard drives.  If I detach them, my problem disappears.  Here is the problem:  GRUB freezes.  I quote:
> GRUB Loading stage1.5.

GRUB loading, please wait...
Thats it.  Ends there, no error code.

After some searching, this is the best help I could find:
[http://ubuntuforums.org/showthread.php?t=13847](http://ubuntuforums.org/showthread.php?t=13847)
I modified menu.lst and changed it to boot with noexec=off however my problem still persists.

What can I do so GRUB will boot Ubuntu with SATA hard drives attached?  I have tried installing Ubuntu directly on the SATA and it fails there too, even if the SATA is by itself.

BTW: The SATA drives are not in RAID, and I only hookup one at a time.
Thanks,
Tom

---

### Post by ian dobson on 2007-07-22
Hi,

Any chance that you give us abit more information. What motherboard/chipset, harddisk types etc.

I'm running on a P5B-plus vista (I965 chipset) with an WD IDE boot drive on a JMicron Technologies IDE controller in  AHCI mode and 4 WD SATA drives on the ICH8R/DO/DH SATA RAID Controller and the system runs like a dream.

I'm runnning a patched kernel (2.6.20) with patches for w83627dhg and coretemp support.

Regards
Ian Dobson

---

### Post by tomstockmail on 2007-07-22
It is a DFI K8M800-MLVF with a VIA chipset. North bridge: VIA K8M800, South bridge: VIA VT8237. The IDE is a Western Digital WD400 and the SATA drive is a Western Digital 120GB Caviar.

After some more searching, mobo specific searching, [http://techreport.com/forums/viewtopic.php?t=50809](http://techreport.com/forums/viewtopic.php?t=50809) "just brew it!" talks about this mobo having a problem with GRUB and SATA.  I don't know if it is the exact same problem though.  In his case he decided to use LILO instead of GRUB.  So I might try that soon, after I search on help for replacing GRUB in Ubuntu.

MoBo:
[http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3100&CATEGORY_TYPE=MB&SITE=US](http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3100&CATEGORY_TYPE=MB&SITE=US)

---

### Post by tomstockmail on 2007-07-23
Hey,
I used a Ubuntu 7.04 Text based Alternate CD to choose the option of LILO.  Now after loading LILO, I just get a black screen and no option to choose an OS.
I used this to help me:
[http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader](http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader)

During the black screen my system is pretty frozen, keyboard lights wont light up and random ups and downs left and rights with enters wondering if it could help does nothing.  I still have the same problem with GRUB.

XP is on the first partition, primary, Ubuntu is on the other two, one being the swap.

---

### Post by Ocxic on 2007-07-23
don't unplug other drives while installing ubuntu, that can mess up the boot order for the drives, and can confuse grub.

---

### Post by tomstockmail on 2007-07-23
I didn't unplug anything while installing, before, or after.  I tried installing Ubuntu with the SATA attached and with the SATA unplugged and same errors, if I plugged the SATA back in after installation that is for the IDE only install.

---

### Post by rsambuca on 2007-07-23
First off, I would check to see what order that your hard drives are listed in your bios.  Make sure that matches what is listed in your grub device map.  Since grub has to guess at the drive order sometimes there can be problems when you have ide and sata drives.  Sorry, but I know nothing about lilo though.

---

### Post by tomstockmail on 2007-07-24
Here's an update:
I made a GRUB boot floppy and it fails like the main GRUB but with different text:
> GRUB Loading stage2..............

---

