---
title: "libDevil for 32 bit applications"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by whoop on 2008-01-22
I am trying to run an application that needs libDevil. I installed this using synaptic. When I run the application it cannot find libIL.so.1. libIL.so.1 is in /usr/lib/ but I reckon it is 64 bit as all the other libs are collected from /usr/lib32/. I cannot find a package in synaptic that lets me install libDevil 32 bit on my 64 bit system.
Is there any way I can make it working?

regards.

---

### Post by or1on on 2008-01-22
did u try cappy's getlibs yet ?

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Cappy on 2008-01-22
Install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
getlibs -p libdevil1c2
```

---

### Post by whoop on 2008-01-22
Wow, that worked! It complained about libmng as well but I could install that the same way. Now the program seems to work. Very cool.
So what if I wanted to remove those packages again? I cannot see them in Synaptec. Or at least I cannot distinguish them from 64 bit packages.

---

### Post by Cappy on 2008-01-22
It's not possible to remove the libraries at the moment using the default options (other than actually using the rm command and removing the libraries).

The newest feature of getlibs lets you remove it but you have to install the library with
```
getlibs --build -p libdevil1c2
```
and then you can remove it with
```
sudo dpkg -r lib32devil1c2
```

Still a beta feature.

---

