---
title: "chroot and wine problem"
date: 2005-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by cypher35 on 2005-09-27
Howdy, i am currently trying to set up Wine on my AMD64 setup... Apparently, wine is a 32bit-only application.


I'm somewhat new to linux, so i may have messed up somewhere, but it is my understanding that i need to set up a chroot to get any 32bit apps to run on my system.  I followed the tutorial at [https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html](https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html) and (after a few headaches) managed to set up a chroot at */var/chroot/sarge-ia32/*.  However, i have absolutely no way of knowing weather or not this setup is working because i don't know how i would go about testing it.

Therefore i decided to proceed with my installation of wine.  I used the command *sudo chroot /var/chroot/sarge-ia32* to login to the chroot and typed *apt-get wine*


It appeared to start installing correctly, then halted on this error.  I have absolutely no idea what this means:

[i]dpkg: syntax error: unknown group `Debian-exim' in statusoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)[/i]


any help would be greatly appreciated.

---

