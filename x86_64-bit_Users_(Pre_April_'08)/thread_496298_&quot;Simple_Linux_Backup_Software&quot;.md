---
title: "&quot;Simple Linux Backup Software&quot;"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Johnny K on 2007-07-09
I'm trying to get "Simple Linux Backup Software" ([http://simplelinuxbkup.sourceforge.net/index.html](http://simplelinuxbkup.sourceforge.net/index.html)) to work. I have it installed, but when I try to run simplebackupconfig, I get this error:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/john/.simplebackup/swt/libswt-pi-gtk-3236.so: Can't load IA 32-bit .so on a AMD 64-bit platform
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.sjrnet.simpleBackup.BackupConfigurator.main(Unknown Source)

```
Is there any way to get this app working in 64 bit?

TIA :)

---

### Post by greenfrog on 2007-07-09
Make sure you have Java 1.5 64 bit installed and it should work.

---

### Post by Johnny K on 2007-07-09
> **greenfrog said:**
> Make sure you have Java 1.5 64 bit installed and it should work.

Under synaptic, what is the name of the package I need to install? There are alot with the name Java in them. I already have sun-java5-bin and sun-java5-jre installed, so I guess I need something else?

---

### Post by Johnny K on 2007-07-09
Now I'm getting a different error:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/john/.simplebackup/swt/libswt-pi-gtk-3236.so: /home/john/.simplebackup/swt/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.sjrnet.simpleBackup.BackupConfigurator.main(Unknown Source)

```

---

### Post by Johnny K on 2007-07-09
Another update (sorry, I'm not trying to bump. Just thought that this info might help):
I installed *java-gcj-compat* via synaptic. That seems to be the package it needs. Now the error I get is:
```
Actual Java version (1.4.2) does not meet or exceed required version (1.5)
```
Where can I get a deb of version 1.5?

TIA :)

---

### Post by Mr_bleu on 2007-07-09
"Make sure you have Java 1.5 64 bit installed and it should work."
I think you need this version installed.
"sun-java5-jre
Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)" It shows as java 1.5.0.1ubuntu2 in synaptic under properties.  I could be wrong, it's happened before.

---

### Post by Johnny K on 2007-07-09
> **Mr_bleu said:**
> "Make sure you have Java 1.5 64 bit installed and it should work."
I think you need this version installed.
"sun-java5-jre
Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)" It shows as java 1.5.0.1ubuntu2 in synaptic under properties.  I could be wrong, it's happened before.

I already have sun-java5-jre installed. I get this error message:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/john/.simplebackup/swt/libswt-pi-gtk-3236.so: /home/john/.simplebackup/swt/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32
```

But if I also install *java-gcj-compat*, I only get this message:
```
Actual Java version (1.4.2) does not meet or exceed required version (1.5)
```

It seems like I have all the packages I need (and some I don't) to get this working. I can't understand why it's not.

---

### Post by tarm on 2007-07-15
I'm having the exact same problems. Anyone find anything for this?

---

### Post by Kemotaha on 2007-07-15
The problems looks to be 64-bit specifc.  I have seem the wrong ELF class problem before when trying to use a java program that didn't have 64 bit libraries compiled with it.  It might work if you have all the 32 bit libraries installed.  But then again it might not.

The error with java-gcj=compat is that the gcj compiler and runtime environment is built to duplicate the Java 1.4 environment, not the java 1.5 environment.  It seems like the program has a check that won't let you run on the 1.4 environment.  

Hope that gives you some help.

---

### Post by kuja on 2007-07-16
Have you run "sudo  update-alternatives --config java"? If not, I recommend you do so.

---

### Post by steveingbg on 2007-07-20
The problem is in the Eclipse SWT libraries that are used by Simple Linux Backup; they are 32 bit. Simple Linux Backup 0.3.3, released yesterday, includes a 64-bit test version (see my post [Simple Linux Backup 0.3.3 Released]("http://ubuntuforums.org/showthread.php?p=3051337#post3051337")). Give that a try and let us know if it works.

BTW, I'm the developer of Simple Linux Backup.

---

### Post by ctothej on 2007-07-22
> **kuja said:**
> Have you run "sudo  update-alternatives --config java"? If not, I recommend you do so.

This worked for me. Thanks.
Anyone having issues with Java not linking correctly should give this a shot. In my case, since I have a 64 bit machine with AMD64 version of Feisty installed, I use 32 bit libraries to make some apps work. I believe in this process the default java was re-linked.

---

### Post by mucnix on 2007-07-29
Also worked for me...

---

