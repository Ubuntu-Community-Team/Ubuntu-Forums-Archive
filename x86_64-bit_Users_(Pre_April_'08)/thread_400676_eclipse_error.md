---
title: "eclipse error"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by mdorn01 on 2007-04-03
When I try to start eclipse i get this error message :
An error has occurred. See the log file
/home/compy/workspace/.metadata/.log.

and then this is the log file.

```
!SESSION 2007-04-03 20:16:07.399 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.720
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.721
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.722
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.722
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-04-03 20:16:13.080
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

I installed from synaptec, i added the proposed updates repo and updated, i have java 1.5 as default and told eclipse where to look for it.

any speedy help would be greatly appreciated as i need eclipse to pass my CS class!
thanks.

---

### Post by KiwiDalang on 2007-04-05
I have exactly the same error.

---

### Post by Cesa on 2007-04-05
Me too, except I don't get java.lang.UnsatisfiedLinkError, but a bunch of other errors instead. I just downloaded the Eclipse update from Ubuntu's automatic software updates, could that be the problem? Any way to "downgrade"?

---

### Post by mdorn01 on 2007-04-08
it didnt work with the lower version either.  ive tried installing from the eclipse site and through synaptic, neither work.:mad:

---

### Post by cobray on 2007-04-08
I had the same problem installing eclipse thru synaptic.

I fixed it by going to the eclipse web site and downloading the eclipse sdk 3.2.2
and untarring it in my home directory.

Everything is working great
(note I have the sun-java5 and sun-java6 packages installed thru synaptic)
HTH

---

### Post by mdorn01 on 2007-04-10
ok, i went to eclipse.org, downloaded and untarred in my home directory, now i get the following error.

```
JVM terminated. Exit code=127
/usr/bin/java
-Xms40m
-Xmx256m
-jar /home/compy/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /home/compy/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 9b58014
-vm /usr/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /home/compy/eclipse/startup.jar 

```

---

### Post by tooCanad on 2007-04-11
I gave up on Eclipse and have been using netbeans with no issue.

---

### Post by mdorn01 on 2007-04-11
ok, i got it to start up by entering 
```
java -jar *path to eclipse*/startup.jar
```

not sure why this works but it does, so i just added a button on my panel to get it open so i dont have to open the terminal and type in that code everytime. thanks for the help guys.

---

### Post by adielkhan on 2007-04-20
try setenv MOZILLA_FIVE_HOME ""

see : [https://eclipse.org/bugs/show_bug.cgi?id=174642](https://eclipse.org/bugs/show_bug.cgi?id=174642)

thanks
Adiel.

---

### Post by jespdj on 2007-04-24
> **KiwiDalang said:**
> I have exactly the same error.

See [this thread](http://ubuntuforums.org/showthread.php?t=281080) where someone else had the same error (scroll down a bit!).

---

### Post by EnkiduinNZ on 2007-04-29
I also have this problem. I've done everything suggested in the various posts here and other places around the Web, including installing the version from the 'edgy-proposed' packages, but with no luck. 

My current versions are : 3..2.1-0ubuntu2

I've even totally removed and reinstalled eclipse including configuration files.

I hope this gets fixed soon.

Cheers,

Cliff

---

### Post by EnkiduinNZ on 2007-05-05
This worked for me - at least, Eclipse now starts, but I've not used it for anything yet. \\:D/ 

1) Removed Eclipse and libswt3.2 completely. i used Synaptic and marked the packages for 'complete removal'

2) removed all '.eclipse' directories and all 'workspace' directories. (Take a backup of 'workspace' of course).

3) Ensure that the 'edgy-proposed' locations are specified in Apt's sources.list. (This can be done through Synaptic or direct editting).

4) Run apt-get update or hit 'reload' in synaptic.

5) Remove all traces of eclipse. This includes /usr/lib/eclipse. I used 'locate eclipse'. 

6) Install 'eclipse' and 'libswt3.2'.

Then Eclipse starts for me.

I think the crucial step is step 5) since I did all the other steps more than once!

Cheers,

Cliff

---

