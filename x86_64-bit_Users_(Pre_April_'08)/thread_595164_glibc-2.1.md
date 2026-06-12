---
title: "glibc-2.1"
date: 2007-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mayhemproject on 2007-10-28
When I attempt to install the Enemy Territory .run file it comes up with this

> 
enemyterritory@Rawr:~> ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
This installation doesn't support glibc-2.1 on Linux / x86_64
(tried to run setup)
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
The setup program seems to have failed on x86_64/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
enemyterritory@Rawr:~> 



Does anyone know how to fix this?

---

### Post by Yellow Pasque on 2007-10-28
Just a shot in the dark...

Try installing the old version of libglib? (libglib1.2)

---

