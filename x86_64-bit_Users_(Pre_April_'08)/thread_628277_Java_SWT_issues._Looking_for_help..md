---
title: "Java SWT issues. Looking for help."
date: 2007-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by trmentry on 2007-12-01
I'm trying to get **[Crashplan](http://www.crashplan.com)** running on Gutsy.   I extracted the archive and can get the engine running.

When I try and run the dekstop gui I get the following:

```

~/bin/crashplan$ ./CrashPlanDesktop.sh
chris@kashyyyk:~/bin/crashplan$ Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-gtk-3346 or swt-gtk in swt.library.path, java.library.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
        at com.backup42.desktop.CrashPlanDesktop.<init>(CrashPlanDesktop.java:117)
        at com.backup42.desktop.CrashPlanDesktop.main(CrashPlanDesktop.java:81)

```

So I figured out it was looking for the  libswt3.2-gtk-java   package.  I installed it and still got that error above.   I cheated and put a symlink in crashplan/lib point to it in /usr/lib/java

But now I get the following:

```

~/bin/crashplan$ Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3236 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at com.backup42.desktop.CrashPlanDesktop.<init>(CrashPlanDesktop.java:117)
        at com.backup42.desktop.CrashPlanDesktop.main(CrashPlanDesktop.java:81)

```

The shared objects for swt appear to be in /usr/lib/jni.  However if I make sym links to libswt-pi-gtk-3236.so in crashplan/lib or /usr/lib/java or where ever I still get the above error.   I'm a bit stuck.  

I've read about doing a 
```

java -Djava.library.path=<blah>  
```but not exaclty sure where to point that at.  I don't want to break java.. and haven't been able to display java's env settings that it currently has in case I want to revert my changes.

Any pointers?


On a side note, Crashplan support says that the next version of the linux client will have an 'installer' that will fix these types of issues on Ubuntu.   However I'm wanting to try it out now. :D

Any advise would be welcome.

thanks

---

### Post by Kilz on 2007-12-01
What java are you running, is it 32bit? If so it is looking for 32bit versions of that file. The solution is to[ get the 32bit version of that file]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fe%2Feclipse%2Flibswt3.2-gtk-java_3.2.2-3ubuntu3_i386.deb&md5sum=8d1d6ee7c0c7ba7f7212c7dfb75e8f08&arch=i386&type=main") then extract it. Do not force install the package, this will overwrite the 64bit files that other things may need.

```
sudo dpkg -x /path/to/the/file.deb
```

This will extract the internal tree of the deb file. Next look in that tree for /usr/lib and copy the files in it to /usr/lib32 in your system.

---

### Post by trmentry on 2007-12-01
I would think I'm running 64 bit... I just apt-get install java-common, etc and let it do the rest. 

```

~# java -version
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)

```

```

~# dpkg -l | grep java
ii  java-common                                0.26ubuntu1                               Base of all Java packages
ii  libcairo-java                              1.0.8-6ubuntu1                            Cairo bindings for Java
ii  libcommons-cli-java                        1.0-8                                     API for working with the command line argume
ii  libglib-java                               0.4.2-7ubuntu1                            GLib bindings for Java
ii  libgnome-java                              2.12.7-3ubuntu1                           Gnome bindings for Java
ii  libgtk-java                                2.10.2-4ubuntu1                           GTK+ bindings for Java
ii  libhsqldb-java                             1.8.0.8-1ubuntu1                          Java SQL database engine
ii  libjaxp1.3-java                            1.3.03-5                                  Java XML parser and transformer APIs (DOM, S
ii  libjline-java                              0.9.5-3ubuntu2                            Java library for handling console input
ii  liblog4j1.2-java                           1.2.13-4                                  Logging library for java
ii  libseda-java                               3.0-3                                     the Staged Event-Driven Architecture library
ii  libservlet2.4-java                         5.0.30-6ubuntu1                           Servlet 2.4 and JSP 2.0 Java library.
ii  libswt3.2-gtk-java                         3.2.2-3ubuntu3                            Fast and rich GUI toolkit for Java, gtk2 ver
ii  libxalan2-java                             2.7.0-4                                   XSL Transformations (XSLT) processor in Java
ii  libxerces2-java                            2.8.1-2                                   Validating XML parser for Java with DOM leve
ii  openoffice.org-java-common                 1:2.3.0-1ubuntu5                          OpenOffice.org office suite Java support arc
ii  sun-java5-bin                              1.5.0-13-0ubuntu1                         Sun Java(TM) Runtime Environment (JRE) 5.0 (
ii  sun-java5-jre                              1.5.0-13-0ubuntu1                         Sun Java(TM) Runtime Environment (JRE) 5.0 (

```

I tried what you said and still no joy.
```

/usr/lib/eclipse/plugins# ls -l
total 1660
-rw-r--r-- 1 root root 1693038 2007-09-14 01:25 org.eclipse.swt.gtk.linux.x86_64_3.2.2.v3236.jar

 ls -l /usr/lib32/eclipse/plugins/
total 1616
-rw-r--r-- 1 root root 1649612 2007-12-01 04:47 org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar

```

The sym links are all there as well in /usr/lib(32)/java

```

$ Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3236 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at com.backup42.desktop.CrashPlanDesktop.<init>(CrashPlanDesktop.java:117)
        at com.backup42.desktop.CrashPlanDesktop.main(CrashPlanDesktop.java:81)

```

---

### Post by trmentry on 2007-12-01
One thing I have noticed... is I have 

/usr/lib  has a lib64 symlink pointing to it as well
/usr/lib32

PLus  

/lib    with a /lib64 pointing here too.
/lib32


The lib dirs off / don't have java stuff in them... should there be some symlinks in there as well?

---

### Post by pboulet on 2008-02-19
I have a similar problem trying to run [xmind]("http://www.xmind.org/"). This eclipse based application is available only as a 32-bit java application. Using the 32-bit sun jre v1.6.0, I am able to get to the splash screen of the application before it fails. In the log file, there is the line
```
Root exception:
java.lang.UnsatisfiedLinkError: no swt-gtk-3346 or swt-gtk in swt.library.path, java.library.path or the jar file

```

I have installed the 32-bit libswt3.2-gtk-java and libswt3.2-gtk-jni packages with the method explained by Kilz (download, extract and manual copy to /usr/lib32). This does not help :(

How can I tell the jvm to find these files? I have tried to copy the .jar and .so files in /usr/lib/jvm/ia32-java-6-sun/jre/lib and /usr/lib/jvm/ia32-java-6-sun/jre/lib/i386 with no visible change. If I copy them to the current directory it does not help either.

Thanks for any help,

---

### Post by jespdj on 2008-02-19
> **pboulet said:**
> I have a similar problem trying to run [xmind]("http://www.xmind.org/"). This eclipse based application is available only as a 32-bit java application. Using the 32-bit sun jre v1.6.0 ...
There are no 32-bit and 64-bit Java applications. So the application you are trying to run is not a "32-bit Java application" - because that doesn't exist. A Java program will run on a 32-bit or 64-bit Java runtime environment without any changes.

SWT, which is the GUI toolkit of Eclipse, includes a few native libraries. You need the 64-bit version of those native libraries if you're using a 64-bit operating system.

---

### Post by pboulet on 2008-02-20
Ok, a java application is world length independent (except for native libraries) but then why is it not even showing the splash screen with the 64-bit jvm is a mystery. The launcher is perhaps limited to 32 bit linuxes.

Concerning the 32-bit swt native files, I have found them and installed them but the application does not find them. Furthermore the application launcher does not seem to accept any command line options, so I am a bit stuck. I would not like to revert to 32 bit ubuntu but I use xmind daily :(

---

### Post by zaphod_42b on 2008-06-10
Hi!
I had a similar problem (with mvPod). I'm using Ubuntu (AMD64).

I copied the swt.jar from  to the lib-directory that came with the program files (mvPod):
```
cp /usr/lib64/java/swt.jar /path/to/mvpod/lib/
```
A link should work, too.

I got rid of the 
[FONT="Courier New"]"no swt-gtk-3349 or swt-gtk in swt.library.path, java.library.path or the jar file"[/FONT]
but got instead the 
"[FONT="Courier New"]no swt-pi-gtk-3236 in java.library.path[/FONT]"
error.

I typed the following before trying to start the program (my libswt-pi-gtk-3236.so is located in /usr/lib/jni)
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jni
```
and everything works fine!

Hope this helps...

---

