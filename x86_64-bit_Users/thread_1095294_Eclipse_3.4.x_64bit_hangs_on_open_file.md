---
title: "Eclipse 3.4.x 64bit hangs on open file"
date: 2009-03-13
forum: x86 64-bit Users
---

### Post by chu8 on 2009-03-13
Has anyone gotten Eclipse 3.4.x x86_64 to work on 8.10 x86_64

I can install and run Eclipse, but it hangs once I try to open a file. 

I'm using java 1.5 64 bit
java version "1.5.0_17"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_17-b04)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_17-b04, mixed mode)

I tried the xulrunner soln in post
[http://ubuntuforums.org/showthread.php?t=920649&highlight=eclipse](http://ubuntuforums.org/showthread.php?t=920649&highlight=eclipse)
But that does not work, it still hangs 

Eclipse 3.2.2 from the repo. runs fine, but 3.4 has new plugins/features that I would like to use.

Thanks,

---

### Post by blakjack on 2009-03-13
Hi,

Im current using eclipse 3.4 on my ubuntu 8.04 64 bits and it works fine, i made a little configuration, first i bo the update-alternatives stuff then in my home folder i modified .bashrc and i put this lines.

#Java Home
JAVA_HOME=/usr/lib/jvm/java-*
PATH=$JAVA_HOME/bin:$PATH
LD_LIBRARY_PATH=$JAVA_HOME/lib:$LD_LIBRARY_PATH

export JAVA_HOME
export PATH
export LD_LIBRARY_PATH

I put eclipse folder in /usr/share/eclipse34 then in the eclipse.ini i put this lines

-vm
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms128m
-Xmx512m
-XX:MaxPermSize=512m

In eclipse check window --> preference --> java --> Installed Jre and add you java folder there.

If you use compiz should check in workarrounds that you have enable Java Window Fix.

You can try that and log out then log in and check eclipse.
Sorry for my bad english :D

---

### Post by kingtaurus on 2009-03-14
I have eclipse 3.4 running on my desktop. You may need to do the following:
```

sudo update-alternatives --config java

```
and choose a different JVM.

---

### Post by chu8 on 2009-03-16
Thanks for your suggestion but it still hangs when I try to open a file.
cpu usage is 0% 
hard drive is idle.
It just seems to be hanging...waiting for something.
I checked Eclipse versions 3.4, 3.4.1 and 3.4.2 all the same behavior.

Am I missing some libs for 8.10 x86_64?

update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.3
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
*         4    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java


Here is my eclipse.ini:
-startup
plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.101.R34x_v20080731
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vm
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms128m
-Xmx512m
-XX:MaxPermSize=512m


I here is the command from ps -ef:
 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java -Dosgi.requiredJavaVersion=1.5 -Xms128m -Xmx512m -XX:MaxPermSize=512m \
-jar /home/chu/bin/eclipse/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar \
-os linux -ws gtk -arch x86_64 -showsplash \
-launcher /home/chu/bin/eclipse/eclipse \
-name Eclipse \
--launcher.library /home/chu/bin/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.101.R34x_v20080731/eclipse_1115.so \
-startup /home/chu/bin/eclipse/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar \
-exitdata 329800f -vm /usr/lib/jvm/java-1.5.0-sun/jre/bin/java \
-vmargs -Dosgi.requiredJavaVersion=1.5 -Xms128m -Xmx512m -XX:MaxPermSize=512m \
-jar /home/chu/bin/eclipse/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar

Does anyone have the same problem?
Thanks,

---

### Post by kingtaurus on 2009-03-18
Have you tried installing and using openjdk-jre?

---

### Post by chu8 on 2009-03-20
I tried openjdk that did not work but I found my problem, or at least I got it work now.

When I initially downloaded sun-java5-jdk via Synaptic it only marks
sun-java5-bin, sun-java5-jdk and sun-java5-jre.

But now I decided to download all sun-java5 packages:
sun-java5-demo
sun-java5-doc
sun-java5-fonts
sun-java5-source

And now Eclipse 3.4.x works! Wow, I can't believe it.

---

