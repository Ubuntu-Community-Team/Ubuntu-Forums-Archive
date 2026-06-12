---
title: "Problems installing intersystems Caché 2007.2 for MultiValue on ubuntu 7.10"
date: 2008-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by tameritoke on 2008-02-27
Hi people! 
I tried to install the intersystems Caché Database 2007.2 MultiValue and the installation doesn't proceed or end successfully. 

I receive the error message on the screen: 

[HTML]
Unable to allocate 52 MB shared memory...
Unable to allocate 52 MB shared memory...
Unable to allocate 52 MB shared memory...
Configuring minimum system...
Unable to allocate 36 MB shared memory...

Allocating shared memory
Cache: Invalid argument
Cache failed to start.
Check if shared memory requirements exceed system resources.
Call InterSystems Technical Support if you need assistance.

** Installation aborted **
[/HTML]

Can somebody help me further? 

Tamer

---

### Post by spurty on 2008-06-25
Its saying that you have insufficient shared memory.

you can fix this like so:

sudo sysctl -w kernel.shmmax=256000000

or a more permanent solution, add this line at the end of /etc/sysctl.conf 

# ISC tweak for shared memory
kernel.shmmax = 256000000

I'd clean up that install and try again after you have given yourself some more shared memory.

---

