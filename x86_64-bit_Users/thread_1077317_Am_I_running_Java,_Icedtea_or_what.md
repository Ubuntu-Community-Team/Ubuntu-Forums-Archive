---
title: "Am I running Java, Icedtea or what?"
date: 2009-02-22
forum: x86 64-bit Users
---

### Post by thadacto on 2009-02-22
I am having problems trying to get into and create a web site in Geocities (free version). I have tried it using Windows XP and Java is causing many problems and I keep getting error logs on my desktop.
So I thought, why not try from Ubuntu (Hardy Heron) (which I much prefer when on the internet, but when I try, I again have a problem that I can't even get Geocities Web Publisher to open and a message pops up that I need Java.

The Java website has check my computer and says
<Your Java version is 1.6.0_0. >  Please click the button below to get the recommended Java for your computer.
Synaptic says I have 3 parts installed:
open-jdk-6-jre
open-jdk-6-jre-headless
open-jdk-6-jre-lib
Also I have the directory usr/lib/jvm/ which has 5 folders

According to my synaptic manager I also have Icedtea installed:
<icedtea-gcjwebplugin> (version 1.0-Oubuntu8)

If I read the messages correctly, I can't use Icedtea with Java

When I look in Firefox under plugins I can't find anything that refers to Java but there is an entry *GCJ Web Browser Plugin (using IcedTea) 1.0*
Sorry this is a bit long-winded but any help would be very much appreciated. Do I need to unstall what I have and start again or is there something I need to do to tell Firefox that Java is installed?

---

### Post by karlr42 on 2009-02-22
You have the horrible free version of Java that comes by default, not the one from Sun(the original developers of Java). 
To install it, open a terminal and:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
Accept the EULA when asked.

---

### Post by thadacto on 2009-02-22
Cheers, karlr42_ that was quick.
I thought it was a long post and going to be more complicated!!!!
Do I need to uninstall / remove all the junk first then?

---

### Post by karlr42 on 2009-02-22
Oh yeah, thanks for reminding me, that only installs the sun version of Java, you need to tell Ubuntu which version to use- 
```
sudo update-alternatives --config java
```
and pick Sun Java- like this:
```
 $  sudo update-alternatives  --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

```

---

### Post by thadacto on 2009-02-22
So I keep everything that is already installed? Yes?

---

### Post by karlr42 on 2009-02-22
It stays installed, but won't be used. Programs that need to run Java just ask Ubuntu for the location of 'java', and Ubuntu will respond with whichever one you chose above, as far as I understand it.
There's no need to uninstall the other versions, they're not hurting anyone.
Now, all this is kind of irrelevant to you, since all you want to do is browse java-enabled websites. Well, that apt-get command I gave you will install the Sun Java plugin for Firefox, so run the command and try geocities again.

---

### Post by thadacto on 2009-02-22
Very many thanks karlr42. I'll give it a try now.

---

### Post by thadacto on 2009-02-22
Couldn't install it. Got the following in terminal:

george@george-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by karlr42 on 2009-02-22
What version of Ubuntu are you running?

---

### Post by thadacto on 2009-02-22
Hardy Heron 8.04 with all the latest updates

---

### Post by karlr42 on 2009-02-22
Hmm, have you read the sticky: [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)
Seems the Java plugin is not available for 64-bit systems.
The solution is to run 32-bit Firefox and the 32-bit plugin. Unfortunatly I've no experience with that, someone on this board will :(

---

### Post by karlr42 on 2009-02-22
Have a read of this:
[http://ubuntuforums.org/showthread.php?t=1019314](http://ubuntuforums.org/showthread.php?t=1019314)

---

### Post by thadacto on 2009-02-22
I've been looking through other posts and found one from sprocket-dk about installing: 
jre-6u12-linux-x64.bin
I'm downloading it at the moment and try to install it.
Thanks karltr42

---

