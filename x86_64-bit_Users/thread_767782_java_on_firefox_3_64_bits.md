---
title: "java on firefox 3 64 bits"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by KhaosMind on 2008-04-25
i been reading about java on 64bits. I installed restricted extras and everything works fine. I dont use java a lot. but i would like to play some games on nintendo8.com and i dont know how. could anyone point me to a guide on how to make java work on firefox 3?

thanks

---

### Post by sluger1138 on 2008-04-25
> **KhaosMind said:**
> i been reading about java on 64bits. I installed restricted extras and everything works fine. I dont use java a lot. but i would like to play some games on nintendo8.com and i dont know how. could anyone point me to a guide on how to make java work on firefox 3?

thanks
I have tried many different approaches, all failed due too my inexperience with Ubuntu.Just Migrated from PClinuxOS, in December. 3 installs later, and  am very happy, Ubuntu works great on 64BIT.But I have tried installing Java from repos, followed the instructions on "how too" at Klitz,s thread, and others.Want to play Texas Holdem on Club Pogo.
     Had Java working great on first install Feisty fawn, by downloading the swift 
weasel browser , mdswrapper for flash, and it got Firefox 3 too work also.But now, With 7.10, cannot play poker on-line at Pogo.Hopefully this weekend my Linux PRO Buddy will configure the Java with me, and will subscribe too this thread, and with any luck will be able too help you, or get some help.
Good Luck KhaozMind/ Which restricted extras did you add?
:guitar:
Cheers

---

### Post by Neo Adventist on 2008-04-26
On my fresh, brand-new install of Hardy Heron 64, the very FIRST thing I did after establishing my internet connection was to use Synaptic and mark "icedtea-gcjwebplugin" for download. After it and many related packages downloaded and installed, I now could view every Java runtime applet Firefox has thrown at me so far, even the ones on [http://java.com](http://java.com)

The SECOND thing I did is run "sudo apt-get install flashplugin-nonfree". Youtube is now at my mercy. Mwua ha ha ha!

"Ubuntu-restricted-extras" should be the LAST thing they download and install.

My Lexmark printer is still as uncooperative as ever; but hey, it's Lexmark. Their Linux support sucks. I'm upgrading to a Hewlett-Packard soon.

---

### Post by anfractuosities on 2008-04-29
NEO...No dice here...I tried this method and java is still not working. any sugestions?

Here is the results of java -verison

```

java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)

```

one thing I noticed is that there is no sun-java -plugins in my synaptic, and I ran across someone installing this file manually in another thread...

The applet "loads" but they some are blank.

the ones that do load, seem to take a very long time.


***********K, I think its working

---

### Post by Julius on 2008-04-29
icedtea-gcjwebplugin and the openJDK did the trick for me. anyway I dont use java applets anyway


I just realized that openJDK replaces the /usr/bin/java link with the openJDK, even if I had suns java installed before. I mean, damn, for one thing that they DO have in 64 bit, openjdk replaces it :(  (just the link :P)

---

### Post by Sef on 2008-05-04
> ...one thing I noticed is that there is no sun-java -plugins in my synaptic....

There is no java plug-in for 64-bit systems.  OpenJDK is the easiest way to get Java.  Read [my sticky]("http://ubuntuforums.org/showthread.php?t=774956") for more information on OpenJDK.

---

### Post by IronWolve on 2008-05-05
Same issue with Vista x64, use java 32 bit plugin, there is no 64 bit plugin for firefox.

---

### Post by old_geekster on 2008-05-06
This worked for me: sudo update-alternatives --config java

Here are the results:

gene@Linuxbox-Ubuntu:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/ia32-java-6-sun/jre/bin/java' to provide 'java'.
gene@Linuxbox-Ubuntu:~$ 

As you can see I chose "2" which is 32-bit java.  Everything is working perfectly for me.  See my signature for the specs on my rig.

---

### Post by peakshysteria on 2008-05-06
java -version gives me:

java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)


How did you get the ia32-sun?

sudo update-alternatives --config java gives me:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-gcj/jre/bin/java
*+        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/gij-4.2
          4    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

Last time I choose java-6-sun I lost sound in Yuotube and other flash sites. Had to enable openjdk for FF tomake it work again. My CPU is 100% while playing flash now for some strange reason.

How did you manage to install 32 bit java? And does your bank work with this setup? Mine can't load java applets even though java is installed.

---

### Post by jeffhoye on 2009-03-15
Hey all, I use ubuntu too, but only experienced the problem on Vista x64, maybe it is related.  

The problem was with FireFox 3.0.7 , Java 6.0_12-b04: Java Applets were blank. 

Vista x64, Java Plugin in Internet Explorer worked just fine.

Couldn't find a solution on the net.  Futzed for a while and found that you need to do the following: 

1) go to the Java Control Panel (search to find out how)

2) Advanced | Java Plug-in

3) _Disable_ "Enable the next-generation Java Plug-in (requires browser restart)"

4) Make sure to enable Mozilla family in Default Java for browsers

Hope this helps someone!

---

### Post by Kareeser on 2009-03-16
> **IronWolve said:**
> Same issue with Vista x64, use java 32 bit plugin, there is no 64 bit plugin for firefox.
Lies. I've been running 64-bit Java on my 64-bit machine for a month now.

[http://download.java.net/jdk6/6u14/](http://download.java.net/jdk6/6u14/)

---

### Post by jespdj on 2009-03-16
> **Kareeser said:**
> Lies. I've been running 64-bit Java on my 64-bit machine for a month now.
Yes, but at the time IronWolve wrote this (May 6th, 2008) it was true!

see this for installation instructions:
[http://ubuntuforums.org/showthread.php?t=1063635](http://ubuntuforums.org/showthread.php?t=1063635)

---

### Post by Kareeser on 2009-03-16
Darn... thought I had him there.

---

### Post by sluger1138 on 2009-03-16
> **KhaosMind said:**
> i been reading about java on 64bits. I installed restricted extras and everything works fine. I dont use java a lot. but i would like to play some games on nintendo8.com and i dont know how. could anyone point me to a guide on how to make java work on firefox 3?

thanks

Through Synaptic you need too enable "icedtea-gcjwebplugin", which should work.Now I just installed Intrepid and get a Unresolved Dependency problem
and have been trying many different tricks to install iced tea, but, all it will let me install is the icedtea6-plugin, which does not work.I will keep poking around in repos to find answer, its not in preferences, or repo http.

If anyone has any ideas, they would be much appreciated

Cheers

Doug

---

### Post by novafluxx on 2009-03-16
Dont use the ones from the repos, they're either old or only 32-bit.

Try the latest Sun Java 6 Update 12, its NOT a beta, and they have a native 64-bit version.

I'd say hold up on OpenJDK and IcedTea until Jaunty, and for now stick with Sun.

---

### Post by Arup on 2009-03-16
The Iced Tea plugin is all x64 and that was the original purpose of it. Also even if you wish to stick to Sun Java, Open Office installs Open JDK by default when you enable the database or Java functionality in it. Java is needed for many of the plugins to work.

---

