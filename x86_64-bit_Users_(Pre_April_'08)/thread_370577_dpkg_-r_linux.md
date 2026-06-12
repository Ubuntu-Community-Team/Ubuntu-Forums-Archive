---
title: "dpkg -r linux?"
date: 2007-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by dfreer on 2007-02-25
lol...

I just compiled a package using checkinstall. A lot of the package descriptions were missing, and since I was in a hurry I didn't bother to check them/fill them all in. Here's the result :D

```
Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/dfreer/source/openal/linux/linux_9.9.9-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r linux

**********************************************************************

```

Oh noes....

---

### Post by louis_nichols on 2007-02-26
That's really funny! It's not a problem, though. You just have a package called linux... You can uninstall it, then remake the package using checkinstall and another package name.

---

### Post by dfreer on 2007-03-01
Oh good. I was afraid that if I run dpkg -r linux on my system I would create some sort of temporal rift on my hard drive, or worse... windows would reinstall lol.

---

