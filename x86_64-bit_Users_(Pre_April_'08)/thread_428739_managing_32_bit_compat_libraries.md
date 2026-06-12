---
title: "managing 32 bit compat libraries"
date: 2007-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by skullmunky on 2007-04-30
i have an athlon 64 x2, using ubuntu edgy and soon feisty.  i'd really like to run in 64 bit because the work i do - 3D and multimedia - does get a real speed boost in 64 bit.  (i kind of doubted it for a while, actually, then benchmarked 64 bit maya/mental ray vs 32 bit, and what do you ?  almost exactly twice as fast.  son of a gun.  ) 

but, i also need flash 9 and java in firefox, and more importantly also frequently need to build 32 bit applications and 32 bit .dso's for other proprietary apps that are still in 32bit.  so, i need to have 32 bit libs for a lot of things.  

now, my question is, can i manage that nicely in synaptic?   i keep running into problems where synaptic will only let me install 32 OR 64 bit versions of packages, but not both.  trying to install a 32 bit version makes it try and de-install the 64 bit version, dependency errors ensue, etc, etc. 

thanks,

skullmunky64

---

### Post by kuja on 2007-04-30
You'd have to edit one of the packages to have a different name, and preferably a different installation path (so they don't conflict). appending something like 32 on the end of a package and changing it to place things in /usr/lib32 instead of /usr/lib and appending 32 to the end of binaries should do the trick without too much work.

---

### Post by Kilz on 2007-04-30
> **skullmunky said:**
> i have an athlon 64 x2, using ubuntu edgy and soon feisty.  i'd really like to run in 64 bit because the work i do - 3D and multimedia - does get a real speed boost in 64 bit.  (i kind of doubted it for a while, actually, then benchmarked 64 bit maya/mental ray vs 32 bit, and what do you ?  almost exactly twice as fast.  son of a gun.  ) 
Nice to know, yet another application that gets a boost.

> **skullmunky said:**
> but, i also need flash 9 and java in firefox, and 
  See my signature, kuja also makes a nice application called simple 64 that can install them.

> **skullmunky said:**
> more importantly also frequently need to build 32 bit applications and 32 bit .dso's for other proprietary apps that are still in 32bit.  so, i need to have 32 bit libs for a lot of things.  
You might want to set up a chroot if you do a lot of 32 bit, or setup vmware server and install a 32bit vm.

> **skullmunky said:**
> now, my question is, can i manage that nicely in synaptic?   i keep running into problems where synaptic will only let me install 32 OR 64 bit versions of packages, but not both.  trying to install a 32 bit version makes it try and de-install the 64 bit version, dependency errors ensue, etc, etc. 

thanks,

skullmunky64

As far as I know you cant install 32bit applications and libraries with synaptic on a 64bit install, except a very few packages specifically with them labeled ia32

---

### Post by ronacc on 2007-04-30
it is possible to do multi arch builds I saw something about it but I don't remember where , sorry.

---

