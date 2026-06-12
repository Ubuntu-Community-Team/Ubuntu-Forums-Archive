---
title: "Eclipse not starting"
date: 2007-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2007-02-27
Hi, I tried to install eclipse on my AMD64 machine, but a very ugly problem showed up in the log, so I tried to download and extract the binary version from the website.

So I donwloaded the 3.2.2 version for AMD64, and installed sun-java6-jdk. I did the update-alternatives and edited the /etc/jvm and /etc/eclipse/java_home to put java 1.6.0 in front of the others.

But while loading, after selecting the workspace, JVM crashes with the following message:

```

JVM terminated. Exit code=127
/usr/lib/jvm/java-6-sun//bin/java
-Xms40m
-Xmx256m
-jar /opt/eclipse/./startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /opt/eclipse/./eclipse
-name Eclipse
-showsplash 600
-exitdata 458011
-vm /usr/lib/jvm/java-6-sun//bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /opt/eclipse/./startup.jar 

```

At the shell it displays this error:

```

/usr/lib/jvm/java-6-sun//bin/java: symbol lookup error: /opt/eclipse/configuration/org.eclipse.osgi/bundles/81/1/.cp/libswt-mozilla-gcc3-gtk-3236.so: undefined symbol: NS_InitEmbedding

```

Has anyone solved this problem?
Please, I need to solve it as soon as possible.

---

### Post by Howler9443 on 2007-02-27
What is your $JAVA_HOME set to?

If you enter 

$java --version

What do you get?

I am just trying to verify that you have the correct version of Java selected.

Also, did you install Eclipse from the repository or did you download it from [www.eclipse.org?](www.eclipse.org?)

---

### Post by rogeriovinhal on 2007-02-27
java -version
```

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)

```

