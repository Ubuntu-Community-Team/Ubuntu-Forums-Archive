---
title: "Azureus not working"
date: 2005-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by potatohead on 2005-04-23
Hey, just wondering if someone has any ideas on this one. I did a quick forums search and couldn't find what I was looking for, my apologies if this has already been answered.

I installed azureus and the sun jre just like I was supposed to, now when I try to run azureus I get the following error:
david@frobox:~/azureus$ ./azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_02]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/david/azureus/Azureus2.jar:/home/david/azureus/swt.jar:/home/david/azureus/swt-mozilla.jar:/home/david/azureus/swt-pi.jar" -Djava.library.path="/home/david/azureus" -Dazureus.install.path="/home/david/azureus" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/david/azureus/libswt-pi-gtk-3106.so: /home/david/azureus/libswt-pi-gtk-3106.so: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:100)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:118)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:71)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:55)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:106)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:73)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:100)
Azureus TERMINATED.
david@frobox:~/azureus$         


this file, "/home/david/azureus/libswt-pi-gtk-3106.so: cannot open shared object file: No such file or directory" is actually there.. not really sure what the problem is here.

Any ideas?

Thanks!

---

### Post by Laurent Cazalet on 2005-04-23
could it be that this file is not readable/executable?

---

### Post by potatohead on 2005-04-25
nevermind, I'm just dumb. Installed the i586 VM instead of the amd64 one. Azureus works fine now

---

### Post by IndieRockSteve on 2005-05-03
I'm getting this error now and I installed 
jre-1_5_0_03-linux-amd64.bin

anyone have an idea?

---

