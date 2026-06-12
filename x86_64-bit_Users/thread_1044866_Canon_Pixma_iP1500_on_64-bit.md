---
title: "Canon Pixma iP1500 on 64-bit"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by Izkata on 2009-01-19
I tried following the instructions here:  [http://ubuntuforums.org/showpost.php?p=4767724&postcount=10](http://ubuntuforums.org/showpost.php?p=4767724&postcount=10)  --but it fails at the bjfilterpixmaip1500 step.  Copying/symlinking the files over as suggested don't work either, for a couple reasons:

libpng.so.2 is required, while libpng12.so.0 is installed
libtiff.so.3 is required, while libtiff.so.4 is installed
According to [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500) , these can be symlinked to the correct name - but it doesn't work:

> 
izkata@Izein:/usr/lib$ bjfilterpixmaip1500 
bjfilterpixmaip1500: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
izkata@Izein:/usr/lib$ sudo ln -s libtiff.so.4 /usr/lib32/libtiff.so.3
izkata@Izein:/usr/lib$ bjfilterpixmaip1500 
bjfilterpixmaip1500: error while loading shared libraries: libtiff.so.3: wrong ELF class: ELFCLASS64


Can anyone help with this?  I'm on Ubuntu Hardy 64-bit.

---

