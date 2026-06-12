---
title: "Ubuntu 8.04 64-bit, firefox2/3, no Java plugin?"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by Pitou on 2008-04-29
Hello,

Because of this bug, [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/212648](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/212648)

I have did remove firefos3 with Synaptic and install firefox2. (I guess it's firefox2 64-bit as well)

But now there is no Java plugin. I guess it's the same for firefox3 also.

Any idea?

Thank you.

Pitou!

---

### Post by Half-Left on 2008-04-29
You need to install the icedtea-gcjwebplugin

---

### Post by Pitou on 2008-04-29
It works, thanks very much!

Pitou!

---

### Post by mivo on 2008-04-29
If you run into Java applets that don't work with OpenSDK/IcedTea, or need javaws (Java Web Start), you can also install a 32-bit browser with the proper plugins. [Kilz's excellent tutorial and automated script]("http://ubuntuforums.org/showthread.php?t=202537") makes this very easy. :)

---

