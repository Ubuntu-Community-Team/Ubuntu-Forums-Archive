---
title: "64bit gtk confusion and problems with eclipse"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by BradNeuman on 2007-03-16
Hello everyone, I am running Dapper (6.06) and have previously had success using Eclipse. Then I suddenly had a bunch of issues with java versions, got angry, and uninstalled it. Now I am trying to re-install it and I get this problem with the download from eclipse.org and the repositories:

(eclipse:6492): Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",
 
It also creates and error log:
```

eclipse.buildId=M20070212-1330
java.version=1.5.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2007-03-16 17:10:02.164
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/bneuman/Desktop/Downloads/eclipse/configuration/org.eclipse.osgi/bundles/80/1/.cp/libswt-pi-gtk-3236.so: /home/bneuman/Desktop/Downloads/eclipse/configuration/org.eclipse.osgi/bundles/80/1/.cp/libswt-pi-gtk-3236.so: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
        at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
        at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
        at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
        at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
        at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
        at org.eclipse.core.launcher.Main.run(Main.java:977)
        at org.eclipse.core.launcher.Main.main(Main.java:952)


```
I can successfully compile and run a test java app from the command line.

```

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)


javac 1.5.0_06
javac: no source files


```

Any ideas? I am sure I just don't have everything installed properly or something

---

### Post by Kilz on 2007-03-16
> **BradNeuman said:**
> Hello everyone, I am running Dapper (6.06) and have previously had success using Eclipse. Then I suddenly had a bunch of issues with java versions, got angry, and uninstalled it. Now I am trying to re-install it and I get this problem with the download from eclipse.org and the repositories:

(eclipse:6492): Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",
 
It also creates and error log:
```

eclipse.buildId=M20070212-1330
java.version=1.5.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2007-03-16 17:10:02.164
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/bneuman/Desktop/Downloads/eclipse/configuration/org.eclipse.osgi/bundles/80/1/.cp/libswt-pi-gtk-3236.so: /home/bneuman/Desktop/Downloads/eclipse/configuration/org.eclipse.osgi/bundles/80/1/.cp/libswt-pi-gtk-3236.so: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
        at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
        at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
        at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
        at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
        at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
        at org.eclipse.core.launcher.Main.run(Main.java:977)
        at org.eclipse.core.launcher.Main.main(Main.java:952)


```
I can successfully compile and run a test java app from the command line.

```

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)


javac 1.5.0_06
javac: no source files


```

Any ideas? I am sure I just don't have everything installed properly or something

You might want to try and install the gtk2-engines-gtk-qt package, it might get rid of the first error. There are also a few other packages that come up in a synaptic search for "gtk engines" with qt in the name that might help.

---

### Post by BradNeuman on 2007-03-17
Oh yeah I probably should have mentioned that I already had those installed and have tried reinstalling it just for fun but to no avail.

---

### Post by phossal on 2007-03-17
Brad, what problems did you have with Java versions?

---

### Post by Kilz on 2007-03-17
> **BradNeuman said:**
> Oh yeah I probably should have mentioned that I already had those installed and have tried reinstalling it just for fun but to no avail.

Its possible that the eclipse from eclipse.org is 32bit. In that case you will need to manualy install the 32bit versions of the engine and java. The 32bit Eclipse will not be able to find the 64bit versions that the repositories install.

---

### Post by cobray on 2007-03-18
I had similar error and major headaches trying to install eclipse from synaptic.
I installed 64bit version from eclipse web site (untarred into my home directory) and everything works great.

I installed suns jdk 5 using synaptic.

---

