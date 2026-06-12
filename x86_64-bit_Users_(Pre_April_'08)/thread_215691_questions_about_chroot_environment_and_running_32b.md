---
title: "questions about chroot environment and running 32bit"
date: 2006-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2006-07-14
I followed howto for version 5.05 and was able to come up with working dapper 32bit chroot. I have some stuff now in 32bit like firefox or synaptic but that's more or less that.

I would like to use it for games but I am just wondering about the x and particularly ati-drivers? Do I need to install the drivers once more for 32bit under dchroot -d? I did not try glxgears or anything yet I just tried to install one game which crashed immediately complaining about the glx...

Has any doom-enthusiast or alike any experience with this? What steps are necessary.

---

### Post by Kilz on 2006-07-14
> **Saubazi said:**
> I followed howto for version 5.05 and was able to come up with working dapper 32bit chroot. I have some stuff now in 32bit like firefox or synaptic but that's more or less that.

I would like to use it for games but I am just wondering about the x and particularly ati-drivers? Do I need to install the drivers once more for 32bit under dchroot -d? I did not try glxgears or anything yet I just tried to install one game which crashed immediately complaining about the glx...

Has any doom-enthusiast or alike any experience with this? What steps are necessary.

You will probably have to because a chroot is a operating system inside an operating system. But just fyi chroot's are not as nessasary for dapper as they were for breezy. But if you plan on adding tons of 32bit programs that there isnt a 64bit version it may be for the best. But Im not sure there are that many.

---

### Post by Saubazi on 2006-07-16
Mmmm...I tried installing ati-drivers under chroot but failed miserably. Does anyone know how to accomplish this. I managed to get my app running directly from 64bit env by just copying the necessary libs from /chroot/usr/lib to /usr/lib32 but I still have some further ideas I'd like to try...

---

### Post by Kilz on 2006-07-16
> **Saubazi said:**
> Mmmm...I tried installing ati-drivers under chroot but failed miserably. Does anyone know how to accomplish this. I managed to get my app running directly from 64bit env by just copying the necessary libs from /chroot/usr/lib to /usr/lib32 but I still have some further ideas I'd like to try...

You could simply install the 32bit applications to the 64bit env like a lot of us do with dapper.

---

### Post by Rhaurison Bergamin on 2006-07-22
Let us know the error from application when you have tried run. Put it here.

---

