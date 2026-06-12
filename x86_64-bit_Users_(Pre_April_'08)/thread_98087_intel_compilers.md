---
title: "intel compilers"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by mverissi on 2005-12-02
Hi all,

I am a new user to Ubuntu and as much as I like it so far, I have one annoying issue that I can't solve. I need badly to install the intel fortran and c++ compilers, as well as math kernel libraries on my turion laptop. Problem is, the installation packages supplied by intel are rpm-based. I have tried to convert the rpm packages to deb ones, but it complains that the architecture amd64 does not appear in the emt64 rpm package, and it also complains about the file formats of some libraries included with the packages. Rpm, although installed in my machine, cannot build a database, so I can't try to fool the installation script anyway. Does anyone know how to install the intel compilers on debian 64 / ubuntu?

Please, avoid "escapist" answers like "we have to fight non-open software", which I have seen in the Debian mailing lists. This does not help and does not change the fact that the intel compilers are the best non-commercial option nowadays, even though it's not open-source. Any real attempts to help will be greatly appreciated and I will kindly acknowledge them.

Thanks in advance,

Marcos

---

### Post by mo_x on 2005-12-02
Did you try the alien package ?

---

### Post by joemomma on 2006-11-22
Installing the Intel compilers in Ubuntu is not straightforward.  It seems to get more difficult with every release.  After a lot of searching I did finally found a way to install them, though, in the latest version (6.10) of Ubuntu.

The first step is to find the install scripts.  After untarring the package go into the /data/ subdirectory.  Edit install_cc.sh (or install_fc.sh for fortran) and change the first line from 

#!/bin/sh

to

#!/bin/bash.

Then in that same file search for the following line:

    RPM_NOT_FOUND=$?

and change it to

    RPM_NOT_FOUND=1

This should allow you to install the compilers (although you will get errors).  After installation, go to your installation directory and go to the bin subdirectory.  Open every script in that directory and if the first line says "#!/bin/sh" change it to "#!/bin/bash".

That worked for me.  Good luck

---

