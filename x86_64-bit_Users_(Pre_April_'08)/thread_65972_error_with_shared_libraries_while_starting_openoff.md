---
title: "error with shared libraries while starting openoffice.org2"
date: 2005-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by ovitrat on 2005-09-15
Hello,

I've installed openoffice.org2 from ubuntu repository on my Debian machine (i'm using Debian AMD64 version on Compaq Presario v2310)

I have the following error message when I try to start Writer:

ovit@HOBBES:~$ oowriter2
/usr/lib/openoffice2/program/javaldx: error while loading shared
libraries: libpam.so.0: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin: error while loading shared
libraries: libjpeg.so.62: cannot open shared object file: No such file or directory 

but the files libpam.so.0 and libjpeg.so.62 are here.
I've done the installation with ia32-libs, not chroot.
any ideas why the program does not start ?

thanks,
Olivier

---

### Post by DancingSun on 2005-09-15
Which Ubuntu repository did you install it from?  I am not aware of any AMD64 build of OOo2 for Ubuntu..

---

### Post by ovitrat on 2005-09-15
hello,
I've this line in my sources.list:

# Ubuntu repository for openoffice.org2
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

AMD64 packages are there

HOBBES:~# apt-cache policy openoffice.org2
openoffice.org2:
  Installed: 1.9.125+2.0beta2-1ubuntu1-1
  Candidate: 1.9.125+2.0beta2-1ubuntu1-1
  Version Table:
 *** 1.9.125+2.0beta2-1ubuntu1-1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
        100 /var/lib/dpkg/status

thanks,
Olivier

---

### Post by DancingSun on 2005-09-15
Breezy's OOo2 are compiled using 32-bit libraries, I'm not sure what the details are beyond ia32-lib, but you'll need to grab all the depenencies.

---

### Post by ovitrat on 2005-09-16
[QUOTE=DancingSun]Breezy's OOo2 are compiled using 32-bit libraries, I'm not sure what the details are beyond ia32-lib, but you'll need to grab all the depenencies.[/QUOTE]
 hello,

yes, I've installed ia32-libs, and all dependencies

---

### Post by DancingSun on 2005-09-16
I found this in the forums, looks that it should help with your case:
[http://ubuntuforums.org/showpost.php?p=293466&postcount=261](http://ubuntuforums.org/showpost.php?p=293466&postcount=261)

---

