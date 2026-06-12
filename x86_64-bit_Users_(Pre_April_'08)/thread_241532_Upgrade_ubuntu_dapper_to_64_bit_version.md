---
title: "Upgrade ubuntu dapper to 64 bit version"
date: 2006-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by shazbot on 2006-08-22
hello I have been running linux since the dapper version on my laptop, but my laptop is a Turon 64 amd I was wondering if I can 'just' upgrade it to the 64 bit version 

and if it does not work can I downgrade / keep  32 original version somehow ??

thanks

---

### Post by Kilz on 2006-08-22
> **shazbot said:**
> hello I have been running linux since the dapper version on my laptop, but my laptop is a Turon 64 amd I was wondering if I can 'just' upgrade it to the 64 bit version 

and if it does not work can I downgrade / keep  32 original version somehow ??

thanks

No, and if you have an already working 32bit setup I advise to leave it alone. You can install another 64bit partition and use the same swap space if you have room on your hard drive. That way if you dont like it all you have to do is remove it and your 32bit install will be unharmed.

---

### Post by shazbot on 2006-08-22
Thanks as still a newbie how do I install a second version ??

I have a winXP partion and of course Dapper, both on the same grub, Can I just start the install procedure from the 64bit ISO, creat a new partion et if so will the the grub be added to the existing grub ??

All done, 64 bit installed and on the smae grub :)

Thanks

---

### Post by Kilz on 2006-08-22
> **shazbot said:**
> Thanks as still a newbie how do I install a second version ??

I have a winXP partion and of course Dapper, both on the same grub, Can I just start the install procedure from the 64bit ISO, creat a new partion et if so will the the grub be added to the existing grub ??

All done, 64 bit installed and on the smae grub :)

Thanks

It should be on the grub in the 64bit install, but everything will be avaiable. If you ever remove the 64bit partition you will have to put your i386 install disk in to fix it. It will do it for you when you select recue installed system.
At least this way you can go slowly and do what you want to do without having to worry about messing a working install up.

---

