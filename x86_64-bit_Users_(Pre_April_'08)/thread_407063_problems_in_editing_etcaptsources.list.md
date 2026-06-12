---
title: "problems in editing /etc/apt/sources.list"
date: 2007-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruhestörer on 2007-04-11
well, 
i tried to gain read write access to my former vista controlled ntfs partitions.
reading is not a problem but the writing, trying to solve this i read much and i found solutions "theoretically" but allready the first step failed. i had to edit the sources.list 
(i added: "deb [http://ntfs-3.sitesweetsite.info/ubuntu/](http://ntfs-3.sitesweetsite.info/ubuntu/) edgy main" and " deb scr [http://ntfs-3.sitesweetsite.info/ubuntu/](http://ntfs-3.sitesweetsite.info/ubuntu/) edgy main ) then when i tried to update my system using sudo  apt-get update the console told me the following:
E: type >> deb-scr << is unknown 
but i don't know why 
pls help

---

### Post by Kilz on 2007-04-11
try deb-src :D

---

### Post by ruhestörer on 2007-04-12
I did, i just missed the "-" out in my description sry
but it still tells me deb-scr is unknown

---

