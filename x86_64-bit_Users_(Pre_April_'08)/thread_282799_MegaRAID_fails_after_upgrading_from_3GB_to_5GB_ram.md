---
title: "MegaRAID fails after upgrading from 3GB to 5GB ram on dual opteron"
date: 2006-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by dpopeck on 2006-10-23
Hi all,

I have an interesting problem with a Megaraid controller.

For the last 3+ months I have been running a Fujitsu-Siemens R220 server with a 8 port MegaRAID SATA 300-8X controller. There are only 2 drives attached, both 250GB and running as a mirror pair.
The machine has 2 opteron 246 processors and 3GB of ram.

Everything has been fine until I tried to upgrade the machine to 5GB ram.

At this point the machine came up with a dozen or so scsi errors before panicing because it was unable to mount the root file system.

There is a BIOS option to do with remapping memory around the PCI address space. This gives me either 4 1/2 GB usable or 5 GB usable. Either way I still get the same errors.

Taking the extra 2 GB out of the machine gets everything working again.

Does anyone have any ideas on this? I'm a bit stuffed for playing with this because its now, after 2 months flawless testing, a production machine running VMware server. 

Help!

TIA

David

---

