---
title: "libjack-dev"
date: 2006-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dudeguythingman424 on 2006-10-16
I need this file to build wine from the source, I don't really know much abou this stuff and need a bit of help.
the error message i get is 
sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for wine cannot be satisfied because the package libjack-dev cannot be found

Thanks for the help

---

### Post by RAOF on 2006-10-16
You **really** don't want to bother building Wine from source.  The Ubuntu deb-src builds a 64bit version (which then won't run any actual programs, 'cause there aren't any Win64 programs :p), and the winehq.org deb-src requires a bunch of 32bit libraries that aren't packaged for AMD64 in Ubuntu.

It's possible, but a **huge** amount more effort than just using --force-architecture to install the 32bit binary deb.

---

