---
title: "ImageJ"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by Rchen on 2008-05-02
Hello guys
I am trying to install ImageJ on a compaq nx6325 machine, but after inserting the run command I keep getting this:

Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/chen/Applications/ImageJ/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
        at java.lang.Runtime.load0(Runtime.java:770)
        at java.lang.System.load(System.java:1005)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:552)

locate libXext.so.6
gives:

/usr/lib/libXext.so.6
/usr/lib/libXext.so.6.0
/usr/lib/libXext.so.6.4.0

any ideas? :(

---

### Post by leafw on 2008-08-14
You may try Fiji: "Fiji Is Just ImageJ (batteries included)" which aims at making complete ImageJ installations trivial.

There are packages from debian and ubuntu. See the downloads page:

[http://pacific.mpi-cbg.de/wiki/index.php/Downloads](http://pacific.mpi-cbg.de/wiki/index.php/Downloads)

---

