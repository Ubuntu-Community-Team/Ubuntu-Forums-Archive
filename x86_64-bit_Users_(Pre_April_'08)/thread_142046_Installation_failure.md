---
title: "Installation failure"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by rtl on 2006-03-09
After running the LiveCD and its memtest for a couple of days w/o a problem I decided to bite the bullet and install Ubuntu on my asus a8n-sli premium (athlon 4800+, 4GB ram & 4*160MB SATA2). Unfortunately any combination of s/w RAID I tried during installation always failed to complete the partitioning/formatting phase, so I tried installing on one of the drives in non-raid mode, which completed successfully, but fails to (re)boot, the bios failing to find a boot device. This box has had FreeBSD on it for a while (but it has problems with the 4GB ram - see my other posts to this forum, if interested), so I'm confident there are no h/w issues. 

Any help/pointers would be gratefully accepted!

Robert

---

### Post by rtl on 2006-03-11
I've managed to complete the installation now, so I thought I'd describe the problems for anyone else with a similar issue.

The main problem of not being able to boot, even after installing on a single, non-raid drive was because the first SATA2 drive reported by the bios was not the first drive found by the installer, with the result that grub ended up being installed on the drive listed third by the bios. Once I'd told the bios to boot from the third sata drive everything worked as expected.

WRT setting up the drives using raid, once I deleted the original raid 0+1 array using the nVidia bios raid setup program, *then* turned it off in the bios, I was able to setup Raid 1 during the install, format it and complete the installation (once again setting the bios to boot from the third sata drive). After trying several different raid setups I ended up using the one described here: [http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

So far I've run a few benchmarks, such as Bonnie++ and all is working well. I'm about to update from the generic to the smp-k8 kernel to take full advantage of the dual core cpu.

---

