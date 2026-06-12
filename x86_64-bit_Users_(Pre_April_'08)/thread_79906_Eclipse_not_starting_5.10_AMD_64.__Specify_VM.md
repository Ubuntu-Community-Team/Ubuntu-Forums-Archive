---
title: "Eclipse not starting 5.10 AMD 64.  Specify VM?"
date: 2005-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by amchugh on 2005-10-21
Am I crazy for trying to get eclipse to run?  It seems to be broken.  Do I have to get it to work with Sun's Java?  There is a -vm flag, but I don't know what path to specify.

> An error has occurred. See the log file /home/me/.eclipse/org.eclipse.platform_3.1.1/configuration/1129880656905.log.

As follows:

> !SESSION 2005-10-21 00:44:16.814 -----------------------------------------------
eclipse.buildId=
java.fullversion=GNU libgcj 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.osgi 2005-10-21 00:44:19.198
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
[snip]

java -version

> java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)


---

### Post by jesterfred on 2005-10-21
I've seen behavior like this before when one has multiple JDK's installed.  In the case of Ubuntu, the gnu java packages are installed.  It looks like you have also installed JDK 5.  Try the following in a terminal window:

export JAVA_HOME=<path to your JDK 5 top level dir>
export PATH=$JAVA_HOME/bin:$PATH
eclipse

This will start eclipse using the JDK 5 exclusively.

If this works for you, you can add the export commands to your .gnomerc file, log out, then log in.  This should fix the problem when running exlipse from the GUI.

Hope this helps

---

### Post by amchugh on 2005-10-21
Thanks, that seemed to help a little.  I'm now getting the following errors in the log.

```
!SESSION 2005-10-21 12:40:30.486 -----------------------------------------------
eclipse.buildId=
java.version=1.5.0_05
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.osgi 2005-10-21 12:40:36.143
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClassInternal(Unknown Source)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Unknown Source)
	at java.lang.Class.getConstructor0(Unknown Source)
	at java.lang.Class.newInstance0(Unknown Source)
	at java.lang.Class.newInstance(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	... 55 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Unknown Source)
	at java.lang.Class.getConstructor0(Unknown Source)
	at java.lang.Class.newInstance0(Unknown Source)
	at java.lang.Class.newInstance(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClassInternal(Unknown Source)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-10-21 12:40:36.146
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	... 27 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-10-21 12:40:36.148
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:405)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-10-21 12:40:36.152
!MESSAGE Bundle update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar [23] was not resolved.

```

---

### Post by yqiang on 2005-10-22
Same behavior here, anyone have ideas?

---

### Post by mpat on 2005-10-22
Hi there,

I'm runnig Eclipse 3.2M2 with GEF, Clay, PHPEclipse and some more plugins and everything works fine.

I downloaded Eclipse directly from [www.eclipse.org](www.eclipse.org) and the Java JRE 5.0 directly from java.sun.com. Then I installed the JRE with sudo and moved it to **/opt/jre1.5.0_05/**. I unpacked Eclipse together with all my plugins into **~/apps/eclipse/**. For the correct PATH and JAVA_HOME I created a small Bash script in ~/apps/eclipse-start containing

```
#!/bin/bash
export PATH=/opt/jre1.5.0_05/bin:"${PATH}"
export JAVA_HOME=/opt/jre1.5.0_05
/home/me/apps/eclipse/eclipse
```

Then I created a launcher on my GNOME desktop starting this script. Everything works fine - besides: Eclipse 3.2M2 seems to be quite stable already. No errors happend to me - yet...:cool: 
Hope this helps you out.

---

### Post by yqiang on 2005-10-22
Yeah, getting the official package works great here, I think the eclipse package is just foobared.

---

### Post by amchugh on 2005-10-23
Thanks, that did the trick.  Foobared is right.

---

