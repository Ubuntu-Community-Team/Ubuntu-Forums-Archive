---
title: "Floola under 64 Karmic?"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by blueridgedog on 2009-11-08
I took the plunge and installed the 64 bit Karmic...

How do I get floola to work?  It wants 
```

~/Desktop$ ./Floola 
./Floola: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

However, I can't install that:

```
# apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5
```

Is it possible to get 5 with karmic 64?

This thread suggests getting the deb from Jaunty:

[http://ubuntuforums.org/showthread.php?p=8258553](http://ubuntuforums.org/showthread.php?p=8258553)

---

### Post by blueridgedog on 2009-11-08
OK, bit of work here:

Download the 32 bit deb package for jaunty with libstdc++5

[http://packages.ubuntu.com/jaunty/libs/libstdc++5](http://packages.ubuntu.com/jaunty/libs/libstdc++5)

Then extract the files you need:

dpkg-deb -x ./libstdc++5_3.3.6-17ubuntu1_i386.deb ./

Then copy the link and the library to /usr/lib32

Floola now works!

---

### Post by nixed242 on 2009-11-12
It works! Thanks for the suggestion. I had the files in /usr/lib instead of /usr/lib32.

---

