---
title: "Jalbum"
date: 2006-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusimo on 2006-10-04
I'm new so go slow.  

[http://www.jalbum.net](http://www.jalbum.net)

I downloaded the linux version.  Works on MAC.  But Ububtu DD 64bit 6.06 no good.  I followed their instructions.  CD to directory and sh jalbuminstall.bin.  But it won't install.  Do I need a new java version or what.

admin@ivlaga:~$ cd ~/Examples
admin@ivlaga:~/Examples$ dir
flashplayer-installer  JAlbuminstall.bin  Readme.htm
flashplayer.xpt        libflashplayer.so  Readme.txt
admin@ivlaga:~/Examples$ sh JAlbuminstall.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError: ZeroGe
   at java.lang.Class.initializeClass(libgcj.so.7)
   at ZeroGd.<clinit>(DashoA8113)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.b(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.Main.main(DashoA8113)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at com.zerog.lax.LAX.launch(DashoA8113)
   at com.zerog.lax.LAX.main(DashoA8113)
Caused by: java.lang.ClassNotFoundException: com.apple.mrj.MRJOSType not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/tmp/install.dir.7737/InstallerData/,file:/tmp/install.dir.7737/InstallerData/installer.zip,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...9 more
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
admin@ivlaga:~/Examples$

Thanks,
Confusimo

---

### Post by confusimo on 2006-10-04
Never mind.  I went to Add and Remove Programs and I found 2 Java already listed.  I installed those and now it works.

Thanks,
Confusimo

---

