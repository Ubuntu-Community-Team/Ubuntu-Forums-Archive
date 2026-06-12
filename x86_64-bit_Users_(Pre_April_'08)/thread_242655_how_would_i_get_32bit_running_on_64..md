---
title: "how would i get 32bit running on 64."
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by sunrex on 2006-08-23
Hello, i have just moved to ubuntu again after windows started screwing up.. again, i have nothing against windows other then the fact it keeps blowing up in my face..

anyway i decided to go with ubuntu 64bit this time, How would i get 32bit apps running on 64bit? and is opera out on 64 yet?

---

### Post by mlind on 2006-08-24
> **sunrex said:**
> Hello, i have just moved to ubuntu again after windows started screwing up.. again, i have nothing against windows other then the fact it keeps blowing up in my face..

anyway i decided to go with ubuntu 64bit this time, How would i get 32bit apps running on 64bit? and is opera out on 64 yet?

You probably need run those apps on a 32bit chroot (or using xen maybe?).
Search the forums how to setup 32bit chroot for 64bit system.

---

### Post by Kilz on 2006-08-24
> **mlind said:**
> You probably need run those apps on a 32bit chroot (or using xen maybe?).
Search the forums how to setup 32bit chroot for 64bit system.

Chroots are not nessasary in Daper. Unless you plan on installing development tools or hundreds of 32bit applications. There is no need to insatll that many as there are already 64bit versions for almost everything.  Chroots were needed in Breezy, but not Dapper. I suggest checking the [sticky in the 64bit section]("http://www.ubuntuforums.org/showthread.php?t=191205") out for specific howto's to getting common 32bit applicatins installed. Opera is listed in it.

---

