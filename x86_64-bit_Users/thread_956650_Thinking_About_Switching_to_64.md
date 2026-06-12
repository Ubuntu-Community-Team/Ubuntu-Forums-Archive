---
title: "Thinking About Switching to 64"
date: 2008-10-23
forum: x86 64-bit Users
---

### Post by CarlosinFL on 2008-10-23
Next week I would like to switch to 64 bit when 8.10 is officially released. My only reason for doing so is basically to utilize all 8GB of RAM on my work station (yes, I have 8 GB of RAM). Right now my 32 bit 8.04 is limited to 3.2GB's or RAM. That and I have a nice Quad Core CPU. My question is if I decide to load the 64 bit version (desktop edition), will I be able to run Java Run Time applications? On my current 32 bit, I had to install "sun-java6-jre" & "sun-java6-plugin". That is required for a lot of my administrative tasks so can anyone tell me if I will be able to do this with Ubuntu 64?

---

### Post by jespdj on 2008-10-23
Yes, there is 64-bit Sun Java. But there is no 64-bit Sun Java browser plug-in.

You can install OpenJDK Java, which does include a browser plug-in, but unfortunately it doesn't work with all Java applets. You'll need to try out if it works with the applet that you need to use.

To take advantage of your 8 GB RAM, there is one other option. You could install a 32-bit Ubuntu with a kernel with [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension) enabled. The normal 32-bit Ubuntu Desktop does not have this enabled, but 32-bit Ubuntu Server does. You could install Ubuntu Server, and manually install the GUI part of Ubuntu after installing the OS, or install 32-bit Ubuntu Desktop and compile and install a custom kernel (which might not be so easy).

The first thing to try is see if the applet you need to use works with 64-bit OpenJDK Java.

---

### Post by Yellow Pasque on 2008-10-23
You can run a 32-bit browser and 32-bit Java on an x86_64 install (because there's no 64-bit plugin yet). See [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by agathian on 2008-10-23
you might want to checkout the sticky thread - [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

I am running 64-bit in my laptop for couple of weeks now. I was able to get a fair bit of it working, after several permutation and combinations, but it is not 100%. 

BTW, depending on your motherboard's chipset - you may not see the whole memory even with 64-bit. i learnt it the hard way. One of many references on the net on this issue - [http://blogs.msdn.com/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx](http://blogs.msdn.com/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx)

---

