---
title: "Java update?"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by acidblue on 2008-10-18
Hi there!
Unbuntu 8.04TLS
Java:java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

Recently updated my system and noticed a Java update, (which i cancelled).
Is it ok to update this?
I installed Java using a script i found here on these forums,
forget the name.
Just want to be sure before i do it.

---

### Post by GSF1200S on 2008-10-18
> **acidblue said:**
> Hi there!
Unbuntu 8.04TLS
Java:java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

Recently updated my system and noticed a Java update, (which i cancelled).
Is it ok to update this?
I installed Java using a script i found here on these forums,
forget the name.
Just want to be sure before i do it.

Hmm.. I dont know since you used a script. I dont know what the script did/does. What do you use for a web browser plugin? Do you just use a 32bit browser, a 64bit browser w/o java, or a 64bit browser with the IcedTea java jre/plugin?

I would make sure apt shows java installed and for that matter what version/s is/are installed and go from there. If the script did it all through apt vs. compiling, you should be fine to update/upgrade.

Check whether or not you have IcedTea installed, and do

```
about:plugins
```

in firefox to see whether the plugin is working...

---

### Post by jespdj on 2008-10-20
Yes, it is OK to update this. If it is in the normal Ubuntu repository, you can normally always count on it that it's OK to update it. There was recently an update for Sun Java version 1.6.0_07.

Why did you install Java using some script, instead of installing it the normal way from the repository?

Since you got an automatic update message, the script most likely installed Java from the repository the normal way.

---

### Post by acidblue on 2008-10-23
Just wanted you to know Your all wrong.
I updated java and now it dosn't work.
This is what I have now:
kaffe VM "1.1.8"

Copyright (c) 1996-2007 Kaffe.org project contributors (please see
  the source code for a full list of contributors).  All rights reserved.
Portions Copyright (c) 1996-2002 Transvirtual Technologies, Inc.

The Kaffe virtual machine is free software, licensed under the terms of
the GNU General Public License.  Kaffe.org is a an independent, free software
community project, not directly affiliated with Transvirtual Technologies,
Inc.  Kaffe is a Trademark of Transvirtual Technologies, Inc.  Kaffe comes
with ABSOLUTELY NO WARRANTY.

Engine: Interpreter   Version: 1.1.8   Java Version: 1.4
Heap defaults: minimum size: 5 MB, maximum size: unlimited

When ever i go to a website with java I get the "install missing plugin".
I'm going to uninstall this and go back to the first one i had.
Thats if i can, I know you can run multiple versions of java, just
can't remember how to do that.

---

### Post by jespdj on 2008-10-24
I don't know what you did, but you're now using some strange and ancient Java version.

Use the following command to select the default Java that you want to use on your system:
```
sudo update-alternatives --config java
```

Note that there is no Java browser plug-in included with 64-bit Sun Java 6. If you want to be able to run Java applets in your browser, use OpenJDK Java. It includes a plug-in, but unfortunately not all applets work with it. So you have to check if the applets you need work with OpenJDK.

If the OpenJDK plug-in doesn't work for you, you could install 32-bit Sun Java 6 and a 32-bit browser. See [this thread](http://ubuntuforums.org/showthread.php?t=956650) for more information.

---

### Post by Nepherte on 2008-10-24
> **acidblue said:**
> Just wanted you to know Your all wrong.
I updated java and now it dosn't work.

As long as we don't know this script you know, people can not always give advise that works 100%.

I *assume* the script you were using installed a 32bit browser and all the 32bit plugins such as flash and java. Otherwise it wouldn't be smart to use a script since every other scenario can be done as usual through synaptic.

---

