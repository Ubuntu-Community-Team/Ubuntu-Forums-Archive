---
title: "Eclipse IDE -- Monstrously Slow"
date: 2006-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Relain on 2006-10-20
Hey everyone,
So i finally thought i'd make the jump from using gedit to using one of those fancy new fangled integrated development environment gizmos. I've always hated these since i had to take a C class at Uni and was forced to use stupid stupid borland to work on my code {i used notepad and gcc in the end, thank god}. Anyway yeah so this project i'm working on got scattered overy too many files, had too many functions etc etc so it'd be IDEal (bad joke).

Anyway point is, eclipse is monstrously slow. It has this heap size / allocated heap size meter at the bottom and that shortly got > 600mb. Well what the hell is that all about? I have 2gb of ram but the project when compiled and running only uses about 512kb of system memory, and it doesn't leak at all. Why the hell was it allocating all that memory when it wasn't even running or compiling. 

I found that if i did something like save the project, make a new file, make a new class, or even open the help the whole thing would hang and hang and hang. 

ANyone else had problems like this? Please excuse my general pean against what is probably a lovely environment to develop in. For tech specs i have a Intel D 3.4 ghz and am running the 2.6.15-27-amd64 SMP kernel. 

I suppose the root of all this lies with java on 64bit? Is there anyway to make it go faster / not be crap? 

Thanks

---

### Post by Relain on 2006-10-20
Fixed, changed the JVM and it's much better

---

### Post by kuja on 2006-10-20
I had a funny feeling that's what it would have been.

---

### Post by rhuang on 2006-11-22
I had similar situation, eclipse ide hang and hang.... for about 3 minutes each time.  Was your problem fixed after JVM changes?  Can you tell me what the changes was?  Thanks](*,) ](*,) ](*,)

---

### Post by incubus on 2006-11-22
If I remember correctly, Ubuntu has "gcj" set to be the default JVM, even if you install Sun's package.  eclipse obeys the config file and uses that one by default.

I think you can change this by editing:
```

/etc/jvm

```

If it doesn't work, some tweaking at:
```

/usr/lib/jvm/

```
...should also do the trick.

incubus

---

### Post by FluffyElmo on 2006-11-22
You can specify any JVM for Eclipse at the command line. Generally I download the AMD64 .bin JDK installers direct from [http://java.sun.com](http://java.sun.com) and have them install to my home directory. I've used both 1.5.x and 1.6.x without problems.

```
eclipse/eclipse -vm /home/username/jdk1.5.0_08/bin/java
```

This works fine in a launcher so you don't have to keep typing it. Once it's running you can check the VM version being used by going to *Help->About Eclipse SDK->Configuration Details*.

Another note, if you are running programs using app servers or other heavy processes make sure that you kill them when you are done testing. The red square in the console window should do it. In some cases you can have multiple console windows running even though you are only using the last one launched.

Hope this helps...

---

### Post by RAOF on 2006-11-22
A better way to change the default JVM is by running
```
sudo update-alternatives --config java
```
and selecting the Sun JVM.  That way, all the java stuff will point to Sun's code.

---

### Post by jordoex on 2006-11-23
I had that problem, although I just ignored it and went to find something different because im using Xubuntu on a p2.  Hope it may run reasonably because im much too used to eclipse(i use it on my new windoze comp)

---

### Post by craiglarry on 2006-11-23
When it is working, it is the fastest system I have ever used including winxp 64, and I have only 512 mb of ram. My problem is that it jumps offline every couple of minutes.I believe what _you _can say is that this is not the system's fault. There is something else going on. 

> **Relain said:**
> Hey everyone,
So i finally thought i'd make the jump from using gedit to using one of those fancy new fangled integrated development environment gizmos. I've always hated these since i had to take a C class at Uni and was forced to use stupid stupid borland to work on my code {i used notepad and gcc in the end, thank god}. Anyway yeah so this project i'm working on got scattered overy too many files, had too many functions etc etc so it'd be IDEal (bad joke).

Anyway point is, eclipse is monstrously slow. It has this heap size / allocated heap size meter at the bottom and that shortly got > 600mb. Well what the hell is that all about? I have 2gb of ram but the project when compiled and running only uses about 512kb of system memory, and it doesn't leak at all. Why the hell was it allocating all that memory when it wasn't even running or compiling. 

I found that if i did something like save the project, make a new file, make a new class, or even open the help the whole thing would hang and hang and hang. 

ANyone else had problems like this? Please excuse my general pean against what is probably a lovely environment to develop in. For tech specs i have a Intel D 3.4 ghz and am running the 2.6.15-27-amd64 SMP kernel. 

I suppose the root of all this lies with java on 64bit? Is there anyway to make it go faster / not be crap? 

Thanks

---

### Post by v79 on 2006-11-23
How did you get eclipse working? I installed eclipse (apt-get), loads of dependences got installed, but I can't run it.

An error appears, and the resultant log message is:
> 
!SESSION 2006-11-23 18:59:33.932 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2006-11-23 18:59:38.830
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-23 18:59:38.831
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-23 18:59:38.831
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-23 18:59:38.832
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2006-11-23 18:59:39.115
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
          at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
        at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
        at org.eclipse.core.launcher.Main.run(Main.java:977)
        at org.eclipse.core.launcher.Main.main(Main.java:952)
  at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)

Any ideas?

---

### Post by incubus on 2006-11-24
I remember I wasn't happy with the eclipse package in the repositories.  Although I'm a big fan of the Debian way, now I just go to eclipse.org and download their latest package.

You can untar it as /opt/eclipse/ and run it normally. If you're tired of it, you just delete that directory.  No complicated installation whatsoever.

incubus

---

### Post by eheck on 2006-11-27
> **incubus said:**
> If I remember correctly, Ubuntu has "gcj" set to be the default JVM, even if you install Sun's package.  eclipse obeys the config file and uses that one by default.

That's not what hod139's post in this thread [http://ubuntuforums.org/showthread.php?t=183239](http://ubuntuforums.org/showthread.php?t=183239) says. I too found I had to edit /etc/eclipse/java_home.

---

### Post by WhiteHorse on 2006-12-23
Hey it works! I edited the /etc/eclipse/java_home as follows(I have Blackdown Java):

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

#/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

Oh BTW editing the ~/.eclipse/eclipserc didn't work for me.

---

### Post by {spitFire} on 2007-02-10
I've been facing this problem with Eclipse's slowdown and have tried all the solutions posted (rather that I managed to read through forums!) with nothing so far even coming closer to resolving the issues. 

  However, contrary to most people facing the problem, I was facing a slow down not only when Eclipse was starting up, but also whenever I typed a 'dot' in the editor, and waited for code-assist to kick in. My sense was that sometime when Eclipse was going through my JDK installation the problem was surfacing. 

  I tried firing up Eclipse as root, and viola! It works 'monstrously' fast!!! No exaggeration!
  Please try it and let me know what you experience.

  Now, the problem is I don't want to run Eclipse as root; can someone help me find a workaround?

---

### Post by uptimebox on 2007-04-21
```

echo "/usr/lib/jvm/java-1.5.0-sun" >> ~/.eclipse/eclipserc

```

---

### Post by LuckyDevil on 2007-11-06
> **WhiteHorse said:**
> Hey it works! I edited the /etc/eclipse/java_home as follows(I have Blackdown Java):

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

#/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

Oh BTW editing the ~/.eclipse/eclipserc didn't work for me.

Thanks a lot!  Changed the default order to search sun-java-6 first and my intellisense doesn't hang forever, program loads much faster as well.

Thanks!

---

