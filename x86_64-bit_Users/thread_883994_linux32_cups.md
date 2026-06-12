---
title: "linux32 cups"
date: 2008-08-08
forum: x86 64-bit Users
---

### Post by oneporter on 2008-08-08
I have a printer (Cannon ip1800) that is not supported under the AMD64, and as far as I can tell, no one has been able to get it going.  I've messed with it a good bit and have stopped at an idea that may or may not work.  

Is it possible to replace my current cups that is 64-bit with a 32-bit cups, if so, would that allow me to install the 32-bit package?  How would I go about doing this?  Ideas?

---

### Post by Thelasko on 2008-08-08
I'm assuming you have exhausted all of the options in the repositories.  Have you tried installing the [Cannon driver]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20iP1800%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&") RPM using alien, or compiling it from source?

---

### Post by Thelasko on 2008-08-08
Ok, I took a closer look at those files on the cannon website.  They're all RPM packages.  The binaries are all i386, but they provide the source code (in RPM format, which is odd).  

How I think you need to do this (I've used alien, but not for a source package) is use alien to convert the source RPM into a deb file.  [Here are the instructions.]("https://help.ubuntu.com/community/RPM/AlienHowto")

Then, you need to compile the source file using:
> dpkg-buildpackage
With the name of the package at the end.  I've never done this before, I just read about it [here.]("http://linux.die.net/man/8/apt-get")  At this point you probably know as much as I do about this process.

Check around, maybe somebody already went through this mess and created a working .deb binary file you can use.  This problem doesn't look insurmountable assuming the source files build ok.  It might even turn out being fairly easy (cross your fingers) since the RPM file will tell Ubuntu all of the dependencies it needs to install.

---

