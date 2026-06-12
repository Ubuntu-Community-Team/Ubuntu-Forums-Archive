---
title: "can 32-bit and 64-bit share a root partition?"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by srhlefty on 2008-12-18
Hi I was wondering if you can install both versions of Ubuntu to the same root partition.  Do they play nice? Or will some libraries be overwritten?

---

### Post by Kilz on 2008-12-19
> **srhlefty said:**
> [B]will some libraries be overwritten?
[/B]


Some will be,

In the 64bit version /usr/lib holds 64bit libraries
In the 32bit version /usr/lib holds 32bit libraries.

Same with /lib

Libraries that have similar names will be overwritten.

Applications would also overwrite since /bin is just like /lib

---

### Post by bford16 on 2008-12-21
> **srhlefty said:**
> Hi I was wondering if you can install both versions of Ubuntu to the same root partition.  Do they play nice? Or will some libraries be overwritten?
Not really.  As posted above, some of the folders and applications have the same names, so they would be overwritten.  If your machine can handle 64-bit, but you also want to use 32-bit software, then you should probably install 64-bit, and install the 32-bit software individually.

Most 32-bit software has 64-bit versions now, with the exception of Adobe Flash and Java browser plugins.  Adobe recently released an Alpha build of a 64-bit Flash plugin, but it is not ready for prime-time just yet. There is a 64-bit Java plugin on the way as well.

---

### Post by Kilz on 2008-12-21
> **bford16 said:**
>  There is a 64-bit Java plugin on the way as well.

There is a beta 64bit Sun Java plugin, while its not advised for those without troubleshooting skills. The open jdk plugin in the repositories while not Sun, should work for 95% of users.

---

