---
title: "jdk on wine - Error"
date: 2012-05-04
forum: Wine
---

### Post by Mohitgarg on 2012-05-04
I am struggling since past 2 days in trying to install jdk (64 bit) from [http://www.java.net/download/jdk6/6u32/promoted/b02/binaries/jdk-6u32-ea-bin-b02-windows-amd64-30_jan_2012.exe](http://www.java.net/download/jdk6/6u32/promoted/b02/binaries/jdk-6u32-ea-bin-b02-windows-amd64-30_jan_2012.exe)

on my wine. Initially I tried it on Ubuntu 12.04. I installed wine1.4-amd64 in hope that it would execute the jdk exe but it did not.  So I went for wine 1.4 source installation. I get to know that the dependency check is not yet documented on the winehq website for 12.04 so I made the installation on a fresh virtual machine with ubuntu 10.04. 

Installation went well but still wine64 is still not able to install jdk. My command is:

```
wine jdk-6u32-ea-bin-b02-windows-amd64-30_jan_2012.exe

```
The output is :
```
fixme:heap:HeapSetInformation 0x2c4000 0 0x22fce0 4
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll._local_unwind, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
wine: Call from 0x7f3f4ff57048 to unimplemented function KERNEL32.dll.__C_specific_handler, aborting
err:seh:setup_exception stack overflow 2704 bytes in thread 0025 eip 00007f3f4ff489bb esp 0000000000130b70 stack 0x130000-0x131000-0x230000
```

Any help please?

---

### Post by Mohitgarg on 2012-05-04
One thing I forgot to mention, my machines are 64 bit.

---

### Post by thatguruguy on 2012-05-04
Just out of curiosity, why not use the native JDK for Linux?

---

