---
title: "link with 32-bit libraries on 64-bit Ubuntu"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by Shawn Yarbrough on 2008-09-29
I'm running 64-bit Ubuntu 8.04 on x86 64-bit hardware.  (Intel Core 2 Quad Q9450.)  The rest of our C++ development network is running on older 32-bit hardware and/or operating systems.  So on 64-bit Ubuntu I need gcc to generate 32-bit code some of the time.  This is working already thru the -m32 flag for gcc and ld, which works because I've installed the gcc multilib package.

However, common dependencies that aren't part of gcc, like libxml2, are failing to link when I build.  I see these errors:

```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libxml2.so when searching for -lxml2
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libxml2.a when searching for -lxml2
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libxml2.so when searching for -lxml2
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libxml2.a when searching for -lxml2
/usr/bin/ld: skipping incompatible /usr/lib/libxml2.so when searching for -lxml2
/usr/bin/ld: skipping incompatible /usr/lib/libxml2.a when searching for -lxml2
/usr/bin/ld: cannot find -lxml2

```

The libxml2 package is installed but as the 64-bit version, which can't link with gcc's -m32 option.  I know Ubuntu also has a 32-bit version of this package and I know that the 32-bit version of the library should link and run correctly under 64-bit Ubuntu...

...but what is the correct way to install 32-bit libxml2 and get it to automatically link with our code when gcc is invoked with the -m32 option?

---

### Post by Shawn Yarbrough on 2008-09-30
I tried this:

```
$ sudo dpkg -i libxml2-dev_2.6.31.dfsg-2ubuntu1.2_i386.deb 
dpkg: error processing libxml2-dev_2.6.31.dfsg-2ubuntu1.2_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 libxml2-dev_2.6.31.dfsg-2ubuntu1.2_i386.deb
```

---

### Post by Yellow Pasque on 2008-09-30
Install getlibs [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
Get library like so:
```
sudo getlibs -p libxml2 libxml2-dev
```

---

### Post by duffrecords on 2008-11-10
And get the 32-bit version of the libs too:```
sudo apt-get install ia32-libs
```I'm dealing with a [similar issue]("http://ubuntuforums.org/showthread.php?t=977064") at the moment.

---

### Post by duffrecords on 2008-11-10
Sorry, I hadn't noticed Temüjin's post--I'll have to try that!

---

