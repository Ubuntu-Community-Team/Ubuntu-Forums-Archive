---
title: "[SOLVED] Java on 64-bit Systems - not works"
date: 2008-10-15
forum: x86 64-bit Users
---

### Post by peryn on 2008-10-15
I've installed gcjwebplugin + openjdk and applets don't work :(
shows:
starting applet...
and gray box on html page
For example i've used 
[http://www.dgp.toronto.edu/~mjmcguff/learn/java/01-drawingLines/](http://www.dgp.toronto.edu/~mjmcguff/learn/java/01-drawingLines/)

---

### Post by Sef on 2008-10-15
How did you install them?

---

### Post by peryn on 2008-10-15
> **Sef said:**
> How did you install them?

via synaptic

as i read other threads looks like i need to install only openjdk
If i have installed other jvm's - openjdk may not work correctly?

see list of installed jvms:
> 
seth@seth-desktop:~$ update-java-alternatives -l
ia32-java-6-sun 63 /usr/lib/jvm/ia32-java-6-sun
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun


---

### Post by Sef on 2008-10-15
> I've installed gcjwebplugin + openjdk and applets don't work :sad:
shows:
starting applet...
and gray box on html page
For example i've used 
[http://www.dgp.toronto.edu/~mjmcguff...-drawingLines/]("http://www.dgp.toronto.edu/%7Emjmcguff/learn/java/01-drawingLines/")

I've tried with 3 sites that require an applet and all have that same problem.  It's a bug.

---

### Post by peryn on 2008-10-15
> **Sef said:**
> I've tried with 3 sites that require an applet and all have that same problem.  It's a bug.

i thought java on x64 works :(

---

### Post by Thelasko on 2008-10-15
I'll tell you what I tell everybody.

The following packages should be installed for OpenJDK to work.
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-gcjwebplugin

Any other Java packages (GCJ, Sun Java, etc.) may interfere with OpenJDK.

Also, please note that OpenJDK has some bugs at the moment. Namely, the LiveConnect feature doesn't work. If you require perfect execution of Java Applets, please install the [32-bit version of Firefox and Java.]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz")

---

### Post by Thelasko on 2008-10-15
> **peryn said:**
> i thought java on x64 works :(

Java works perfectly, it's the web plugin that has the problem.

---

### Post by Nepherte on 2008-10-15
The applets work for me with openjdk6.

---

### Post by peryn on 2008-10-15
> **Thelasko said:**
> I'll tell you what I tell everybody.

The following packages should be installed for OpenJDK to work.
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-gcjwebplugin

Any other Java packages (GCJ, Sun Java, etc.) may interfere with OpenJDK.

Also, please note that OpenJDK has some bugs at the moment. Namely, the LiveConnect feature doesn't work. If you require perfect execution of Java Applets, please install the [32-bit version of Firefox and Java.]("http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz")

hmm i can't remove other jvm cos i need 32-bit one to use it with Adobe Flex Builder - so looks like there is one exit for me - install 32-bit firefox

---

### Post by Thelasko on 2008-10-15
> **peryn said:**
> hmm i can't remove other jvm cos i need 32-bit one to use it with Adobe Flex Builder - so looks like there is one exit for me - install 32-bit firefox

You might as well, you already have 32-bit Java installed.

---

