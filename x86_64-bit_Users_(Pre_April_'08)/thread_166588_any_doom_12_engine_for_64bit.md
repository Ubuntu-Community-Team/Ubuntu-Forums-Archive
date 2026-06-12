---
title: "any doom 1/2 engine for 64bit?"
date: 2006-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by siman on 2006-04-26
hi guys,
I miss doom on my amd 64.
I tried compiling deng, prboom, doom legacy... anything, but it wont work

the legacy doom binaries crash with
libXxf86vm.so.1: cannot open shared object file

I've read about this, and the only solution seems to be this chroot32-thing ... I think I don't want to try it :-)

any ideas? any doom-engine I missed?
thx

---

### Post by Jason_25 on 2006-04-26
It's usually just a matter of finding that file and copying it to the /usr/lib folder.  That particular file is from one of the x development packages in synaptic.  Sorry I can't be more specific.  This is the way to get pretty much any 32-bit program working without a chroot.

---

### Post by siman on 2006-04-26
that worked.
I copied a lot of .so-files in the game's directory and changed LD_LIBRARY_PATH

but now its broken because of something else, related to sdl... but merci anyways.

---

### Post by Yagisan on 2006-04-27
I have working deng for am64 packages. (OK I cheat a bit, it is a 32bit package, with support libs.) If you click the link in my signature, and look in community projects you'll find details and instructions for breezy. It may work on dapper, but I haven't gotten around to that yet.

Regards,
Yagisan

---