variables:
```

echo "$JAVA_HOME"
/usr/lib/jvm/java-6-sun/
echo "$PATH"
/usr/lib/jvm/java-6-sun//bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

I Downloaded form eclipse.org, it is not the one from the repositories.

---

### Post by Howler9443 on 2007-02-28
Hmm, I'm not sure...

I installed JDK6.0 by enabling the backports repository via Synaptic and then did the install.  I did not have to touch any of the links. IIRC, I didn't need to use update-alternatives either...but my memory fails me on that.

Try to remove JDK 6.0 and pull the one from the backport repository and see if that helps.

---

### Post by rogeriovinhal on 2007-03-01
Actually, the one I am using is from the backports...

---

### Post by phossal on 2007-03-02
I have always found that downloading 32bit Java directly from SUN, and 32bit eclipse directly from eclipse.org, always provided the best performance overall. People do it a lot of ways, but up to about nine months ago there were many complaints about the poor performance of eclipse on Ubuntu. That's when I started the widely read thread on installing java's jdk and eclipse for performance and ease (avoiding the package managers). I spent a couple weeks installing the various packages, and trying all of the combinations of things available at the time from SUN and eclipse. 

Something to consider.

---

### Post by rogeriovinhal on 2007-03-02
I kind of solved it by using the 1.5 java version from the repos... I'll try the downloaded 1.6 and see if it works. I'll edit the post when done.

EDIT:
Same error, now it starts eclipse and after a little time it crashes with that message.

I'll just stick up with 1.5 anyway.

---

### Post by phossal on 2007-03-02
I think you miss understood the point of my comment, but I'm happy you're up and running. Congrats. If, in the future, you decide to try a different method, I would suggest downloading the 32bit JDK and the 32bit eclipse, and installing *both* manually. I recommend the 32bit packages, even on the 64bit platform.

---

### Post by diegoeche on 2007-03-13
I had the same problem but it only appeared when i used the code completion feature of eclipse.

I solve it just by starting eclipse using 

```
java -jar startup.jar
```

 instead of the eclipse executable

---

### Post by iridiumcao on 2007-03-17
> **diegoeche said:**
> I had the same problem but it only appeared when i used the code completion feature of eclipse.

I solve it just by starting eclipse using 

```
java -jar startup.jar
```

 instead of the eclipse executable

Thank you, I did so as you told, and start Eclipse normally.

---

### Post by phossal on 2007-03-18
FYI, there are differences between launching eclipse from the .jar file rather than the script/exe. Ubuntu uses a script, usually, which is used to locate JAVA_HOME, and passes a few options in the command to launch startup.jar. One of the options within the script is typically a memory limit. 

Something to consider.

---

### Post by iridiumcao on 2007-03-18
> **phossal said:**
> FYI, there are differences between launching eclipse from the .jar file rather than the script/exe. Ubuntu uses a script, usually, which is used to locate JAVA_HOME, and passes a few options in the command to launch startup.jar. One of the options within the script is typically a memory limit. 

Something to consider.

good info. need use a script witch contain "java -jar /{eclipse_home}/startup.jar and other constrains such as

 "-Xms40m
-Xmx256m
-jar /opt/eclipse/./startup.jar
-os linux
-ws gtk"

and etc. ?

It throws OutOfMemoryException sometimes now, so I think Eclipse need launch with parameters.

---

### Post by cmoad on 2007-03-18
I was experiencing the original issue posted and after googling around I found that "MOZILLA_FIVE_HOME" needs to be set in your environment.  Does anyone know package out there that might set this by default?

export MOZILLA_FIVE_HOME=/usr/lib/mozilla
/usr/local/eclipse/eclipse

---

### Post by macross3003 on 2007-04-03
same problem here using feisty and eclipse 3.2.2
exporting MOZILLA_FILE_HOME doesn't works :(

googling around i found this thread alerting that NS_InitEmbedding is not anymore in the libraries [http://www.mail-archive.com/pkg-java-maintainers@lists.alioth.debian.org/msg04502.html](http://www.mail-archive.com/pkg-java-maintainers@lists.alioth.debian.org/msg04502.html) :S

---

### Post by phossal on 2007-04-03
Did you install eclipse and Java as packages, or directly from their respective sites?

---

### Post by macross3003 on 2007-04-03
java as package (sun-java6-jdk) and eclipse from the site...

a rare thing is that the error appears when i try to create a new workspace and if i copy the .metadata folder from an existing one, eclipse starts without any trouble...

at this point i don't know if it's some ubuntu or eclipse.org problem...

---

### Post by kbogert on 2007-04-10
Fixed for me:

jvm 1.6 amd64 (downloaded from sun)
Eclipse 3.2.2 amd64 (downloaded from eclipse)

I had to do  **export MOZILLA_FIVE_HOME=/usr/bin/mozilla**
(that is not a typo)

I put this in a script before running eclipse.  Found the answer here:
[http://www.centos.org/modules/newbb/viewtopic.php?topic_id=7162](http://www.centos.org/modules/newbb/viewtopic.php?topic_id=7162)

---

### Post by adielkhan on 2007-04-20
Try setenv MOZILLA_FIVE_HOME ""

see [https://eclipse.org/bugs/show_bug.cgi?id=174642](https://eclipse.org/bugs/show_bug.cgi?id=174642)

thanks
Adiel.

---

### Post by jespdj on 2007-04-24
Note: This is indeed a bug in Eclipse 3.2.2. See this bug report: [https://eclipse.org/bugs/show_bug.cgi?id=174547](https://eclipse.org/bugs/show_bug.cgi?id=174547)

Also look carefully at the comments in the bug report, Grant Gayed has added an attachment in one of the comments that fixes this bug for Eclipse 3.2.2.

---

### Post by phossal on 2007-04-24
Why not just download eclipse and Java manually?

---

### Post by jespdj on 2007-04-25
> **phossal said:**
> Why not just download eclipse and Java manually?
Because that does not fix the problem... #-o It is a bug in Eclipse 3.2.2, and it doesn't matter if you use Eclipse 3.2.2 from the Ubuntu repository or if you download and install it manually.

Look at this Eclipse bug report: [https://bugs.eclipse.org/bugs/show_bug.cgi?id=174547](https://bugs.eclipse.org/bugs/show_bug.cgi?id=174547)
There is an attachment in the bug report which fixes the problem.

Download it (it is a JAR file) and put it in your Eclipse plugins directory. Make sure to delete the old version of the JAR from the plugins directory.

---

### Post by phossal on 2007-04-25
Perhaps it works because I use the 32bit versions. I don't have any troubles though. No bug, mate. I've been running the 32bit JDK and Eclipse for months, and it worked just fine when I updated to 6. However, I do find your face icon entertaining, if not indicative of the type of person who's married to packages.

---

### Post by lapsu on 2008-03-28
> **diegoeche said:**
> I had the same problem but it only appeared when i used the code completion feature of eclipse.

I solve it just by starting eclipse using 

```
java -jar startup.jar
```

 instead of the eclipse executable

Hah, that also worked for me.  Java and eclipse rules. Good tip!

---

