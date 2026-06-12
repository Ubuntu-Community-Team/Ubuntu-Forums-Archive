---
title: "Dapper 64 hangs at reboot when attached to JBOD"
date: 2006-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by tabweb on 2006-08-01
I have a 12 Disk Adaptec storage array attached to my 6.06 64-bit server. Everything installed fine. I have fiber-channel, and another scsi adapter hoooked up that work fine. After configuring all 12 devices with mdadm, I noticed problems. 

Whenever I reboot, the system hangs right after 'decompressing linux...booting kernel' If I detach the JBOD, the system boots fine. Everything with mdadm seems to be working when the system is up. I think it's a problem with syncing, the kernel, or termination? 

I have removed mdadm, stopped multipath, stopped scsitools and lvm but it still hangs. I also used dd to clear out the superblocks of all 12 drives. 

Has anyone experienced this problem or does anyone have any suggestions that may help?

Thanks

---

### Post by tabweb on 2006-08-02
After compiling new kernel for dapper, 2.6.17.7, and modifying some of the LSI mpt fusion controller settings the systems is now rebooting fine. setting the card devices to 80mbs (really 160) stopped the card and system from trying to iniate mptbase ioc recovery.

Only problem I am having now is with scsidev. It starts and creates /dev/scsi but it doesn't create the device list in that dir and I need to manually run scsidev.  Is anyone familiar with scsidev and might have a suggestion?

---

