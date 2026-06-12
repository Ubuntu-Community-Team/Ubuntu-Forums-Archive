---
title: "delete chroot"
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by dannyngweekiat_85 on 2005-12-27
I have install a chroot wrongly. So now i setup another ...well... hope it will go well. So how to delete off the older chroot directory? i have install the new 1 in chroot2 directory.

---

### Post by olivierp on 2005-12-27
[quote=dannyngweekiat_85]I have install a chroot wrongly. So now i setup another ...well... hope it will go well. So how to delete off the older chroot directory? i have install the new 1 in chroot2 directory.[/quote] How about:```
sudo rm -rf /the_old_chroot_directory
``` 
Then, check /etc/fstab for any bind mounts you may have defined. Edit/remove them as necessary

---

### Post by dna on 2005-12-27
sudo rm -r /chroot ?

edit:
olivierp beat me to it.

---

### Post by dannyngweekiat_85 on 2005-12-27
haha...
thx both of u guys... got it runnin now..

---

