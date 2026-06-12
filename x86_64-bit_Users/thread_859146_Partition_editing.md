---
title: "Partition editing"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by tzirtzi on 2008-07-14
Hi :)

I'm in the process of installing Windows XP on my computer to dual boot with my existing Ubuntu 8.04 system. I'm using [this guide](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) to do so. However, before I install Windows I want to clear up my partition structure - when I installed Ubuntu I already had some active partitions that I'm no longer using, so there are some funny gaps. Here is a screenshot of my current setup (I also have another internal harddrive, but I'm going to leave that to linux):

[IMG]http://www.superlush.co.uk/images/Screenshot--dev-sda-GParted.png[/IMG]

I want to move my two existing partitions to the beginning of the drive so that there will be a single 132gb empty space into which to install Windows. When I boot the computer with the Ubuntu live CD I can move sda3 using PartEd without problem, but I can't move sda4/5. Is there any way of doing this, or am I stuck with my existing messy setup?

Thanks in advance for any help! :)

---

### Post by stchman on 2008-07-14
> **tzirtzi said:**
> Hi :)

I'm in the process of installing Windows XP on my computer to dual boot with my existing Ubuntu 8.04 system. I'm using [this guide](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) to do so. However, before I install Windows I want to clear up my partition structure - when I installed Ubuntu I already had some active partitions that I'm no longer using, so there are some funny gaps. Here is a screenshot of my current setup (I also have another internal harddrive, but I'm going to leave that to linux):

[IMG]http://www.superlush.co.uk/images/Screenshot--dev-sda-GParted.png[/IMG]

I want to move my two existing partitions to the beginning of the drive so that there will be a single 132gb empty space into which to install Windows. When I boot the computer with the Ubuntu live CD I can move sda3 using PartEd without problem, but I can't move sda4/5. Is there any way of doing this, or am I stuck with my existing messy setup?

Thanks in advance for any help! :)

It would be WAY easier to expand your EXT3 partition to consume that 10GB on the left.  Judging from your EXT3 partition you need the room.

---

### Post by tzirtzi on 2008-07-14
Thanks, that's a good idea. I don't actually need the space as I'm about to move about 50gb worth to a different drive, but I don't suppose 10gb would make much difference to the Windows partition either and if, as you say, it's easier - :) I'll report back as to whether all goes well.

---

### Post by Kilz on 2008-07-14
Another option is to copy the swap partition and then delete the original. If you do that make sure to copy down the location because you may have to edit /etc/fstab to tell Ubuntu where to look for swap.

---

### Post by tzirtzi on 2008-07-14
Thanks for the other suggestion :) But I've now successfully resized the sda3 partition. Next to install Windows in the unpartitioned space...

---

