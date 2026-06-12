---
title: "Are source files needed after kernel built"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by ThunderRd on 2009-01-10
Question about kernel compiling:

After using 'linux-1.2.3.tar.bz2' to compile 'linux-image-1.2.3.deb', and then the .deb is installed using dpkg, do the files residing in /usr/src have to remain available to the OS for any reason? Specifically, the .deb file itself, and teh resulting '/usr/src/linux-1.2.3' directory[which is sizable], and the symlink called simply "linux"?

Or can they be archived on another drive or deleted completely?  If I rename '/usr/src/linux-1.2.3' the machine still boots; but before I backup and then delete the directory [3.5G] I'd like to have someone here confirm that this is safe practice.

---

### Post by paddy2706 on 2009-01-10
you can safely remove the deb-file and the linux-sources. if you decide to compile some modules, you will need the kernel-headers, but you can aswell download the kernel anew or copy it from your backup.

---

