---
title: "VT-x"
date: 2008-06-30
forum: x86 64-bit Users
---

### Post by sl1mshadyx on 2008-06-30
Hello, I'm currently using hardy amd64 (on a Q6600 with 4GB DDR2) and im looking for a VM hypervisor that can support VT-x with x86_64. 
I tried VirtualBox (non-free edition) but when i enable VT-x it crashes, i thought it was that the guest OS (FreeBSD 7) was 32 bit, so i downloaded the x86_64 version of FreeBSD 7 and it crashes too... Does VMware server support VT-x on x86_64? I think Xen is too complicated for my needs...

I'd appreciate some advice :) thanks!

edit: found something relevant @ virtualbox.org:
[http://forums.virtualbox.org/viewtopic.php?p=21852](http://forums.virtualbox.org/viewtopic.php?p=21852)
its supposed to be fixed in 1.6.2 (the version i have) but its not :(
also, when i boot (FreeBSD 7 i386 or x86_64 its the same) i get a 
"00:00:29.503 Guest Log: BIOS: int13_diskette: unsupported AH=41" error and it hangs...

edit2: the problem was FreeBSD -_- , installing Windows XP right now with VT-x enabled, no problems so far (CentOS 5.2 booted fine too)

---

### Post by pixel :-) on 2008-07-01
download a virtual hard disk with freebsd alredy installed.Also try deactivating various emulated hardware.

---

