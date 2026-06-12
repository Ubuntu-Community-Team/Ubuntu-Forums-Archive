---
title: "[SOLVED] Azureus / java help plz!"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by Novus on 2008-05-15
up till now I thought my upgrade to 64bit went soo smooth but ofc the last thing I install will not work. azureus, I installed it from Add/remove and thought it would just work as it should.. but nooooo, clicking the louncher does nothing.. so I tried from terminal and get

```
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Thu May 15 18:25:38 CEST 2008::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::68:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to 'null'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::104,Main::<init>::84,Main::main::216
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:177)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:128)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:89)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:104)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
```

so I checked and find out that my SWT version is 3.2, which seams to be the latest in the repos (why on earth does ubuntu have a program in the repos which need newer things then they have in the repos??) so I go to eclipse.org/swt and after some tumbling  around I find a download for x64.. download it, but what on earth do I do with the files now? am I even on the right track?

---

### Post by philinux on 2008-05-15
Azureus kept crashing on me and was a devil to set up.

I'm now using deluge, with random ports, and it works perfectly.

---

### Post by ludovicc on 2008-05-17
Azureus works well for me on Ubuntu 8.04, Amd 64.

Try to do the following:

sudo apt-get install sun-java6-bin sun-java6-jre
sudo update-java-alternatives -s java-6-sun

# Full reinstallation of azureus if it still doesn't work
sudo apt-get -purge azureus
sudo apt-get azureus

Hope this helps,
Ludovic

---

### Post by JoseReyes on 2008-05-17
> **ludovicc said:**
> Azureus works well for me on Ubuntu 8.04, Amd 64.

Try to do the following:

sudo apt-get install sun-java6-bin sun-java6-jre
sudo update-java-alternatives -s java-6-sun

# Full reinstallation of azureus if it still doesn't work
sudo apt-get -purge azureus
sudo apt-get azureus

Hope this helps,
Ludovic

I am using Azureus version 3.0.5.2 in Ubuntu 8.04 64 bit and it works fine.. I downloaded it from this location.. use the AMD64 version...

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

---

### Post by Novus on 2008-06-08
Im so proud of myself I just have to post, it's working! :)

I went with deluge for a while, but never really got to like it, I missed the way azureus lets me configure it.. so I thought I'd kill some time and bang my head against the wall a few times so I started to try to get azureus working and after some messing around it worked! I had downloaded the tarball from sourceforge and put it in /tmp/azureus/ and changed the permissions and it just worked. so I put it in ~/.azureuz/ and there i didn't even have to change the permissions and I could get into a half working GUI (lots of buttons and menus wouldn't work) but as azureus is so great :D it prompted me to upgrade to SWT 3.4.something + VUZE, so and the upgrade button worked, so I upgrade SWT and hit cancel to not get VUZE and now Im all happy and have a good working bittorrent client
:popcorn:

---

