---
title: "RadRails on Edgy64bit?"
date: 2006-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by v79 on 2006-11-09
Hello,

Have any Ruby developers managed to get RadRails working on Edgy 64-bit? The program fails to run for me, probably an problem Java I think.

Here is the error output (in metadata/log)

```
!SESSION 2006-10-31 22:48:52.577 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.4.2-02
java.vendor=Blackdown Java-Linux Team
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2006-10-31 22:48:57.182
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: wrong ELF class: ELFCLASS32
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1586)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1495)
	at java.lang.Runtime.loadLibrary0(Runtime.java:788)
	at java.lang.System.loadLibrary(System.java:834)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.radrails.ide.ui.RadRails.createDisplay(RadRails.java:104)
	at org.radrails.ide.ui.RadRails.run(RadRails.java:59)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2006-10-31 22:48:57.199
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-10-31 22:48:57.199
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-10-31 22:48:57.199
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2006-10-31 22:48:57.203
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-10-31 22:48:57.203
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ [84] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-10-31 22:48:57.203
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).
!SESSION 2006-11-08 13:18:40.320 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2006-11-08 13:18:46.499
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: wrong ELF class: ELFCLASS32
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:993)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.radrails.ide.ui.RadRails.createDisplay(RadRails.java:104)
	at org.radrails.ide.ui.RadRails.run(RadRails.java:59)
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

!ENTRY org.eclipse.osgi 2 0 2006-11-08 13:18:46.509
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-08 13:18:46.509
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-08 13:18:46.509
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2006-11-08 13:18:46.525
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-08 13:18:46.525
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ [84] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-08 13:18:46.525
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).
!SESSION 2006-11-08 13:32:38.424 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2006-11-08 13:32:45.958
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: wrong ELF class: ELFCLASS32
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:993)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.radrails.ide.ui.RadRails.createDisplay(RadRails.java:104)
	at org.radrails.ide.ui.RadRails.run(RadRails.java:59)
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

!ENTRY org.eclipse.osgi 2 0 2006-11-08 13:32:45.969
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-08 13:32:45.969
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-08 13:32:45.970
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2006-11-08 13:32:45.973
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-08 13:32:45.974
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ [84] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-08 13:32:45.974
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).
!SESSION 2006-11-09 18:46:57.786 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2006-11-09 18:47:00.801
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: wrong ELF class: ELFCLASS32
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:993)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.radrails.ide.ui.RadRails.createDisplay(RadRails.java:104)
	at org.radrails.ide.ui.RadRails.run(RadRails.java:59)
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

!ENTRY org.eclipse.osgi 2 0 2006-11-09 18:47:00.912
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-09 18:47:00.912
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-09 18:47:00.912
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2006-11-09 18:47:00.916
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-09 18:47:00.916
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ [84] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-09 18:47:00.917
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).
!SESSION 2006-11-09 18:47:07.128 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2006-11-09 18:47:08.461
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: /home/liam/Development/RubyOnRails/radrails/configuration/org.eclipse.osgi/bundles/47/1/.cp/libswt-pi-gtk-3232.so: wrong ELF class: ELFCLASS32
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:993)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.radrails.ide.ui.RadRails.createDisplay(RadRails.java:104)
	at org.radrails.ide.ui.RadRails.run(RadRails.java:59)
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

!ENTRY org.eclipse.osgi 2 0 2006-11-09 18:47:08.577
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-09 18:47:08.578
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-09 18:47:08.578
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2006-11-09 18:47:08.582
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-11-09 18:47:08.588
!MESSAGE Bundle update@plugins/org.eclipse.platform_3.2.0.v20060601/ [84] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-11-09 18:47:08.589
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).

```

Thanks,

v79

---

### Post by the_burk on 2006-11-13
do you got java 1.4 installed... i think its in the multiverse repos.. there are no java that are fully fuctional in 64 bit yet ... blackberry 1.4 i think is called is the best...

---

### Post by FluffyElmo on 2006-11-13
I have RADRails running perfectly. Java works perfectly on AMD64, only the web browser integration (applets, webstart) is missing. For Java development and Java desktop applications it's actually better than 32bit.

I'm not sure exactly how I got Rails itself running, it wasn't hard I just had to install a bunch of packages from the repository. Assuming you have Ruby and Rails up and running, you can install RADRails this way...

1. Download the latest AMD64 JDK from [http://java.sun.com]("http://java.sun.com"). Change the permissions (chmod 777 *filename*) on the resulting *.bin* file and run it. This should install the JVM into your home directory. Either 1.5.x or 1.6.x will work fine.

2. Download Eclipse 3.2 from [http://eclipse.org]("http://eclipse.org") and extract it into your home directory. You should then be able to run eclipse using the following command (adjust path to JDK and Eclipse to match your system):
```
*~username*/eclipse/eclipse -vm *~username*/jdk1.6.0/bin/java
```

3. In Eclipse go to *Help->Software Updates->Find & Install->Search for New Features*. Add *[http://updatesite.rubypeople.org/release](http://updatesite.rubypeople.org/release)* make sure it's selected and then click *Finish*. Follow the wizard to install the features, then restart Eclipse. Now Add *[http://radrails.sourceforge.net/update](http://radrails.sourceforge.net/update)* make sure it's selected and then click *Finish*. Install and restart again.

4. You will also want Subversion installed, so in Eclipse go to *Help->Software Updates->Find & Install->Search for New Features*. Add *[http://subclipse.tigris.org/update_1.2.x](http://subclipse.tigris.org/update_1.2.x)* make sure it's selected and then click *Finish*. 

Note that I add the features one at a time, since with the latest Eclipse it tends to crash when checking more than one update site at once. It never used to do this and I assume this may be fixed but as of a week ago this was the case so one at a time is the way to go.

Once you install and restart Eclipse you can access the RADRails perspective through *Window->Open Perspective->Other*.

Good luck and have fun...if you have any problems just ask.

---

