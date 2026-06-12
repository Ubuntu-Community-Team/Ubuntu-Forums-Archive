---
title: "New install preperation"
date: 2005-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by psoulocybe on 2005-04-09
I'm installing this afternoon on my new A64 3000+ system.

I'm wondering if there are any tricks I should know about for optimizing my 64bit lifestyle.

I'll mostly just be playing w/ this box, as it's my dual boot machine...

---

### Post by c_dog on 2005-04-10
As long as it's dual boot and you going to play; set up a extra partition the rsync backups of the 32 and 64 bit patitions to every now and then or with a cron job. That way you can play around and break stuff to your hearts content then rysnc an unbroken backup back over the mess.
```
rsync -a -v /source_partition/ /destination/
```  to backup
```
rsync -a -v /destination/ /source_parttion/
```  to restore

---

