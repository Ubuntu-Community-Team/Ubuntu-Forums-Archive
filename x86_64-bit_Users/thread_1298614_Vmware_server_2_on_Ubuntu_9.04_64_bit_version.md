---
title: "Vmware server 2 on Ubuntu 9.04 64 bit version"
date: 2009-10-23
forum: x86 64-bit Users
---

### Post by nubber7 on 2009-10-23
Hello,

   While trying to install Vmware I am getting the following error. Can some one tell what to do to make Vmware to work. 

File: VMware-server-2.0.1-156745.x86_64



@ubuntu:~/Vmware/vmware-server-distrib$ sudo ./vmware-install.pl
This version of "VMware Server" is incompatible with this operating system.  
Please install the "i386" version of this program instead.

Execution aborted.

---

### Post by nubber7 on 2009-10-23
Can Any one help me this error?

---

### Post by dabl on 2009-10-23
It looks like you have downloaded a the wrong architecture of VMware.  You appear to be running a 32-bit OS, and trying to install a 64-bit VMware package.  :confused:

---

### Post by nubber7 on 2009-10-23
It is a Intel Quad Core 64 bit processor.


----

Closing this thread I as I have started a new thread in a similar kind of issue.

"Vmware instalation failing with "Unable to build the vmmon module.""

---

### Post by Zafrusteria on 2009-10-24
You may well have a 64-bit processor but it would seem that you have installed the 32-bit version of Ubuntu :)

The output from the following command should have **x86_64 GNU/Linux** at the end if you are running 64 bit.

```
uname -a
```

If you do not see that then you are indeed running the 32-bit version of Ubuntu.

---

### Post by saphil on 2009-10-24
You may also have downloaded the AMD-64bit, which intel machines (often) spit out.  I have had the same issue with an Intel core2 duo chip when I accidentally get the AMD version..  This is made all the more difficult because many packages are not labeled well.

Also, Ubuntu installed the 64 bit update automatically, even though I had only the 32-bit cd when I did the clean install on the new machine.

---

