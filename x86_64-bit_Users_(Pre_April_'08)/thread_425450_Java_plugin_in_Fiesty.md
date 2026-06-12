---
title: "Java plugin in Fiesty"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by r_rehashed on 2007-04-27
I installed Java 6 JDK from the Multiverse repos. and made a symbolic link to,

           /usr/lib/jvm/ia32-java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so

in,      /usr/lib/firefox/pugins/

I thought this worked but, Firefox still gives a `plug-in not installed' message.
Any clues?

I am using 64-bit Firefox. Kilz's tutorial for 32-bit seems to be the next thing if nothing works out.

---

### Post by Tanker Bob on 2007-04-27
> **r_rehashed said:**
> I installed Java 6 JDK from the Multiverse repos. and made a symbolic link to,

           /usr/lib/jvm/ia32-java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so

in,      /usr/lib/firefox/pugins/

I thought this worked but, Firefox still gives a `plug-in not installed' message.
Any clues?

I am using 64-bit Firefox. Kilz's tutorial for 32-bit seems to be the next thing if nothing works out.

For Java support in 64-bit Kubuntu, I installed Blackdown J2SE from the 64-bit repositories.  It works fine in 64-bit Firefox.

---

### Post by flossgeek on 2007-04-27
Realised you have said 64 bit after reading. However if you do install 32 bit version of Ubuntu do the following below.


**Installing Java 6**

If you want the plugin for mozilla and the java runtime, then you would do the following in a terminal:-

```
sudo apt-get update
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

If you want the jdk(for writing java and contains jre) do this:-

```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

Once you have done either of these run:-

```
sudo update-java-alternatives -s java-6-sun
```

Finally open the jvm config file:-

```
gksudo gedit /etc/jvm
```

arrange lines in following order:-

/usr/lib/jvm/java-1.6.0-sun
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr

Save and exit. Thats Java setup! ;-)

---

### Post by r_rehashed on 2007-04-30
Thanks guys. :)

Silly of me to not have mentioned i am using 64-bit Feisty.

I have the 32-bit version of Sun's Java 6 JRE installed too alongside the 64-bit version.

will it work if i download the sun-java6-plugin .deb file and install it? I have ia-32 libs installed.

I shall be using Java to code too and so do not want to install Blackdown's Runtime just to get applets to display.

Thank you again

---

### Post by Tanker Bob on 2007-04-30
I found out last night that there is a 64-bit version of Sun Java 6 in the Feisty repositories.  It is installed as part of a "restricted" package.  I'll look up the name when I get home.  It doesn't have a Mozilla plug-in, though, as best I can tell.  The Blackdown Java provided that.

---

### Post by CapPicard on 2007-04-30
Blackdown's JRE causes my 64-bit firefox to freeze up to the point I have to kill it.

I'm currently resorting to 32-bit firefox...

I would like to have 64-bit java working, but I guess that would have to wait.

---

### Post by Tanker Bob on 2007-04-30
In the x86-64 Feisty non-free repository, the Sun packages are sun-java6-bin and sun-java6-jre.  However, I don't see a Sun Java6 browser plug-in for in any of these repositories.

---

### Post by Mr_bleu on 2007-04-30
**[SIZE="3"]There isn't any.  I used a combination of pinguin and killz' coding to get mine working.  Java and flash.[/SIZE]**

---

