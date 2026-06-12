---
title: "Synaptc32 in chroot startup error message"
date: 2006-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-02-01
Every time I open Synaptic32 from chroot I get a popup containing the following:
```
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20amd64%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20amd64%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
```
The computer is Ubuntu-64 Breezy with a chroot environment. I don't understand the references to Hoary.

If I just close the window I can continue as though nothing was wrong. But error messages disturb me, especially ones that are written in Geeklish. :)

Any ideas what's wrong?

---

### Post by slavik on 2006-02-01
edit the repo list and comment out the lines that have that ...

it is looking for hoary repo on the cdrom, which it doesn't find. :)

---

### Post by John Jason Jordan on 2006-02-01
[QUOTE=slavik]edit the repo list and comment out the lines that have that ...
it is looking for hoary repo on the cdrom, which it doesn't find. :)[/QUOTE]
That did it. Problem solved. Thanks!

---

