---
title: "Java64"
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by Joshmotron on 2009-01-08
I know there are only about 15 million of these posts, but I've spent the last 3 hours trying everything under the sun to get this to work any nothing seems to be happening. (Anything in Bold is a command)

Process:
Downloaded the 64 bit Firefox, installed it, lives under ~/Firefox for me.  There's a ~/.mozilla/plugins directory to where I have libflashplayer.so and it's being seen and working no problems at all.

Downloaded the newest Java update, **jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin**, I installed this, lives in **/usr/lib/jvm/jre1.6.0_12** (like a lot of examples have them... it's either there or /opt/jre1.6.0_12).  Had the **sun-java6-jre** installed first cause it didn't seem to recognize the .bin install at all.  "Officially" installed it as a version of java.
```

**update-alternatives --list java**
/usr/lib/jvm/java-6-sun/jre/bin/java
/usr/lib/jvm/jre1.6.0_12/bin/java
```

I ran -config java to set the bottom one (newest update) as my default.
```

**java -version**
java version "1.6.0_12-ea"
Java(TM) SE Runtime Environment (build 1.6.0_12-ea-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.2-b01, mixed mode)
```

Also, just for an extra check!
```
**ls /usr/bin/java**
/usr/bin/java -> /etc/alternatives/java

**ls /etc/alternatives/java**
/etc/alternatives/java -> /usr/lib/jvm/jre1.6.0_12/bin/java
```

My .mozilla/plugins directory:
```
**ls**
libflashplayer.so
libnpjp2.so -> /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so
```

(I even removed the link and just copied it over)
Nothing at all seems to get this thing close to even wanting to work, and for whatever reason, in my **about:plugins** file...
```
    File name: /home/joshmotron/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 10.0 r15
```

Flash shows up perfectly!  But even though it's in the same directory, NO FREAKIN JAVA!

There have also been examples where a person changes their **about:config** file where
**java.default_java_location_others** is changed to say **/usr/lib/jvm/jre1.6.0_12** and
**java.java_plugin_library_name** is set to **libnpjp2**

At this point I'm completely at a loss on what to do.

---

### Post by tuxxy on 2009-01-08
Flash and Java are both provided in the ubuntu-restricted-extras package, this package provides flash, java, codecs etc and will install for you automaticallty

To install it open terminal and run

```
sudo apt-get install ubuntu-restricted-extras
```I noticed your running 64-bit Ubuntu? if so once you have installed the package above it would be a good idea to manually remove the flashplugin-nonfree that comes with the package and install the latest alpha 64-bit native flash plugin, see my thread for information on how to do that.

[http://ubuntuforums.org/showthread.php?t=999313](http://ubuntuforums.org/showthread.php?t=999313)

---

### Post by Joshmotron on 2009-01-08
```
joshmotron@joshmotron:~$ sudo apt-get install kubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

That was one of the first things I did when I install Kubuntu, but the thing is, I never installed Firefox using sudo apt-get install, I just went to their website and got the firefox-3.0.5.tar.bz2 file, extracted and just tossed it in my home directory, since my first time installing the 64 bit Kubuntu didn't go so smoothly and using the package was not at all "fully functioning" with my system (graphics kinda wonky, just didn't seem to work like it should, etc... probably cause the package is 32 bit??).  This tarball installed directly from their website though seems to do the trick much better.

---

### Post by Thelasko on 2009-01-09
[QUOTE=Joshmotron]I never installed Firefox using sudo apt-get install, I just went to their website and got the firefox-3.0.5.tar.bz2 file, extracted and just tossed it in my home directory[/QUOTE]
Don't do that.  [You need to read this.]("http://www.psychocats.net/ubuntu/installingsoftware")

I had originally posted something else, but I read the above quote and deleted it.

---

### Post by tuxxy on 2009-01-09
I agree Firefox should be included as the default browser in GNOME anyway and no the package you get is not 32-bit.

---

### Post by Joshmotron on 2009-01-09
Turns out I hate Linux.  I swear the last time I tried this, I downloaded Firefox through package manager, it was completely messed up, and almost nothing worked, now, it recognizes that new Java package, has no appearance problems whatsoever, and runs fine.

---

### Post by Thelasko on 2009-01-10
> **Joshmotron said:**
> Turns out I hate Linux.  I swear the last time I tried this, I downloaded Firefox through package manager, it was completely messed up, and almost nothing worked, now, it recognizes that new Java package, has no appearance problems whatsoever, and runs fine.

Sounds like a weird glitch or something.  Don't write off Linux/Ubuntu because of it.

Did you install any other software from tarball?

---

