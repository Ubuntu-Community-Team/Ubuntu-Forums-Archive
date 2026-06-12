---
title: "Java stopped working..."
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by notna01 on 2007-09-21
```
anton@anton-desktop:~$ cd Desktop/scapeservers/altoone
anton@anton-desktop:~/Desktop/scapeservers/altoone$ ./compile
Note: stream.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
compiled....
Running...
Exception in thread "main" java.lang.UnsupportedClassVersionError: server (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
anton@anton-desktop:~/Desktop/scapeservers/altoone$ 
```
I am now getting that error ever since I downloaded updates....
Any help?

---

### Post by Kilz on 2007-09-21
What version of Ubuntu are you running?

---

### Post by tszanon on 2007-09-21
And what version of Java?

---

