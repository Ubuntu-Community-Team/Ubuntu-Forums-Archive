---
title: "downgrade 64b to 32b?"
date: 2005-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by bahbo on 2005-10-22
Hi,
A long time ago I installed Hoary on a partition, but didn't use it much.  I thought it was 32bit Hoary, but after upgrading to Breezy I notice that my kernel is an amd64 kernel.  Is there a way to determine if I have the 64b or 32b libraries?  And if I have a 64b machine, is it possible for me to change over to a 32b system without a completely new install?  If so, how would I go about doing that?  I want to have this partition be 32b so that everything will work without a chroot.
Thanks,
Ric

---

### Post by RAOF on 2005-10-23
Well, my install has "lib32" and "lib64" directories/links under /

If you do "ls /" and find the lib64 directory shown, it's a pretty fair bet that you've got the 64bit libraries installed.

Failing that, you can use "readelf -h" to work out the version of an (ELF) binary.  Pick some lib in your /lib directory (I used readelf -h /lib/libattr.so.1) and it'll spit out all sorts of stuff about that binary, including
```
  Class:                             ELF64
...
  Machine:                           Advanced Micro Devices X86-64

```
Showing that mine is a 64bit lib.

If you do have a 64bit install there, the easiest way to get a 32bit install is just to do a new install.  If you copy over your home directory, that will preserve almost all of your current settings.

---

### Post by jon_gunnar on 2005-10-23
[QUOTE=bahbo]Hi,
A long time ago I installed Hoary on a partition, but didn't use it much.  I thought it was 32bit Hoary, but after upgrading to Breezy I notice that my kernel is an amd64 kernel.  Is there a way to determine if I have the 64b or 32b libraries?  And if I have a 64b machine, is it possible for me to change over to a 32b system without a completely new install?  If so, how would I go about doing that?  I want to have this partition be 32b so that everything will work without a chroot.
Thanks,
Ric[/QUOTE]

jon@irda:~$ uname -r
2.6.12-9-amd64-generic

---

### Post by bahbo on 2005-10-23
Thanks,
I do have both lib32 and li64 (linked to lib) in /, and uname -r gives me 
2.6.12-9-amd64-k8
so I guess I have the amd64 version install.  Fortunately I have home in separate partion, so it won't be too difficult to do a fresh install.
Thanks,
Ric

---

