---
title: "K3b Problem.."
date: 2008-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chris P. Bacon on 2008-03-30
When I try to burn an ISO Image which is larger than 4 GB K3b just says " not enough space on device" but there is 4,7 GB on the device. 
  I know this error pops up due to some mechanism who refuses you to burn images larger than 4 GB, but how do I overrule it? 

Kthx

---

### Post by majnun on 2008-03-31
> **Chris P. Bacon said:**
>   I know this error pops up due to some mechanism who refuses you to burn images larger than 4 GB, but how do I overrule it? 

Kthx

and how do you know that? Not joking, I'd like to know ...

could you post the results of a df -h command?

anyway if it was my machine, I would free some space on disk if it were possible

FAT32 filesystems don't allow files bigger than 4GB ...is that your case?

---

### Post by Chris P. Bacon on 2008-03-31
This is how I know:

[http://grigio.org/how_burn_file_4gb_dvd_udf](http://grigio.org/how_burn_file_4gb_dvd_udf)

But i cant figure out how to get that setting panel, i'm using K3b 1.0.4

Btw... The device i'm burning it to is a 4.7Gb DVD-R disk...

---

### Post by majnun on 2008-03-31
excuse me, I've understood you were doing an ISO image ...maybe you have no space on the hard disk and k3b needs to prepare the iso image first?

this setting panel appears when you click "burn", I can get it normally :-)

---

