---
title: "Java issues"
date: 2007-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by danieljay on 2007-09-17
I am trying to install Zend on Ubuntu Feisty 64bit and I am getting the following:

> Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

'SWING' UI not supported by VM.  Reverting to AWT.
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.10258/Linux/resource/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.load0(Unknown Source)
        at java.lang.System.load(Unknown Source)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

I checked for java packages and it looks like it is installed:
> :~/Desktop$ dpkg -l |grep -i java
ii  bsh                                        2.0b4-4ubuntu4                         Java scripting environment (BeanShell) Versi
ii  gij                                        4.1.2-1ubuntu1                         The GNU Java bytecode interpreter
ii  gij-4.1                                    4.1.2-0ubuntu5                         The GNU Java bytecode interpreter
ii  j2re1.4                                    1.4.2.02-1                             Blackdown Java(TM) 2 Runtime Environment, St
ii  java-common                                0.25ubuntu2                            Base of all Java packages
ii  libgcj-common                              4.1.2-1ubuntu1                         Java runtime library (common files)
ii  libgcj7-0                                  4.1.2-0ubuntu5                         Java runtime library for use with gcj
ii  libhsqldb-java                             1.8.0.7-1ubuntu2                       Java SQL database engine
ii  libjaxp1.3-java                            1.3.03-5                               Java XML parser and transformer APIs (DOM, S
ii  libjline-java                              0.9.5-2ubuntu2                         Java library for handling console input
ii  libservlet2.3-java                         4.0-8ubuntu3                           Servlet 2.3 and JSP 1.2 Java classes and doc
ii  libxalan2-java                             2.7.0-1ubuntu3                         XSL Transformations (XSLT) processor in Java
ii  libxerces2-java                            2.8.1-1ubuntu3                         Validating XML parser for Java with DOM leve
ii  openoffice.org-java-common                 2.2.0-1ubuntu4                         OpenOffice.org office suite Java support arc
ii  sun-java5-bin                              1.5.0-11-1ubuntu2                      Sun Java(TM) Runtime Environment (JRE) 5.0 (
ii  sun-java5-jre                              1.5.0-11-1ubuntu2                      Sun Java(TM) Runtime Environment (JRE) 5.0 (

Any ideas?

---

### Post by duagne on 2007-10-23
Before you try running the installation, run these two lines from the command line.  It worked for me.

sudo apt-get install libc6-i386

sudo apt-get install ia32-libs

---

