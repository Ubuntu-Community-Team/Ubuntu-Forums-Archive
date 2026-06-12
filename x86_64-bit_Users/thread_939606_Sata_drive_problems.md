---
title: "Sata drive problems"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by briancb on 2008-10-06
Ok tried everything spent hours trying to get Nvidia drivers reinstalled after deletion, gave up reinstalled Ubuntu but now will not boot up with sata drive attached.

I have 2 drives one is IDE and the other is IDE with a sata adapter.

I have Hardy on the sata connection and Intrepid on the IDE. I have reconfigured the grub to access Hardy but to access Intrepid I have to disconnect the sata drive.

Any ideas?

---

### Post by briancb on 2008-10-07
Ok I have solved this for me.

This problem only occurs in 8.04.1 and 8.10

so I downloaded 8.04 64bit and installed that no problem. Updated everything.

integrated my home folder from previous install

ran 
chmod 644 .dmrc
chmod 700 ~

everything worked including Skype.

so I now have to be brave enough to upgrade to 8.10 but will leave that a little while longer.

---

