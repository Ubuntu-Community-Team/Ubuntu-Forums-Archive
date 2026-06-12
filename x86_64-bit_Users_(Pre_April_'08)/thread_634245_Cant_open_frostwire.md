---
title: "Cant open frostwire"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by collector on 2007-12-07
I cant open frostwire(nothing happens when i click it) 
 i get this message in terminal

> rnaud@arnaud-desktop:~$ sudo apt-get install sun-j2re1.5
[sudo] password for arnaud:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
Pakket sun-j2re1.5 is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket sun-j2re1.5 heeft geen installeerbare kandidaat
arnaud@arnaud-desktop:~$ echo 3 | sudo update-alternatives --config java

Er zijn 3 alternatieven die 'java' voorzien.

  Selectie    Alternatieven
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

druk enter om de standaardwaarde [*] te behouden, of  geef het selectienumber in: '/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' wordt gebruikt om in 'java' te voorzien.
arnaud@arnaud-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_13]
Configuring environment...
Loading FrostWire:

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.font.FontManager$1.run(FontManager.java:178)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(FontManager.java:173)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(SunGraphicsEnvironment.java:722)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(SunGraphicsEnvironment.java:602)
        at sun.java2d.SunGraphicsEnvironment.access$200(SunGraphicsEnvironment.java:58)
        at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:174)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:94)
        at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:164)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
        at java.lang.Class.newInstance0(Class.java:350)
        at java.lang.Class.newInstance(Class.java:303)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:93)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)

im quite new to linus so a simple solution would be nice :p
thx in advance

---

### Post by wolffkrieger on 2008-01-04
Check out this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=563819") and be sure to thank** master_kernel**. :)

---

### Post by Major_Kong on 2008-01-07
> **collector said:**
> im quite new to linus so a simple solution would be nice :p
thx in advance

It isn't a "linux" problem, but more of a Frostwire problem...

---

