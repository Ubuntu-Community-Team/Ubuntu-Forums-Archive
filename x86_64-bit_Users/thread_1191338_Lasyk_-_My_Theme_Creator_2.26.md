---
title: "Lasyk - My Theme Creator 2.26"
date: 2009-06-18
forum: x86 64-bit Users
---

### Post by alliance1975 on 2009-06-18
Trying to launch Lasyk's My Theme Creator linux distro. Unzipped file to yield 2 items: mTC.jar and lib folder. Notes say to keep lib folder with mTC.jar in same directory. Must have java 1.5 or greater. Terminal readout follows:

chris@hpdv5k:~$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)
chris@hpdv5k:~$

chris@hpdv5k:~$ cd /home/chris/MCDApps/MTC
chris@hpdv5k:~/MCDApps/MTC$ java -jar mTC.jar
Exception in thread "AWT-EventQueue-0" java.lang.UnsatisfiedLinkError: no jdic in java.library.path
at java.lang.ClassLoader.loadLibrary(ClassLoader.java :1709)
at java.lang.Runtime.loadLibrary0(Runtime.java:823)
at java.lang.System.loadLibrary(System.java:1030)
at org.jdesktop.jdic.browser.internal.WebBrowserUtil$ 1.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at org.jdesktop.jdic.browser.internal.WebBrowserUtil. loadLibrary(Unknown Source)
at org.jdesktop.jdic.browser.internal.WebBrowserUtil. getDefaultBrowserPath(Unknown Source)
at org.jdesktop.jdic.browser.BrowserEngineManager.sel ectEngine(Unknown Source)
at org.jdesktop.jdic.browser.BrowserEngineManager.get ActiveEngine(Unknown Source)
at mTC.LSKInterface.initLSKComponents(LSKInterface.ja va:2447)
at mTC.LSKInterface.<init>(LSKInterface.java:194)
at mTC.LSKInterface$1.run(LSKInterface.java:171)
at java.awt.event.InvocationEvent.dispatch(Invocation Event.java:209)
at java.awt.EventQueue.dispatchEvent(EventQueue.java: 597)
at java.awt.EventDispatchThread.pumpOneEventForFilter s(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(E ventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarch y(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispa tchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispa tchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThre ad.java:122)

"no jdic in java.library.path" seems to be problem. A solution proposed by a java forum said "For solaris/unix/linux, put folder contains libjdic.so into the LD_LIBRARY_PATH"

Only 3 libjdic.so exist on my puter in the following folders:
 /usr/lib/jni, /usr/lib/frostwire and /home/chris/MCDApps/MTC/lib/linux/x86

My Theme Creator will not even launch. I don't want to screw anything up. I can't help thinking that the mtc lib must somehow be moved to the /usr/lib/... folder.

Anyone got any suggestions?

---

### Post by alliance1975 on 2009-06-19
As Inspector Clouseau would say, "beump"

---

### Post by alliance1975 on 2009-06-20
No need to reply. The software has a windows version that I know works. I will load on my pc instead.

---

