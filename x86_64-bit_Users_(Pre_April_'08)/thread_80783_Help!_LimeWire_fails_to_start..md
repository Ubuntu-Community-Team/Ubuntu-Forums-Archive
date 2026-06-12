---
title: "Help! LimeWire fails to start."
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brian McConnell on 2005-10-23
LimeWire won't start for me!!

Here's the terminal output:
```
brian@ubuntu:~$ /usr/bin/runLime.sh
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading LimeWire:
java.lang.ExceptionInInitializerError
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)
Caused by: java.lang.NullPointerException
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:2171)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:2006)
        at java.lang.Runtime.loadLibrary0(Runtime.java:824)
        at java.lang.System.loadLibrary(System.java:908)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:76)
        at java.security.AccessController.doPrivileged1(Native Method)
        at java.security.AccessController.doPrivileged(AccessController.java:287)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1488)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1511)
        ... 2 more

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxppc32142-20050609 (JIT enabled: jitc))

brian@ubuntu:~$
```

here's the terminal output for checking my java version:
```
brian@ubuntu:~$ java -version
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxppc32142-20050609 (JIT enabled: jitc))
brian@ubuntu:~$
```

Any suggestions? Installation of both java and Limwire seemed to have gone fine without a hitch. So, I'm a bit stumped. Any help would be greatly appreciated.
Thanks,
Brian

---

### Post by Entity on 2005-10-27
I'm sorry can't help for your limewire problem, but you can consider using gtk-gnutella instead wich is really nice also.

---

### Post by step han on 2005-11-11
I have exactly the same problem, except that I am using Gentoo Linux on ppc (old blue imac 450 MHz)

So it is not an error specific to ubuntu...

---

### Post by Jason-X on 2005-11-11
Me too. I get the same error. I use GTK-Gnutella which works really well.

---

### Post by cstudent on 2005-11-11
You need to install the Sun version of Java. You can use Arnieboy's script called Automatix to install it. It will simplify the process for you. Uninstall the Java version you have now first.

You can find Automatix here:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Bill

---

### Post by Brian McConnell on 2005-11-12
[QUOTE=cstudent]You need to install the Sun version of Java. You can use Arnieboy's script called Automatix to install it. It will simplify the process for you. Uninstall the Java version you have now first.

You can find Automatix here:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Bill[/QUOTE]
I thought that was x86 only and not for ppc. Am I mistaken?

---

### Post by cstudent on 2005-11-14
[QUOTE=Brian McConnell]I thought that was x86 only and not for ppc. Am I mistaken?[/QUOTE]

No. That's correct. I didn't see anything in your post that clued me in to you being ppc or I'm overlooking it. Sorry. My bad. :) 

Bill

---

### Post by dloudy on 2007-07-15
I took the advice of using GTK-Gnutella, but it will not start for me when I try to open it up.  Any ideas why?  I went into the permissions and gave myself (owner) the execute permission, but still it did not work?

Thanks!!

---

### Post by Mr_bleu on 2007-07-15
This thread's almost 2 yrs old.

---

### Post by cbiere on 2007-07-15
You should try to run gtk-gnutella from a terminal to see why it doesn't start. Most-likely it's just too old. Feisty Fawn has a newer version of gtk-gnutella.

---

### Post by Kilz on 2007-07-15
For those having a problem getting Frostwire to start. [Take a look at this post.]("http://ubuntuforums.org/showpost.php?p=2886970&postcount=12") In fact [that whole thread]("http://ubuntuforums.org/showthread.php?t=477363") is a good source of help.

---

