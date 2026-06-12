---
title: "another java issue on firefox"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by fulgencio on 2008-09-23
Hi I'm using Ubuntu Hardy on a hp amd 64 Turion.
I'm having trouble with java on firefox, when I try to show some 3D images
instead of showing them, the whole area where the image should be turns yellow, and show the message:

[PHP]You do not have Java applets enabled in your web browser, or your browser is blocking this applet.
Check the warning message from your browser and/or enable Java applets in
your web browser preferences, or install the Java Runtime Environment from www.java.com[/PHP]

I haven't followed this instructions because I would like to see if anybody can share some knowledge or prior experience.
One more thing, in the site [www.java.com](www.java.com) I couldn't find any .deb packages, should I install?? using alien for the rpm's or something else????

---

### Post by Bucky Ball on 2008-09-23
Open System->Admin->Synaptic Package manager and do a search for:

**ubuntu-restricted-extras**

If you don't have them installed, install them. :)

Let us know if that fixed the problem.

---

### Post by Thelasko on 2008-09-23
> **fulgencio said:**
> Hi I'm using Ubuntu Hardy on a hp amd 64 Turion.
I'm having trouble with java on firefox, when I try to show some 3D images
instead of showing them, the whole area where the image should be turns yellow, and show the message:

[PHP]You do not have Java applets enabled in your web browser, or your browser is blocking this applet.
Check the warning message from your browser and/or enable Java applets in
your web browser preferences, or install the Java Runtime Environment from www.java.com[/PHP]
Can you provide a link so I know what you are talking about.
> **fulgencio said:**
> 
I haven't followed this instructions because I would like to see if anybody can share some knowledge or prior experience.
Sure, Java has some [issues on 64-bit]("http://ubuntuforums.org/showthread.php?t=774956").  You need to use OpenJDK.  OpenJDK requires the following packages:
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-gcjwebplugin
> **fulgencio said:**
> 
One more thing, in the site [www.java.com](www.java.com) I couldn't find any .deb packages, should I install?? using alien for the rpm's or something else????
No, don't install any packages from Java.com.  [Please read this.]("http://www.psychocats.net/ubuntu/installingsoftware")  Installing the packages from java.com probably won't get you much farther than you have come with the repositories.

If you must have perfectly working Java on your system, I suggest you [install the 32-bit version of Firefox.]("http://ubuntuforums.org/showthread.php?p=1174435")

---

### Post by fulgencio on 2008-09-24
Thanks, for the responces, I installed the package: ubuntu-restricted-extras, and unfortunately it still doesn't work,

I checked and I also have all this installed
> openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-gcjwebplugin


> Can you provide a link so I know what you are talking about.
sure in [https://www.sagenb.org/home/pub/20/]("https://www.sagenb.org/home/pub/20/") In the second example (the Lorentz picture) is the one that gives me trouble...

one last thing when I write in the command line:

~$ update-java-alternatives -l
 I get
[PHP]
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj
[/PHP]

---

### Post by Thelasko on 2008-09-25
Yeah, I forgot to mention, get rid of any Java that's not OpenJDK.  Sometimes that causes problems.

I'll let you know if that site works for me when I get home.

---

### Post by tuxxy on 2008-09-25
What Java are you currently using

```
sudo update-alternatives --config java
```

---

### Post by fulgencio on 2008-09-25
```
:~$ update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-gcj/jre/bin/java
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          4    /usr/lib/jvm/java-6-sun/jre/bin/java
          5    /usr/bin/cacao
          6    /usr/bin/gij-4.1

```

So should I uninstall 1,2,4,6 and keep only 3 and 5 right.

---

### Post by Thelasko on 2008-09-25
> **fulgencio said:**
> ```
:~$ update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-gcj/jre/bin/java
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          4    /usr/lib/jvm/java-6-sun/jre/bin/java
          5    /usr/bin/cacao
          6    /usr/bin/gij-4.1

```

So should I uninstall 1,2,4,6 and keep only 3 and 5 right.
I only have 3 installed.  However, the applet doesn't work for me either (that self signed ssl certificate kinda freaked me out by the way).  If you really need to use this applet, I suggest you install 32-bit Firefox with the 32-bit version of Java.

---

