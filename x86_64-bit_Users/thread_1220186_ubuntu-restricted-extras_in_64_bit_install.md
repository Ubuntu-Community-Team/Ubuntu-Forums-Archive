---
title: "ubuntu-restricted-extras in 64 bit install"
date: 2009-07-22
forum: x86 64-bit Users
---

### Post by psychobot on 2009-07-22
I apologize if this topic has been covered numerous times. I'm thinking of installing the ubuntu-restricted-extras package from synaptic but I have a 64-bit installation. Is it better to install the 64-bit alpha flash plugin, 64-bit beta Sun Java plugin, and let gstreamer download codecs as I need them? I want to be able to browse the web with the best functionality and play all formats. I already installed the dvd package.

Also, I noticed the package installs the openjdk, icedtea plugin, and sun jre. Are all of these needed? I don't have much experience with Linux but am willing to learn. I understand the terminal and how it works. 

I appreciate any assistance I get

---

### Post by Arup on 2009-07-22
Avoid that, enable medibuntu repos and you will get latest Java 14, for flash download from Adobe site and install latest alpha x64 which works very well with x64. The restricted extras installs x32 plugin with nsplugin wrapper and later on that creates lots of issues.

---

### Post by psychobot on 2009-07-22
thanks for the advice. for some reason i was thinking ubuntu 9.04 came with the medibuntu repo enabled by default. i must've read the message wrong. What files do I need to download to get Java working right? Is this Java 14 from Sun or the OpenJDK? 

THanks

---

### Post by bford16 on 2009-07-22
> **psychobot said:**
> thanks for the advice. for some reason i was thinking ubuntu 9.04 came with the medibuntu repo enabled by default. i must've read the message wrong. What files do I need to download to get Java working right? Is this Java 14 from Sun or the OpenJDK? 

THanksJust go to [[COLOR="Blue"]_http://medibuntu.org/_[/COLOR]]("http://medibuntu.org/") and follow the 'Repository HowTo' instructions.  Then install 'ubuntu-restricted-extras' and anything else you might want.  I recommend 'libdvdcss2' and 'w64codecs,' which are necessary to play some DVDs (libdvdcss2 is not legal in all jurisdictions).  The alpha 64-bit Flash and beta 64-bit Java may be cool, but they also may not work so well.  My opinion: stick with the stuff from Medibuntu and Ubuntu for now.  Wait for the finished products.

---

