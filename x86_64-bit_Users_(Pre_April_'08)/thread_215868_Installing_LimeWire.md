---
title: "Installing LimeWire?"
date: 2006-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chaoswarrior100 on 2006-07-14
I need help installing LimeWire. I unpacked everything but when I trying and run the runLime.sh file I get this error.


Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

but when I try and update with apt-get for jre it says I already have it up to date.

---

### Post by bigken on 2006-07-14
[LEFT]delete double post 
[/LEFT]

---

### Post by bigken on 2006-07-14
[LEFT]you could use automatix to install jre    [http://www.ubuntuforums.org/showthread.php?t=177646&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=177646&highlight=automatix)[/LEFT]

---

### Post by Jedeye on 2006-07-14
yeah Automatix makes it easy to install JRE. If you do try automatix you should give frostwire a whirl

---

### Post by Kilz on 2006-07-14
> **Jedeye said:**
> yeah Automatix makes it easy to install JRE. If you do try automatix you should give frostwire a whirl

Automatrix can cause problems in the amd 64bit version. Adding java is so easy, as is frostwire. Why bother to install an application like automatrix, to install 2 other applications?

```
sudo apt-get install j2er1.4 
```

[URL="http://www.frostwire.com/"]
Go here[/URL] or [Click here to download Frostwire]("http://www.frostwire.com/download.php?file=http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb") 
Save the file to your desktop.
Open a terminal and copy/paste in the following two lines.
```
cd ~/Desktop
sudo dpkg --force-architecture -i FrostWire-4.10.9-2.i586.deb
```

---

### Post by weird_c00kie on 2006-10-13
i downloaded frostwire and installed it using the force-architecture command line you provided, but it won't run :(

i'm pretty sure i've installed java already, but just to make sure i tried *sudo apt-get install j2er1.4 *, but it doesn't work
comes up with
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package j2er1.4


---

### Post by weird_c00kie on 2006-10-13
nevermind. i found it through senaptic :)

j2re1.4

frostwire works now :D

---

### Post by sdude on 2006-12-09
> **weird_c00kie said:**
> i downloaded frostwire and installed it using the force-architecture command line you provided, but it won't run :(

i'm pretty sure i've installed java already, but just to make sure i tried *sudo apt-get install j2er1.4 *, but it doesn't work
comes up with

same :(

---

