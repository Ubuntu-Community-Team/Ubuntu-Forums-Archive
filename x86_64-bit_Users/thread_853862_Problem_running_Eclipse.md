---
title: "Problem running Eclipse"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by chetan.89 on 2008-07-08
Hi !

I use Ubuntu 7.10 Gutsy Gibbon (64-bit version) and have some troubles running Eclipse under it. I get the following error msg.

> 
JVM terminated. Exit code=1
/usr/lib/j2se/1.4/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 718025
-install /usr/lib/eclipse
-vm /usr/lib/j2se/1.4/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar


I saw many other posts relating to the same problem but couldn't resolve. Please help me out.

Thank you very much !
Chetan.

---

### Post by heffaklump90 on 2008-07-10
I have the same problem, in two different configurations of eclipse. One is used for PHP with PDT installed, and the other one is for ruby and ror with Aptana installed. Most of the crashes disappear if you uncheck the "Project -> Build Automatically" feature, as well as comment out the build command in the .project file in your workspace.

This greatly reduces the powers of eclipse with regards to autocompletion et.c. but it allows it to run at least moderately good.

I recommend trying out older eclipse versions as well.

---

### Post by ibutho on 2008-07-10
Try using sun java as the default java instead of gcj or icedtea.

---

### Post by heffaklump90 on 2008-07-10
The solution seems to be using sun-java-5 as described in the following thread: [http://ubuntuforums.org/showthread.php?t=850606](http://ubuntuforums.org/showthread.php?t=850606)

For me it works simply with installing java-5 and do a ```
sudo update-alternatives --config java

```
and select java-5 as the java solution.

---

### Post by hodge24 on 2008-07-10
Hi,

I wrote an article on how to set up Eclipse 64 bit, with PDT, WST and MySQL Explorer plugins - [http://www.64bitjungle.com/tech/64-bit-eclipse-linux-installation-including-pdt-wtp-wst-atf-and-mysql-sql-explorer-plugin/](http://www.64bitjungle.com/tech/64-bit-eclipse-linux-installation-including-pdt-wtp-wst-atf-and-mysql-sql-explorer-plugin/), which includes setting up the latest Sun JRE.

When I get some time, I'll convert it to a HowTo and post it to the forums.

Hope it helps.

---

