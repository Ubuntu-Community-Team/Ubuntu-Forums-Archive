---
title: "9550SXU Alternating"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by benjamintm on 2007-12-05
Hi All,
I'm running into a bit of a problem.  I have a dual Xeon system running 7.10 64bit with a 3ware 9550SXU RAID controller.  I have a 3 drive setup, one drive connected to the on board SATA port and the other two connected to the RAID Controller in a RAID1 configuration.  Everything works and I have successfully installed 7.10 and my needed software, but every time I reboot, the RAID switches from sda to sdb (or vice versa) depending on what it was before the reboot.  The plays havoc with my mounting of the RAID drive to a mount point.

Any suggestions for a fix or has anyone seen this before?

Thanks,
Ben

---

### Post by njparton on 2007-12-05
How wierd - my 9560SE is fine (although that's little consolation to you).

I can only guess that your BIOS is changing some PCI or IRQ settings each time you reboot?

Try upgrading your BIOS to the latest available and try your 3ware card in a different slot in case the one you've chosen has irq conflicts.

I had an analogous issue with my onboard LAN at one point in that the mac address changed after each reboot. To cure it I fixed the mac address via a config file, I wonder if there's something similar you could do in fstab?

Does the UUID for the array change on each reboot?

---

### Post by njparton on 2007-12-05
PS, you could also trying downloading and compiling the latest 3ware drivers into your kernel.

---

