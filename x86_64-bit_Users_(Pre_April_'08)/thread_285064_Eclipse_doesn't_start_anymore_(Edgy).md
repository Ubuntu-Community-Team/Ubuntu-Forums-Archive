---
title: "Eclipse doesn't start anymore (Edgy)"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bill Cosby on 2006-10-26
Hey all,

after I upgraded to Edgy x64 I installed Eclipse 3.2 from the repository, everything went fine.

But when I want to start eclipse it stops after the splash screen with the message, that I should look in a log file, here is the output of that file:

```
!ENTRY org.eclipse.osgi 4 0 2006-10-26 15:49:00.275
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

After some search on the net I think this must be because of SWT, I am not sure though.

Thanks for any help,
Bill

---

### Post by rmjb on 2006-10-26
Hi, this bug is being worked on. You can track the progress here:
[https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/68053](https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/68053)

- rmjb

---

### Post by Sparticuz on 2006-10-26
Is this an incompatibility between Edgy64, or just a weird problem.

---

### Post by ploosqva on 2006-11-01
> **Sparticuz said:**
> Is this an incompatibility between Edgy64, or just a weird problem.
Probably just a temporary problem. For now it seem just fine to use a version downloaded from eclipse website. Actually you won't probably need a repo package.

---

### Post by svurg on 2006-11-18
I'm still stuck on this problem.  I reloaded all the packages -- still get it.  I tried downloading the latest jdk from sun and the latest eclipse from eclipse.org, putting them in /opt, and starting eclipse with:

/opt/eclipse/eclipse -vm /opt/jdk1.5.0_09/bin/java

as was suggested in another thread.  Same error.

Bug #68053 (and related bug #68380 still haven't had any resolutions.

I'd really like to use 3.2, but right now I'm dead in the water.  Anybody got any suggestions as to how to move forward again?

--wjm

---

### Post by cosine7 on 2006-11-18
```
sudo /usr/lib/eclipse/eclipse
```

Will get eclipse running, but it will try and load the root workspace, you have to goto /home/username/workspace it will load

---

### Post by svurg on 2006-11-19
> **cosine7 said:**
> ```
sudo /usr/lib/eclipse/eclipse
```

Will get eclipse running, but it will try and load the root workspace, you have to goto /home/username/workspace it will load

Afraid this gave me the same memmove error (though as you noted it put it in /root/workspace/.metadata/.log).

What puzzles me is that some people are reporting that downloading eclipse and java directly from eclipse.org/sun and running them (as opposed to using the repository versions) works properly, yet for me both produce the memmove error.

I guess my next step is to try using the debdiff in bug 68380 to patch the repository eclipse source.

Either that or just call it a day and go back to emacs! :) 

Any other suggestions would be greatly appreciated.

wjm

---

### Post by zingo on 2006-11-19
> 
Any other suggestions would be greatly appreciated.


Well I use my "Developing time" to play PlaneShift now! :cool: 

/Zingo

---

### Post by evgol on 2006-11-20
> **zingo said:**
> Well I use my "Developing time" to play PlaneShift now! :cool: 

/Zingo

As many of us. ;) Interesting, this bug makes x64 version of Edgy simply useless for many people. No java app that relies on SWT (Azureus for example) works because of this. Why nobody cares? As far as I understand it is just a matter of repackaging...

---

### Post by zingo on 2006-11-21
Just my luck planeshift is also down due to client and server update ....

---

