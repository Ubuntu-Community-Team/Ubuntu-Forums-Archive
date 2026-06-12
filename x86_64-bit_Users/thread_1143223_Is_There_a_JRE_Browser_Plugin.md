---
title: "Is There a JRE Browser Plugin"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by CarlosinFL on 2009-04-29
I am needing to find a Java JRE browser plugin for my Ubuntu system so I can manage some applications that require Java however I can't find it. I was wondering if anyone knows if this is available for 9.04 x64?

---

### Post by Rog-Mahal on 2009-04-29
there are two options, depending on whether you want open source java with less functionality or official sun java with full functionality. 

FOSS option:

Go to Applications -> Add/Remove and search for OpenJDK (your JRE) and IcedTea (the browser plugin). Check the boxes and install. Start up Firefox and you should be good to go! I use this currently, and I haven't run into too many problems, however some websites will require the most recent java, in which case you'll need:

Sun Java option:

The easiest way I've found is to use the script found in [this post.]("http://http://ubuntuforums.org/showthread.php?t=772490") Just follow the instructions. Kilz was also nice enough to make a script for the flash plugin as well.

Hope that helps!

---

### Post by Kingsley on 2009-04-29
Look up sun-java6-plugin in the repositories.

---

### Post by jespdj on 2009-04-30
> **Rog-Mahal said:**
> The easiest way I've found is to use the script found in [this post.]("http://http://ubuntuforums.org/showthread.php?t=772490") Just follow the instructions. ...
This is out-of-date. Since Ubuntu 9.04, there is a 64-bit Sun Java browser plug-in, and installing it is the same as in 32-bit Ubuntu. Just install the package **sun-java6-plugin**:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by Arup on 2009-04-30
Install sun java from the repos, then open up Java test site with FF [http://www.javatester.org/](http://www.javatester.org/) It will ask for Java plugin on top, click on it and select Sun Java, thats all. Don't install with any other way as that might lead to issues, this method works out best.

---

### Post by Rog-Mahal on 2009-04-30
Cool, I wasn't sure if they included it or not. I've stuck with OpenJDK and IcedTea because it works for me. Sorry for the outdated info. (Someone might want to update the sticky as well.)

---

### Post by Sef on 2009-05-01
Here is a sticky on[ Java for 64-bit]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by jespdj on 2009-05-01
Sef, maybe you should mention in your sticky that you can now just install **sun-java6-plugin**. Java on 64-bit systems is now really exactly the same as on 32-bit systems.

The problem with the missing 64-bit Sun browser plug-in has finally been fixed in Jaunty.

---

### Post by trash on 2009-05-01
anybody know why both of these plugins freeze up Opera but work in Firefox?

---

### Post by jespdj on 2009-05-01
> **trash said:**
> anybody know why both of these plugins freeze up Opera but work in Firefox?
As far as I know, Opera does not use the plugin that you install by installing the package sun-java6-plugin. The plugin is for Firefox, not for Opera.

Opera uses the JRE directly (i.e. what you install with sun-java6-jre), and should not at all be affected by installing the plugin. I don't use Opera, but maybe you should have a look if somewhere in Opera you can specify which Java runtime environment should be used.

---

### Post by trash on 2009-05-01
> **jespdj said:**
> As far as I know, Opera does not use the plugin that you install by installing the package sun-java6-plugin. The plugin is for Firefox, not for Opera.

Opera uses the JRE directly (i.e. what you install with sun-java6-jre), and should not at all be affected by installing the plugin. I don't use Opera, but maybe you should have a look if somewhere in Opera you can specify which Java runtime environment should be used.

Actually Opera detects the right java install not the plugin... freezes up opening a new window 'reparenting into 566...'  everytime regardless which install I choose.

---

### Post by rplantz on 2009-05-04
> **jespdj said:**
> As far as I know, Opera does not use the plugin that you install by installing the package sun-java6-plugin. The plugin is for Firefox, not for Opera.

Opera uses the JRE directly (i.e. what you install with sun-java6-jre), and should not at all be affected by installing the plugin. I don't use Opera, but maybe you should have a look if somewhere in Opera you can specify which Java runtime environment should be used.

This is not the case for me. The Firefox java plugin is libnpjp2.so which is located in
```
/usr/lib64/jvm/java-6-sun-1.6.0.13/jre/lib/amd64
```

Go to Tools -> Preferences -> Advanced -> Content -> Java Options... and set the Java path to that location.

---

