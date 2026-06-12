---
title: "Javarrrrrgh"
date: 2009-01-05
forum: x86 64-bit Users
---

### Post by joey-elijah on 2009-01-05
I've installed Java from the java.com site and followed the tutorial in the getting started post above and installed java 64. However, nothing i install that needs java can find java or i'm being dumb and not knowing how to use java properly.

**Case 1: thingamablog **

Has a [linux version]("http://thingamablog.sourceforge.net/") (albeit in RPM, which i used Alien to convert to a Deb which installed fine. Aside from not showing up in any menu, running 'thingamablog' in terminal gives me: -

joey@ibex:~$ thingamablog
/usr/bin/thingamablog: 3: java: not found

*Grumble*

I also downloaded another blogging application - ['bleezer]("http://larryborsato.com/bleezer/")' which, again, is cross platform. However i unzip to find a lib folder full of .jars and one main .jar. but i have no option of opening them with Java or them automatically knowing to open with java (which i assume i would do?)

any help would be much appreicated, cheers!

---

### Post by stchman on 2009-01-05
> **joey-elijah said:**
> I've installed Java from the java.com site and followed the tutorial in the getting started post above and installed java 64. However, nothing i install that needs java can find java or i'm being dumb and not knowing how to use java properly.

**Case 1: thingamablog **

Has a [linux version]("http://thingamablog.sourceforge.net/") (albeit in RPM, which i used Alien to convert to a Deb which installed fine. Aside from not showing up in any menu, running 'thingamablog' in terminal gives me: -

joey@ibex:~$ thingamablog
/usr/bin/thingamablog: 3: java: not found

*Grumble*

I also downloaded another blogging application - ['bleezer]("http://larryborsato.com/bleezer/")' which, again, is cross platform. However i unzip to find a lib folder full of .jars and one main .jar. but i have no option of opening them with Java or them automatically knowing to open with java (which i assume i would do?)

any help would be much appreicated, cheers!

If you want Java for Intrepid 64 it is in the repositories.

```
sudo apt-get install openjdk-6-jdk icedtea6-plugin
```

That should get you up an running.

---

