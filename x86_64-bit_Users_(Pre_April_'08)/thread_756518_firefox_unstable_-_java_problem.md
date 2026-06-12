---
title: "firefox unstable - java problem??"
date: 2008-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tjk on 2008-04-15
I have posted this problem here because I use Gutsy 64-bit - so the solutions may be different.

Firefox is very unstable and crashes regularly.  It appears that it is site specific.  I ran --safe-mode in a terminal and still have the same problem (although I didn't toggle all the selectable features off while starting).  Here is the terminal readout:
```
Java process: caught exception from sun.plugin.navig.motif.Plugin.start
Exception in thread "main" java.lang.OutOfMemoryError
        at java.util.zip.ZipFile.open(Native Method)
        at java.util.zip.ZipFile.<init>(ZipFile.java:112)
        at java.util.jar.JarFile.<init>(JarFile.java:127)
        at java.util.jar.JarFile.<init>(JarFile.java:65)
        at sun.misc.URLClassPath$JarLoader.getJarFile(URLClassPath.java:578)
        at sun.misc.URLClassPath$JarLoader.<init>(URLClassPath.java:545)
        at sun.misc.URLClassPath$3.run(URLClassPath.java:323)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.misc.URLClassPath.getLoader(URLClassPath.java:312)
        at sun.misc.URLClassPath.getLoader(URLClassPath.java:289)
        at sun.misc.URLClassPath.getResource(URLClassPath.java:159)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:191)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:282)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.util.ResourceBundle.loadBundle(ResourceBundle.java:1058)
        at java.util.ResourceBundle.findBundle(ResourceBundle.java:928)
        at java.util.ResourceBundle.getBundleImpl(ResourceBundle.java:765)
        at java.util.ResourceBundle.getBundle(ResourceBundle.java:552)
        at java.awt.Toolkit$3.run(Toolkit.java:1448)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1444)
        at java.awt.Color.<clinit>(Color.java:250)
        at sun.plugin.navig.motif.Plugin.start(Plugin.java:71)
INTERNAL ERROR on Browser End: Could not read ack from child process
System error?:: Resource temporarily unavailable

```Oh yes, I also upgraded to version 3 under a different user and the problem was still there.

---

### Post by felker2 on 2008-04-16
Which site/URL is causing the crash?

How much memory have you got?

Which java-plugin are you using (check via about:plugins in Firefox)

---

