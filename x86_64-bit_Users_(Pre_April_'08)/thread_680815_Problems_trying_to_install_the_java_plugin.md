---
title: "Problems trying to install the java plugin"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by mitsugiri on 2008-01-28
I'm trying to get java to work on Firefox but I can't seem to install the Java6 plugin.

When I try to install using sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

I get the following message.
..............
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
.............

What could be the problem?  I have checked my repositories under the synaptic package manager and everything is checked except the cd.  What am I missing here?

Please help.

---

### Post by Kilz on 2008-01-28
> **mitsugiri said:**
> I'm trying to get java to work on Firefox but I can't seem to install the Java6 plugin.

When I try to install using sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

I get the following message.
..............
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
.............

What could be the problem?  I have checked my repositories under the synaptic package manager and everything is checked except the cd.  What am I missing here?

Please help.

The problem is that there is no 64bit version of the sun java 6 plugin. You can try icedtea, it is open source and has a open source 64bit java plugin, but it doesnt work for all sites.

---

### Post by mitsugiri on 2008-01-28
> **Kilz said:**
> The problem is that there is no 64bit version of the sun java 6 plugin. You can try icedtea, it is open source and has a open source 64bit java plugin, but it doesnt work for all sites.


That clarifies things a bit.  Thanks Kilz!

---

