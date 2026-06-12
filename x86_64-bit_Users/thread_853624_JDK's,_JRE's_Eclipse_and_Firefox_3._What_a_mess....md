---
title: "JDK's, JRE's Eclipse and Firefox 3. What a mess......"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by moonshinerat on 2008-07-08
Hi guys,

I'm having a real bad day.

I'm running Ubuntu and Kubuntu 8.04.1 64bit. I had the icedtea plugin working with Firefox 3, but then it became necessary to install Eclipse and a JDK too.

Now, installing the OpenJDK wasn't a problem, but then Eclipse couldn't find it. I tried the Sun JDK, both the Ubuntu package and the binary from Sun's website. Both made a mess of my IcedTea plugin for some reason.

I currently have the binary installed from Sun but my system can't find it.

[HTML]javac -version[/HTML] just gives me a command not found.

I tried to follow instructions with some kind of script from these forums to install 32bit Firefox 3, but the script breaks half way through with a missing symbol alert.

What is the best thing to do here? I can't wipe off my systems and use 32bit distros, but I need Firefox 3, a working JDK and a working JRE. Do I use the Sun ones or the OpenJDKstuff? Binaries or 'buntu packages? Do I use 64bit JDK with a 32bit JRE and Firefox 32bit or go 64bit all the way through? Can I combine Sun JDK's with OpenJDK's JRE and the IcedTea Plugin? How can I get Firefox 3 32bit installed on these systems?

Sorry for so many questions. Thanks folks.

---

### Post by stchman on 2008-07-08
> **moonshinerat said:**
> Hi guys,

I'm having a real bad day.

I'm running Ubuntu and Kubuntu 8.04.1 64bit. I had the icedtea plugin working with Firefox 3, but then it became necessary to install Eclipse and a JDK too.

Now, installing the OpenJDK wasn't a problem, but then Eclipse couldn't find it. I tried the Sun JDK, both the Ubuntu package and the binary from Sun's website. Both made a mess of my IcedTea plugin for some reason.

I currently have the binary installed from Sun but my system can't find it.

[HTML]javac -version[/HTML] just gives me a command not found.

I tried to follow instructions with some kind of script from these forums to install 32bit Firefox 3, but the script breaks half way through with a missing symbol alert.

What is the best thing to do here? I can't wipe off my systems and use 32bit distros, but I need Firefox 3, a working JDK and a working JRE. Do I use the Sun ones or the OpenJDKstuff? Binaries or 'buntu packages? Do I use 64bit JDK with a 32bit JRE and Firefox 32bit or go 64bit all the way through? Can I combine Sun JDK's with OpenJDK's JRE and the IcedTea Plugin? How can I get Firefox 3 32bit installed on these systems?

Sorry for so many questions. Thanks folks.

Looks like Eclipse is compatible with OpenJDK and SUN Java.

You can install SUN Java 1.6 in 64 bit but you will have no browser plugin.  Try installing these.

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

This might work.  Uninstall the SUN Java stuff first.

---

### Post by HotCupOfJava on 2008-07-08
Yes, IcedTea has its own JDK and JRE - they SHOULD play nice with your plugin (seeing how they are from the same group). You might have an easier time making the necessary changes with the Synaptic Package Manager, too. Unless you just want to use the command-line sudo apt etc for the experience.

---

### Post by pablosanchezuy on 2008-07-08
I use eclipse (3.2 and 3.3) with openjdk, also with docs . 
See, [http://ubuntuforums.org/showthread.php?t=851678](http://ubuntuforums.org/showthread.php?t=851678) .

Instead of using supplied eclipse with ubuntu, i just downloaded from eclipse.org, uncompress and run .

Regards.

Pablo .

---

### Post by KhipuX on 2008-07-09
You shouldn't have any problems with OpenJDK compatibility, I would personally avoid the direct Sun stuff.

If you install the OpenJDK JDK from the Ubuntu Repos it will install the JRE at the same time. Then, install the plugin (not the transitional one) and Java should work; no symlinks or anything. There are a handful of sites that don't like the IcedTea plugin (some banks etc) but you don't need the 32bit Firefox either.

I have found that with 8.04.1 that the non-free flash plugin works with Firefox 3 straight off as well.

Sorry, just remembered, in my opinion it's easier to install Eclipse from the spource at their own website as well. I tried several times with the Ubuntu package and never got it to work.

---

### Post by KhipuX on 2008-07-09
.... that would be source, not spource ....

---

### Post by Yellow Pasque on 2008-07-09
Try the following command. It allows you to choose which installed version of java to use:
```
dan@harvest:/dev$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

```

EDIT: I believe you were looking for this command:
```
dan@harvest:/dev$ sudo java -version
java version "1.6.0"
OpenJDK  Runtime Environment (build 1.6.0-b10)
OpenJDK 64-Bit Server VM (build 1.6.0-b10, mixed mode)

```

---

