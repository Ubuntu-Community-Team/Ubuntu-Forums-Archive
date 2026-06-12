---
title: "eclipse 3.3 crashes"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by plinkputty on 2008-10-03
Hello,

I've tried a variety of the different proposed solutions on the ubuntu forum but my eclipse 3.3 always seems to crash after about 2 minutes of using it.  I'm running it from the Menu, which is a "Custom Application Launcher" with the following command:

/usr/bin/eclipse-3.3


The error I get is:

JVM terminated. Exit code=1
/usr/lib/jvm/java-6-sun//bin/java
-Xms256m
-Xmx1024m
-jar /usr/lib/eclipse-3.3/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-os linux
-ws gtk
-arch x86_64
-showsplash
-launcher /usr/lib/eclipse-3.3/eclipse
-name Eclipse
--launcher.library /usr/lib/eclipse-3.3/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.2.R331_v20071019/eclipse_1021.so
-startup /usr/lib/eclipse-3.3/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-exitdata 880035
-install /usr/lib/eclipse-3.3
-vm /usr/lib/jvm/java-6-sun//bin/java
-vmargs
-Xms256m
-Xmx1024m
-jar /usr/lib/eclipse-3.3/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar 

Any ideas would be greatly appreciated.

Thanks.

---

### Post by jespdj on 2008-10-03
You are already using the right version of Java (Sun Java 6), so that's not the problem.

The first thing you could try is starting Eclipse with the "-clean" option:
```
eclipse -clean
```

If that doesn't help, you could try deleting your Eclipse configuration directory:
```
rm -rf ~/.eclipse
```
(Note, this will delete all your settings and also updates that you downloaded from within the Eclipse update manager).

---

### Post by plinkputty on 2008-10-04
I used -clean as per your suggestion in my "Application Launcher" but that didn't seem to work.  I ended up changing the version of java to 1.5.0 and that works.  Is this a known issue?

The version of eclipse I'm using is: Version: 3.3.1.1

---

### Post by mmore on 2009-04-13
i have eclipse 3.4. the eclipse crashes in many ways , some times when compiling the code , note that i am using eclipse just for python programs not JAVA , another times it crashes with itself, and gives log of :

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 2f002b
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar   


i tried to downgrade the JRE from Java 6 to Java 5 , but with no help

---

### Post by jespdj on 2009-04-13
Hello mmore, I remember that you've asked a question about this before.

It looks like you're still using GNU Java, and not Sun Java 5 or 6. I can see that from lines like this one:
```
/usr/lib/jvm/java-gcj/bin/java
```
Note the "gcj" in there. That indicates that you're using GNU Java, not Sun Java. Eclipse does not run well with GNU Java (you don't want GNU Java, it's, slow, incomplete and obsolete).

You need to install Sun Java 6, and then make Sun Java 6 the default version of Java that's used on your system:
```
sudo apt-get install sun-java6-jre
sudo update-java-alternatives -s java-6-sun
```
See [this page](https://help.ubuntu.com/community/Java) for more information about Java on Ubuntu.

Instead of "java-gcj" you should see something like "java-6-sun" in the Eclipse information; if you don't, then you're not using Sun Java 6 to run Eclipse.

You might try uninstalling GNU Java:
```
sudo apt-get remove gcj gij
```

---

### Post by mmore on 2009-04-14
i got a message that the switching between two JAVA did work well


$sudo update-java-alternatives -s java-6-sun

No alternatives for firefox-3.0-javaplugin.so.
No alternatives for HtmlConverter.
No alternatives for java-rmi.cgi.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so'.

---

### Post by mmore on 2009-04-15
hi jespdj, 


i tried today after install Sun Java , with 


sudo apt-get install sun-java6-jre

then ensure that i have the alternatives through :

sudo update-java-alternatives --list

 then open the eclipse configuration file 

gedit /etc/eclipse/java_home

and then make sure that  sun Java before java-gcj , as the following:

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj 


then eclipse will use it and working correctly 

for more information please refer to this Article 

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by jespdj on 2009-04-15
Good to hear that you've solved the problem! :KS And thanks for posting back, so that people who have the same kind of problem and who find this thread will have some information to work with.

---

