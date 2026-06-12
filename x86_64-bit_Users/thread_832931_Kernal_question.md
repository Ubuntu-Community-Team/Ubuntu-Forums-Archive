---
title: "Kernal question"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by redbrain on 2008-06-18
Is it possible to take the 32bit ubuntu jeos server, and re-complile the kernal inside to be 64bit ?!

---

### Post by Mizzou_Engineer on 2008-06-18
> **redbrain said:**
> Is it possible to take the 32bit ubuntu jeos server, and re-complile the kernal inside to be 64bit ?!

No. A 32-bit OS has a 32-bit userland and 32-bit build tools. Yes, you can do things like boot with a 64-bit live CD and make a chroot to build a 64-bit kernel on that machine, but you are much better off just installing the 64-bit version of Ubuntu Jeos. If there is not a 64-bit version available (there may not be, I am not familiar with Jeos), you *can* take the source for the entire OS and compile it under a 64-bit Linux to make 64-bit .deb files, then remaster the install disk to make a custom, completely 64-bit version of Jeos.

---

### Post by redbrain on 2008-06-19
thats quite an intereasting solution i might give that a try, just to my mind was kind of confused because like i didnt think it would be possible like compiling 64bit inside a 32bit systems beacuse all the c libs and gcc would all just be 32bit but how do you get the source for the entire ubuntu jeos? is it in an svn branch or something?!

---

### Post by Mizzou_Engineer on 2008-06-19
> **redbrain said:**
> thats quite an intereasting solution i might give that a try, just to my mind was kind of confused because like i didnt think it would be possible like compiling 64bit inside a 32bit systems beacuse all the c libs and gcc would all just be 32bit but how do you get the source for the entire ubuntu jeos? is it in an svn branch or something?!

You should be able to get the source off the Ubuntu FTP/HTTP file server as everything is GPL and letting people have the source is a requirement of that license.

---

