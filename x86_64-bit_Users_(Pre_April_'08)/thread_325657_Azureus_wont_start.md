---
title: "Azureus wont start"
date: 2006-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by vikrant_me on 2006-12-26
I followed the instruction from here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

When i try to start it fr gui...nothing happens
when i try CLI:
vicky@vicky-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.UnsatisfiedLinkError: memmove
        at org.eclipse.swt.internal.gtk.OS.memmove(Native Method)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:80)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

........nothing happens

---

### Post by kesman on 2006-12-27
Same problem here... Any clues?

---

### Post by vikrant_me on 2006-12-27
:bump: nop still looking......

---

### Post by hinzel on 2006-12-28
i had this same error, and got it fixed last night... 

first, remove azureus and all dependencies with:

sudo apt-get autoremove azureus

next, download the newest 64 bit build of azureus from sourceforge

install to /usr/bin

---

### Post by kesman on 2006-12-28
I extracted the files to my /home/user/azureus and then moved the directory to /usr/bin/azureus-bin and then created a link to azureus app with sudo ln -s /usr/bin/azureus-bin/azureus azureus .

Yet still there's a problem:

```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/usr/bin/*.jar" -Djava.library.path="/usr/bin" -Dazureus.install.path="/usr/bin" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.ui.swt.Main
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.ui.swt.Main not found in gnu.gcj.runtime.SystemClassLoader{urls=[], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Azureus TERMINATED.

```

What's the problem? And shouldn't azureus be installed somehow so that apt and dpkg recognizes it as being installed so it could be removed and apt-get install azureus wouldn't override it?

---

### Post by hinzel on 2006-12-28
did you first remove azureus and all of it's dependencies? (sudo apt-get autoremove azureus)

the tarballed file you download from sourceforge ([http://downloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux-x86_64.tar.bz2?modtime=1156163419&big_mirror=0)](http://downloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux-x86_64.tar.bz2?modtime=1156163419&big_mirror=0)), once extracted does not need to be installed. just browse to the directory and ./azureus

worked for me

---

### Post by kesman on 2006-12-29
Yes, and it's working now. I still would prefer to install software by downloading a .deb -file so that dpkg and apt would "know" that the software is installed :P

---

### Post by Frak on 2006-12-29
Why not just use the defualt Gnome-torrent?

---

### Post by kesman on 2006-12-29
never tried, but I'd still prefer azureus I guess :P It's just so well-equipped.

---

