---
title: "[SOLVED] Feisty Raid 1 Boot Problem after Kernel Upgrade"
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by PaulRSte on 2007-11-14
In order to get my system to boot after converting to RAID 1, see [http://ubuntuforums.org/showthread.php?t=515594](http://ubuntuforums.org/showthread.php?t=515594) I had to remove the UUIDs from menu.lst and replace them with paths such as /dev/md0.  Subsequent upgrades cause menu.lst to be edited and revert back to using UUIDs, which again causes the system not to boot.  I have to edit menu.lst and replace the UUIDs with /dev/md0 etc.

There is a known issue here and something to do with #groot I think, but I haven't seen how to correct this issue once and for all.

Basically I want to update to Gutsy as this should cure a couple of issues with my system but I don't know how the upgrade process will cope with my menu.lst.

Can anyone help please

---

### Post by jpkotta on 2007-11-14
You need to edit kopt as well.  See [GrubHowTo]("https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668").

Here is the relevant part of my menu.lst.  I have a RAID 1 /boot partition.
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dcfff082-0b76-45cc-9288-80383392a753 ro
# kopt_2_6=root=/dev/md1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

```

Apparently, it only looks at the kopt_2_6, because the kernel entries have /dev/md1 instead of the UUID.

BTW, you should use the alternate install CD when installing to a RAID array.  I made the mistake of trying to install to a single disk and create the array afterwards, and it was much more complicated than it needed to be.

---

### Post by PaulRSte on 2007-11-16
jpkotta

Thanks for the reply, very informative, and the link to the GRUB Howto was very informative as well.  I can see now where the UUID is coming from.  This must have been the original UUID that the system was first built with.  As the partition has been recreated it will now have a different one presumably?

My main query now stems from my lack of understanding of the boot prrocess, i.e. which UUID should be quoted in menu.lst?  Is it that of the raw partition (sda1) or is it that of the raid array, md0?

Many thanks

Paul

---

### Post by jpkotta on 2007-11-16
The UUID and the device node in my listing refer to the same device, the RAID array that my root fs is on.  Honestly, I wouldn't bother with the UUID.  Just make kopt and kopt_2_6 the same and use the device node for your root fs partition.

---

### Post by PaulRSte on 2007-11-18
Thanks for that.  Have amended the UUID in the menu.lst to the correct UUID for md0 and then run update-grub.  This, as expected, set the correct UUIDs and the system rebooted ok.

I've left the UUID in rather than specify /dev/md0 as I want to update to gutsy and I'm assuming that this will want to use UUIDs.

Again, many thanks for the explanation.

---

