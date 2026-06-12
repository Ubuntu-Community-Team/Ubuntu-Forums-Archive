---
title: "Anyone got java web start workin on Hardy AMD64?"
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by catabriga on 2008-08-29
I have spend hours searching how to make java web start work in my Hardy Hedron AMD64, but couldn't make it work so far. When I run it with openJDK nothing happens at all, and when I run it with sun java 32-bit, the "java starting" even splash appears, but I get the following error (trying to launche topcoders arena):

```
com.sun.deploy.net.FailedDownloadException: Unable to load resource: http://www.topcoder.com/contest/arena/ContestAppletProd.jnlp
	at com.sun.deploy.net.DownloadEngine.actionDownload(DownloadEngine.java:961)
	at com.sun.deploy.net.DownloadEngine.getCacheEntry(DownloadEngine.java:1059)
	at com.sun.deploy.net.DownloadEngine.getResourceCacheEntry(DownloadEngine.java:1134)
	at com.sun.deploy.net.DownloadEngine.getResourceCacheEntry(DownloadEngine.java:1068)
	at com.sun.deploy.net.DownloadEngine.getResource(DownloadEngine.java:142)
	at com.sun.deploy.net.DownloadEngine.getResource(DownloadEngine.java:127)
	at com.sun.javaws.Launcher.updateFinalLaunchDesc(Launcher.java:245)
	at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:127)
	at com.sun.javaws.Launcher.launch(Launcher.java:95)
	at com.sun.javaws.Main.launchApp(Main.java:300)
	at com.sun.javaws.Main.continueInSecureThread(Main.java:210)
	at com.sun.javaws.Main$1.run(Main.java:107)
	at java.lang.Thread.run(Thread.java:619)
```

---

### Post by Thelasko on 2008-08-29
[I do]("http://ubuntuforums.org/showthread.php?t=890143&highlight=java"), for the most part.  Make sure you don't have any other Java packages installed other than the OpenJDK ones.

---

### Post by Sef on 2008-08-29
Sun Java is not made for 64-bit systems at this time.  OpenJDK is.  It is an open source version of Sun Java.  It is available from Add/Remove.

---

### Post by catabriga on 2008-08-29
I have openJDK installed, but when I tried to run it nothing happens. The first time I run it (after installation) it opens a window asking where to store cache files (or something like that), but that's it, the application is never launched. 

I tried uninstalling the sun java packages I have installed and some other packages, but there was no difference (as I expected because I can choose with what I want to open the .jnlp file).

I can run everything made in java, applets, jars, etc, except .jnlp. I really need to solve that, does anyone have a clue of what it might be?

---

### Post by Sef on 2008-08-29
Have you seen [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz") on installing 32-bit firefox with java?

---

### Post by catabriga on 2008-08-30
> **Sef said:**
> Have you seen [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz") on installing 32-bit firefox with java?

I haven't followed that tutorial because my applets and flash are already running with firefox. The only problem is the jnlp, which I think is not related to any web browser, it opens only with java.

---

### Post by doubleallergic on 2008-09-18
> **catabriga said:**
> I haven't followed that tutorial because my applets and flash are already running with firefox. The only problem is the jnlp, which I think is not related to any web browser, it opens only with java.

You are right - the problem is java related. If you're using ia32-sun-java6-bin to run webstart mode on 64bit hardy, you may be missing the lib32nss-mdns library. 

This is a required lib but java does not have an enforced dependency on it for some reason?

See the related bug here: [https://bugs.launchpad.net/ubuntu/+bug/220530](https://bugs.launchpad.net/ubuntu/+bug/220530)

---

### Post by vk_rams on 2009-04-10
Hi Guys,

Follow the below instructions to open with webstart

1. First remove your open jre by the following command
sudo apt-get remove openjdk-6jre (this is depends on your version)
2. After removing openjdk type javaws on your terminal, it should say command not found. If it is true follow the below steps otherwise open jdk or jre doesn't removed properly. Go to Step 1
3. Now download jdk1.6.0_13 from sun.java website and extract it on your Desktop
4. Run this command
sudo cp ~/Desktop/jdk1.6.0_13 -R /usr/java
5. Create a simlink to /usr/bin. Run the below command
ln -s /usr/java/jdk1.6.0_13/bin/javaws /usr/bin
6. Now type javaws in terminal. You should get like this, I am providing you some content below...

Java(TM) Web Start 1.6.0_13
Usage:  javaws [run-options] <jnlp-file>
        javaws [control-options]

where run-options include:
  -verbose              display additional output
  -offline              run the application in offline mode
  .............


Launching the application
---------------------------
1. open your terminal and type
javaws <application link location>

eg: javaws [http://blabla.com/blabla.jnlp](http://blabla.com/blabla.jnlp)
or
javaws ~/Desktop/blabla.jnlp

Seems to be a lengthy procedure. But will help you sure :guitar:

---

### Post by vk_rams on 2009-04-13
Hey did you got it?

---

### Post by Thelasko on 2009-04-13
> **vk_rams said:**
> Hey did you got it?

This thread is old and dead.  Sun released a 64-bit version of Java, including web start, [long ago]("http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ").

---

