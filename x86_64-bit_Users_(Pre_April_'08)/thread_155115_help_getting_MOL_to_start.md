---
title: "help getting MOL to start"
date: 2006-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuntubrian on 2006-04-04
I followed all of the howto on the wiki for MOL and everything worked-no errors at all. Kernel headers match and everything. When I trued starting mol I got:
sudo startmol -X
Mac-on-Linux 0.9.70 [Jul 23 2005 19:20]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
FATAL: Module mol not found.
====================================================================
  Failed to load the Mac-on-Linux kernel module -- please install
  mol-modules-source and build your own, or find a binary package
  providing mol-modules for your running kernel.

So I used the pre-compiled kmod @ [http://www.petrvz.net/~pvz/mol/](http://www.petrvz.net/~pvz/mol/)
and installed it with dpkg
I still get the same error of module mol not found. Any ideas?

Thanks

---

### Post by ubuntubrian on 2006-04-04
I restarted and everything works fine!

---

