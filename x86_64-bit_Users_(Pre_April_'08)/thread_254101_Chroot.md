---
title: "Chroot"
date: 2006-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-09-09
How do you safely uninstall Chroot?

---

### Post by kidders on 2006-09-09
Can I ask why you would want to?

Uninstalling **chroot** is ill-advised, unless you're *really* certain you have no intention of using anything that might like it to be there.

---

### Post by Mongoose on 2006-09-09
I think he means a chroot eg '/var/chroot/', and not the package.  In that case you can just remove the directory and remove the entry from /etc/dchroot.conf. 

Are you sure that's what you want?

---

### Post by Kilz on 2006-09-09
[There is a script that can help setup a chroot.]("http://www.ubuntuforums.org/showthread.php?t=157412") I used it once when I just started using Ubuntu. This was before learning that the the things I wanted didnt need one to be installed in Dapper.

---

