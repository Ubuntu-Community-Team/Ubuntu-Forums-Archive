---
title: "E521, Athlon 64 X2
Dell E521, Athlon 64 X2 3800+ Memory Problems"
date: 2007-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by jason_d on 2007-04-18
I'm trying to add ram to my Dell E521.  I'm running Drapper Drake.  
The machine came with 1GB (2 512mb sticks in slots 1 and 2) and has been running without problems since I bought the machine 6 months ago.  I recently bought 2 1gb sticks and placed them in slots 3 and 4.  The machine booted up without problem and Ubuntu seemed to recognize that 3gb is installed in the system.  However, the network doesn't work - I can ping localhost but cannot ping any other machines on the local network.  Ifconfig displays the same output as before the memory was installed.

I've tried many different memory configurations, and the common thread seems to be that if the machine has more than 1GB installed, the network interfaces stop working properly.  Occasionally X doesn't start up properly either.  With exactly 1GB installed (with the 2 512mb sticks or with one of the 1GB sticks installed), there are no problems.  I've also tried other configs, such as putting 1GB in slot 1 and the other GB stick in slot 3, but to no avail.

I'm by no means a linux expert, so I'm not sure where to start troubleshooting here.  I've checked the /var/log directories, but nothing stands out.  

Any advice would be greatly appreciated.

---

