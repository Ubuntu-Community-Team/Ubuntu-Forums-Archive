---
title: "Frostwire does not work in 64 bit Ubuntu 9.04"
date: 2009-05-30
forum: x86 64-bit Users
---

### Post by tuxusa on 2009-05-30
I cannot get Frostwire to work on 64 bit Ubuntu 9.04. It works great on my other pc which is 32 bit Ubuntu 9.04. What is needed to get Frostwire to work on 64 bit Ubuntu 9.04? 

Thanks in advance
Rick

Java installed:
Sun-java6-bin
ia32-sun-javaq6-jre
sun-java6-fre
java-common
Sun-java6-fonts

pc is: 
AMD Quad core 3.0GHZ.
4 gigabyte of memory
500GB hard drive


FrostWire version 4.17
Java version 1.6.0_13 from Sun Microsystems Inc.
Linux v. 2.6.28-11-generic on i386
Free/total memory: 60332248/61079552

java.lang.NoClassDefFoundError: org/limewire/util/VersionUtils
	at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.limewire.util.VersionUtils
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	... 6 more

STARTUP ERROR!

---

### Post by Yellow Pasque on 2009-05-31
You could always use gtk-gnutella: [https://launchpad.net/~medigeek/+archive/ppa](https://launchpad.net/~medigeek/+archive/ppa)

---

### Post by Fluffy13 on 2009-05-31
Frostwire works out of the box for Jaunty 64Bit. I have it installed on a few systems (AMD/Intel) running this OS.

Make sure you are using the newest version from their website.

---

### Post by CoreyB. on 2009-05-31
Run 'sudo update-alternatives --config java' in Terminal and choose java-6-sun.  You could also try the version from GetDeb, which works flawlessly for me: [Frostwire 4.18.0 64-bit from getdeb]("http://www.getdeb.net/download/4369/0").

---

### Post by tuxusa on 2009-05-31
Frostwire 4.18.0 64-bit from getdeb is working flawlessly. Thanks everyone!

---

### Post by Fluffy13 on 2009-05-31
No problem :)

---

### Post by lookitseman on 2009-06-12
I had the the same results.  Using the package from getdeb with java-6-sun works.  I wonder what the different is?  The package from the main frostwire site is 7.7MB.  From Getdeb it's 35.5MB.

---

### Post by ruffneck on 2009-10-08
Thanks guys, works a treat!

---

### Post by whistlerspa on 2009-10-15
4.18.3 doesn't work on my 8.04 64bit box however - i had to revert to 4.17.

---

