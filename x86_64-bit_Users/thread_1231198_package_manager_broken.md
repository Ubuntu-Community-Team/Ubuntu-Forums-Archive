---
title: "package manager broken"
date: 2009-08-04
forum: x86 64-bit Users
---

### Post by xeno_phile on 2009-08-04
hello one and all,
 I've encountered a problem that i hope someone can help me solve.
 When i run Package Manager i get the following error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

I am running Kernel 2.6.28-14-generic.

Any suggestions?

---

### Post by wojox on 2009-08-04
It can't find the server for what ever reason. You could try opening System > Admin > Software Sources and the first tab Ubuntu Software will give you the ability to download from a different location.

---

### Post by xeno_phile on 2009-08-04
> **wojox said:**
> It can't find the server for what ever reason. You could try opening System > Admin > Software Sources and the first tab Ubuntu Software will give you the ability to download from a different location.
Changed Ubuntu Software Source from UK Server to Main Server.
Problem solved.
Thanks wojox.

---

### Post by xeno_phile on 2009-08-05
A quick update to tidy up loose ends.

Not wanting to add to the burden placed upon the Main Server, i retried the local UK Mirror again. Connection was successful. 
Must assume it was either a temporary glitch at my end or a brief problem with the Mirror.
Anyway, good to know of temporary work-arounds when problems do arise.

xeno_phile.

---

