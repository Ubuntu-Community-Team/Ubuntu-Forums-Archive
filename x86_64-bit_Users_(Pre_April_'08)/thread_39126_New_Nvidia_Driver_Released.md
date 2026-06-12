---
title: "New Nvidia Driver Released"
date: 2005-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by dom_cyrus on 2005-06-03
hi@all
Anyone installed the new Nvidia drivers? I get some errors about some libs. If someone installed it correctly it would be nice to have a howto. 

thx cu

edit: Also if someone know a solution to enable inotify ==> pls post it :)

---

### Post by rsw on 2005-06-05
This is the error after compiling/installing the 7664 nvidia module:

relocation error: /usr/lib/libGL.so.1: symbol gnu_dev_makedev, version GLIBC_2.3.3 not defined in file libc.so.6 with link time reference

According to the people over at nvnews's linux forum, we need to install glibc-2.3.5. I'm not entirely sure what dist libc6-2.3.5 is apart of, (probably breezy?) but it is there for us amd64 users to grab.

From [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/) I grabbed: 

libc6-dbg_2.3.5-1ubuntu4_amd64.deb
libc6-dev_2.3.5-1ubuntu4_amd64.deb
libc6_2.3.5-1ubuntu4_amd64.deb

..and from [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/)  I grabbed: 

linux-kernel-headers_2.6.11.2-0ubuntu10_amd64.deb



To upgrade to these new packages, you do:

#  dpkg -i libc6_2.3.5-1ubuntu4_amd64.deb libc6-dbg_2.3.5-1ubuntu4_amd64.deb libc6-dev_2.3.5-1ubuntu4_amd64.deb linux-kernel-headers_2.6.11.2-0ubuntu10_amd64.deb


Doing glxinfo & glxgears works, I've not tested with an actual game or checked for general system stability yet. I installed this on a custom built 2.6.11.11 kernel (athlon64/opteron/k8).

Please post if you have problems or success. I'm going to see if the lovely "no-symbols-bug" is still alive and well with this release (it should be, as it is a bug in xorg, not nvidia's module).

---

### Post by rsw on 2005-06-05
well, ut2004 works. I see no performance increases, however.

Doom3 is broken, and I bet it has to do with the conflicts encountered when you choose to install the 32bit compatibility libs during the nvidia install. This causes the entire installation to "fail", yet the installer leaves the modules & stuff in the right places... just, well, you know.. broken if you need to use the 32bit compat libs (and I assume d3 does since it's a 32bit exe running in a 64bit os) ;)

No clue on how to fix.

---

### Post by rsw on 2005-06-06
Sigh. No-symbols-bug is in full effect. Back to 2.6.10 & nvidia-glx :(   ](*,)  ](*,)  ](*,)  ](*,)

---

