---
title: "Install ORacle 10r1 fails!"
date: 2006-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by cable2000 on 2006-06-30
Hi,

I'm trying to install Oracle 10gr1 on my SUN Fire X4100 (AMD64) Server under Ubuntu 6.06

When i run the installer, the following happens:

Preparing to launch Oracle Universal Installer from /tmp/OraInstall2006-06-30_03-36-58PM. Please wait ...oracle@Airforce1:~/10gr1/Disk1$ Exception in thread "main" java.lang.UnsatisfiedLinkError: /tmp/OraInstall2006-06-30_03-36-58PM/jre/1.4.2/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1560)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1477)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:506)

And that was it. I checked ldconfig and the missing lshared object is present in //usr/lib, usr/X11R6/lib and /usr/X11R6/lib64

Is there someone who has oracle installed on 6.06? 

Any help will be great!

With kind regards
Robert Hassing

---

### Post by guido_sohne on 2006-07-04
I tried with Oracle 10gR1 and 10gR2 both. 

I made it to the point where I supplied needed 32 bit libraries from a 32 bit install I had around and the Java installer worked.

There's a problem with the Java installer. It bombs on trying to check/set permissions for the oraInventory directory, so you will wind up not being able to get past page two of the installer. At least, that's the experience I had. 

I'm now running 10gR1 on a Sparc Solaris box ...

-- G.

[QUOTE=cable2000]Hi,

I'm trying to install Oracle 10gr1 on my SUN Fire X4100 (AMD64) Server under Ubuntu 6.06

When i run the installer, the following happens:

Preparing to launch Oracle Universal Installer from /tmp/OraInstall2006-06-30_03-36-58PM. Please wait ...oracle@Airforce1:~/10gr1/Disk1$ Exception in thread "main" java.lang.UnsatisfiedLinkError: /tmp/OraInstall2006-06-30_03-36-58PM/jre/1.4.2/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1560)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1477)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:506)

And that was it. I checked ldconfig and the missing lshared object is present in //usr/lib, usr/X11R6/lib and /usr/X11R6/lib64

Is there someone who has oracle installed on 6.06? 

Any help will be great!

With kind regards
Robert Hassing[/QUOTE]

---

### Post by cable2000 on 2006-07-04
Well i've got it up and running

So i've got Oracle 10.2.0.1 64-bit edition running under ubuntu Dapper AMD64

this one wasn't easy, but it finally worked.

uf anyone else is trying to run oracle in the same way i do, just shoot an email :)

---

### Post by svaiyapu on 2006-07-16
Please see

[http://oande.blogspot.com/2006/07/oracle-10gr2-on-ubuntu-dapper-amd64.html](http://oande.blogspot.com/2006/07/oracle-10gr2-on-ubuntu-dapper-amd64.html)

Best Regards,
-senthil

---

