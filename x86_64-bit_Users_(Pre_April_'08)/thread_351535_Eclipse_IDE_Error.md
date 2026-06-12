---
title: "Eclipse IDE Error"
date: 2007-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Codestorm on 2007-02-02
I'm curious if anyone has encountered any problems running Eclipse 3.2 (installed from the Add/Remove Applications utility in Ubuntu)

I receive an error immediately after Eclipse's splash screen disappears, which goes a little something like "An error has occurred. See the log file /home/user/workspace/.metadata/.log".

The contents of the log file follows:
```
!SESSION 2007-02-02 19:31:15.015 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2007-02-02 19:31:21.942
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-02 19:31:21.943
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-02 19:31:21.943
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-02 19:31:21.943
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-02-02 19:31:22.350
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
	at org.eclipse.swt.internal.gtk.OS.memmove(Native Method)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
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
This means nothing to me as I know nothing of Eclipse internals or Java for that matter (I use Eclipse with the PDT extension).

I realise this is probably an issue I need to report to the Eclipse developers, but perhaps someone here can shed some light on the issue, and perhaps knows of a remedy...

---

### Post by mizar001 on 2007-02-02
Please make sure to execute eclipse with a sun java runtime environment, not the version bundled with ubuntu. 
Furthermore try the clean version(without plugins).
Other possible solutions :
try the -clean option at command line : $>eclipse -clean

---

### Post by sludge99 on 2007-02-02
ive had a problem with eclipse from the ubuntu repos for a very long time i would recommend to just download eclipse from the official site and install it to /opt/eclipse that worked just great for me

edit:
i prity sure i was having the same error as you it was some file not found error

---

### Post by Codestorm on 2007-02-02
> **mizar001 said:**
> Please make sure to execute eclipse with a sun java runtime environment, not the version bundled with ubuntu. 
Furthermore try the clean version(without plugins).
Other possible solutions :
try the -clean option at command line : $>eclipse -clean

I'm using the latest JRE from the Sun website, and it's a clean version/install, this is the first time I've tried to run it (since upgrading to Edgy).

I'll give the official Eclipse package a whirl and see how things go.

---

### Post by phossal on 2007-02-02
I think the other gents are correct about download eclipse direct. I'd install a dedicated Java, too. Get version 6. Plus, I recommend pulling the 32Bit packages, rather than using the 64Bit. I've found the combination works best (after trying a couple dozen others) - their cooperation rivals the performance of eclipse on my Windows box.

Cheers!

---

### Post by dazlari on 2007-02-03
I'm having this problem right now too. There's a thread on it here: [https://launchpad.net/ubuntu/+source/eclipse/+bug/68053](https://launchpad.net/ubuntu/+source/eclipse/+bug/68053)  which I add for completeness,  though there's nothing there that I'm willing to try outright - as patching an compiling eclipse is not my idea of a good time.   I am going to try the above, I prefer the download and run option any day  :)

---

### Post by dazlari on 2007-02-03
Happy to report that this working nicely - best advice I've had all day.
---
Linux monolith 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_08-b03, mixed mode)

Eclipse Version: 3.2.1
Build id: M20060921-0945

---

