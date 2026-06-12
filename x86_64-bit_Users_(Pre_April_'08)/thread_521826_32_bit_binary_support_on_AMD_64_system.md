---
title: "32 bit binary support on AMD 64 system"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by als365 on 2007-08-09
Hey all.  My roommate told me there was a way to enable 32 bit binary support on amd 64 systems.  Is this true.  He said that it would allow me to install i386 deb packages on my amd64 system running Kubuntu.  Is this possible?  If so, can someone point me in the right direction?

Thanks,

-Austin

---

### Post by John.Michael.Kane on 2007-08-09
Yes it's possible.

What package or packages are you looking to install?

For most common items you can look at this thread.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

For more advance items read here.
[getlibs: Automatically solves dependencies for binaries]("http://ubuntuforums.org/showthread.php?t=474790&highlight=cappy")

---

### Post by als365 on 2007-08-10
Trying to install some specialty robotics simulation software [http://www.playerstage.sourceforge.net](http://www.playerstage.sourceforge.net)

They have an i386 deb but no amd64.  I installed it from source, but had some problems, which i corrected, but were still a pain to deal with.  I was just wondering for future reference and for other amd64 systems I install this software on.

Thanks,

-Austin

---

### Post by Kilz on 2007-08-10
> **als365 said:**
> Trying to install some specialty robotics simulation software [http://www.playerstage.sourceforge.net](http://www.playerstage.sourceforge.net)

They have an i386 deb but no amd64.  I installed it from source, but had some problems, which i corrected, but were still a pain to deal with.  I was just wondering for future reference and for other amd64 systems I install this software on.

Thanks,

-Austin

You can install 32bit applications. Getlibs, linked above will install any required 32bit libs for you.

---

