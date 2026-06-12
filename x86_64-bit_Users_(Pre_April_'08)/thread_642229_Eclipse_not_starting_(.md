---
title: "Eclipse not starting :("
date: 2007-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2007-12-16
Eclipe doesn't start, and it gives a error which is as follows :
> JVM terminated. Exit code=1
/usr/lib/kaffe/pthreads/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 560031
-install /usr/lib/eclipse
-vm /usr/lib/kaffe/pthreads/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

Anyone? what can the issue be?

---

### Post by azbarcea on 2007-12-18
The issue is that u don't use sun's java version:
Follow this thread with modifications accordingly!

[http://ubuntuforums.org/showthread.php?p=3401095](http://ubuntuforums.org/showthread.php?p=3401095)

---

