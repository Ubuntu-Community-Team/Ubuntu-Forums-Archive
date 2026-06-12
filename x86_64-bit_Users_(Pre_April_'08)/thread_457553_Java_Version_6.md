---
title: "Java Version 6"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ry60003333 on 2007-05-28
I'm trying to install Java Version 6 into Firefox on Ubuntu, but in the jre6.0.0_01 folder, there is no plugin folder! How do I make a link to the java plugin when it doesn't exist? :(

---

### Post by Blender on 2007-05-28
I don't think there's a 64-bit plugin, but I may be wrong.

You could try with **nspluginwrapper** and **ia32-sun-java6-bin**.

---

### Post by Kilz on 2007-05-28
> **Blender said:**
> I don't think there's a 64-bit plugin, but I may be wrong.

You could try with **nspluginwrapper** and **ia32-sun-java6-bin**.

You are correct, these is no java 6 pluguin for the 64bit browser.[ There is an old blackdown one]("ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/JDK-1.4.2/amd64/03/") (jre 1.4) that crashes the browser when loading applets. 
No, you cant use nspluginwrapper, it does not support java plugins, only Flash and mplayer. 
No you cant use ia32-sun-java6-bin as it contains a 32bit java/plugin that wont work with the 64bit browser.

---

### Post by kleeman on 2007-05-29
I use the GCJ Web Browser Plugin 0.92 in a 64 bit browser and it works fine for simple applets (eg dslr speedtest). To install do this:

sudo apt-get install gcjwebplugin-4.1
sudo cp /usr/lib/gcj-4.1/libgcjwebplugin.so /usr/lib/mozilla/plugins/

---

