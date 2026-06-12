---
title: "Error Compiling Driver"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by g12345567 on 2006-03-08
Im trying to compile the Ralink RT2500 driver for use with Ubuntu 5.10 on my g3 powermac.

I have followed the instructions here
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig) 
and installed the required build essentials and gcc-3.4 files successfully.
But when it comes to running MAKE I get the following error message

make: *** /lib/modules/2.6.12-9-powerpc/build: No such file or directory.  Stop.
rt2500.ko failed to build!
make: *** [module] Error 1

Just wondering what files or modules I am missing and how to fix the problem I am having.

---

### Post by Sutekh on 2006-03-08
Did you install the relevant linux-headers?

```
uname -r
```Will tell you your current kernel.

I imagine it is 2.6.12-9-powerpc, so you need the package **linux-headers-2.6.12-9-powerpc**.  They should be on the PPC install CD.

---

### Post by g12345567 on 2006-03-08
[QUOTE=Sutekh]Did you install the relevant linux-headers?

```
uname -r
```Will tell you your current kernel.

I imagine it is 2.6.12-9-powerpc, so you need the package **linux-headers-2.6.12-9-powerpc**.  They should be on the PPC install CD.[/QUOTE]


I have installed 
2.6.12-10-powerpc

looks like I forgot to install the "linux headers"  (uname -r) componnt when running section 3 when installing the required drivers. Went back and did it again and all went well after that.

---

