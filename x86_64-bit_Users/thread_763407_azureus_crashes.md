---
title: "azureus crashes"
date: 2008-04-23
forum: x86 64-bit Users
---

### Post by Amorget on 2008-04-23
I found an archived post on this, but I think so people can see it I need to create a new post. Anyway, here is the post:

[http://ubuntuforums.org/showthread.php?t=738886&highlight=azureus+x64](http://ubuntuforums.org/showthread.php?t=738886&highlight=azureus+x64)

Does anyone have a fix?  I don't have IcedTea installed and I am running the latest Java 6 JRE

---

### Post by mad_max0204 on 2008-04-23
I've had this problem too. I solved it with uninstalling Iced java and installing sun java 1.6.0. All was done with synaptics. Works as a charm.

Good luck

---

### Post by Amorget on 2008-04-23
> **mad_max0204 said:**
> I've had this problem too. I solved it with uninstalling Iced java and installing sun java 1.6.0. All was done with synaptics. Works as a charm.

Good luck

As far as I can tell I don't have Iced Java installed.

---

### Post by Thorjelly on 2008-04-23
In the console, type

```
sudo apt-get install sun-java6-bin
```

Next type

```
sudo update-alternatives --config java
```

and press the number next to /usr/lib/jvm/java-6-sun/jre/bin/java

See if that works for you. I think that's what I did.

EDIT: Oh, you might have to install sun-java6-jre instead, I'm not sure. Sorry, it's been a while.

---

### Post by Amorget on 2008-04-24
```
sudo apt-get install sun-java6-bin
```

I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manual installed.
The following packages were automatically installed and are no longer required:
  nspluginwrapper libboost-date-time1.34.1 gnash-common libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


```
sudo update-alternatives --config java
```

I get:

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.

```

That leads to:

```
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aaad4280428, pid=5720, tid=1076017488
#

```

When I run Azureus

The JRE is also already installed and the latest...

---

### Post by Spike-X on 2008-04-24
I solved it by installing Deluge and using that instead.

---

### Post by Amorget on 2008-04-24
Installing now :)  We'll see how I like it compared to azurues.

---

