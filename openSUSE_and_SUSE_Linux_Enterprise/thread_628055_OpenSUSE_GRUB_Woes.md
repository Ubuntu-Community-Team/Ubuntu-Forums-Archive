---
title: "OpenSUSE GRUB Woes"
date: 2007-11-30
forum: openSUSE and SUSE Linux Enterprise
---

### Post by twisted willow on 2007-11-30
I sit here at 1.30am after a third failed attempt to install OpenSUSE 10.3. Although I'm really impressed with Ubuntu I've had an itch to try SUSE that just won't go away. However, attempts to install from the live CD version and a magazine cover DVD have ended in failure and wasted hours.

On both occasions SUSE has failed to correctly set up GRUB, leaving me with an unbootable system. I don't know enough about GRUB to solve the issues, and utilities like Super Grub Disk and an article entitled 'When Linux Won't Boot' that was coincidentally in the magazine the DVD came with didn't help.

How can Ubuntu get GRUB setup right when SUSE gets it wrong? I'd love to try SUSE (I guess I have the live CD) but I can't waste more hours reinstalling and setting up Ubuntu if it goes wrong again.

I have a fairly simple setup; Windows XP on one drive (hda) and a second drive devoted to Linux (hdb). I guess GRUB is installing the bootloader on hda. Besides getting an error along the lines of (hd0,0)/boot/message:file not found I was also getting Error 17 Cannot find selected partition.

I guess I'll stick with Ubuntu for the time being - it's a very good distro to stick with after all!

Ubuntu has installed and updated as I've typed this (on my daughter's laptop). As it's now 2.00am, I think I'd better get to bed, and leave the rest of the setting up until tomorrow.

Goodnight.

---

### Post by sandysandy on 2007-11-30
> **twisted willow said:**
> I sit here at 1.30am after a third failed attempt to install OpenSUSE 10.3. Although I'm really impressed with Ubuntu I've had an itch to try SUSE that just won't go away. However, attempts to install from the live CD version and a magazine cover DVD have ended in failure and wasted hours.

On both occasions SUSE has failed to correctly set up GRUB, leaving me with an unbootable system. I don't know enough about GRUB to solve the issues, and utilities like Super Grub Disk and an article entitled 'When Linux Won't Boot' that was coincidentally in the magazine the DVD came with didn't help.

How can Ubuntu get GRUB setup right when SUSE gets it wrong? I'd love to try SUSE (I guess I have the live CD) but I can't waste more hours reinstalling and setting up Ubuntu if it goes wrong again.

I have a fairly simple setup; Windows XP on one drive (hda) and a second drive devoted to Linux (hdb). I guess GRUB is installing the bootloader on hda. Besides getting an error along the lines of (hd0,0)/boot/message:file not found I was also getting Error 17 Cannot find selected partition.

I guess I'll stick with Ubuntu for the time being - it's a very good distro to stick with after all!

Ubuntu has installed and updated as I've typed this (on my daughter's laptop). As it's now 2.00am, I think I'd better get to bed, and leave the rest of the setting up until tomorrow.

Goodnight.

what is output of sudo fdisk -lu

regards

---

### Post by Incense on 2007-12-02
Can you boot into SuSE at all, even when you use the grub super disk? If you can, there is a nice GUI tool in YaST to help you setup your boot loader. You start up YaST, go into the system section, click Boot Loader. You can then select the second tab **Boot Loader Installation**, and from here you can reload grub, and tell it where to load, and what to load. **Section management** tab should also detect all your other partitions.  

If you can not boot into SuSE, try to load up the live disc and see if you can load grub as described above from the live disc. I have not tried this yet, but I don't see why it wouldn't work. 

I don't think I remember how to do it in ubuntu. I think you have to load the live disc, and manually load grub from the command line.

---

### Post by tgalati4 on 2007-12-02
Check your device naming scheme.  Perhaps /dev/sda1 versus /dev/hda1?

---

