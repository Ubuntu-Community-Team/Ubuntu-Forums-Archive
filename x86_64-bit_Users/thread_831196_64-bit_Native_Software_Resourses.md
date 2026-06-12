---
title: "64-bit Native Software Resourses"
date: 2008-06-16
forum: x86 64-bit Users
---

### Post by alexus2005 on 2008-06-16
Hi everyone,

I am using Ubuntu on AMD 64-bit patform and have been facing a problem of absence of native 64-bit software. Ususally I was using Google and downloads.com to find some 64-bit native apps... and also I've found nice website about 64-bit native software: [www.64xsoft.com]("http://www.64xsoft.com").

Would be nice to have some more links to good resourses here. Thank you.:popcorn:

---

### Post by stchman on 2008-06-16
> **alexus2005 said:**
> Hi everyone,

I am using Ubuntu on AMD 64-bit patform and have been facing a problem of absence of native 64-bit software. Ususally I was using Google and downloads.com to find some 64-bit native apps... and also I've found nice website about 64-bit native software: [www.64xsoft.com]("http://www.64xsoft.com").

Would be nice to have some more links to good resourses here. Thank you.:popcorn:

The software in the Ubuntu repos is 64 bit.  Now I don't know if the code has been reworked to include new memory addresses and such.

I suspect a lot of the software was simply recompiled using a 64 bit compiler.

More importantly I would like for software to be multiple processor aware and if a quad core is present there will be multiple threads used in the code to take full advantage of the hardware.

As now most of the new processors are 64 bit multi core lets have the software take advantage of all that power.

---

### Post by cariboo on 2008-06-16
Go to System-->Administration-->Synaptic Package Manager and peruse the list of packages all of them are compiled for the amd64. Most of the programs are also multi processor aware. Smp has been an option in the kernel for years. I used my first dual processor computer back in 1990 it had dual 233Mhz processors and 128mb of 30 pin ram. The kernel back then was 2.2.

As aside in a terminal type:

```
uname -a 
```

The result should be:

```
Linux intrepid 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux
```

note the smp

Jim

---

