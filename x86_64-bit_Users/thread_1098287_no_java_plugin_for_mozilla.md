---
title: "no java plugin for mozilla"
date: 2009-03-16
forum: x86 64-bit Users
---

### Post by bigheart on 2009-03-16
hello,
i installed openjdk 6 and sun java 6 in my 64bit ubuntu from apt however i can't find the libnpjp2.so in niether of their amd64 directories.

i search in internet and it seems that the current sun JRE package didn't included this plugin, is that true?

for the openjdk, i found in some forum, they suggest to remove icedtea so openjdk 6 has a plugin itself? but why i can't find this plugin in openjdk 6?

by the way, i have a laptop using 32bit system, the installation is much more easier.

Joseph

---

### Post by cariboo on 2009-03-17
Use the script I have attached to install the 64-bit java plugin. I can't seem to find the thread I got it from at the moment, but it works well.

Jim

---

### Post by jocko on 2009-03-17
> **cariboo907 said:**
> Use the script I have attached to install the 64-bit java plugin. [COLOR=Red]I can't seem to find the thread I got it from at the moment[/COLOR], but it works well.

Jim
Look at the stickies in this section of the forum. [This one explains it all]("http://ubuntuforums.org/showthread.php?t=772490").

---

### Post by Yellow Pasque on 2009-03-17
Ubuntu 9.04 (officially released next month) has a sun-java6-plugin package in the repos, so this won't be a problem for most users for much longer.

---

### Post by jespdj on 2009-03-17
> **jocko said:**
> Look at the stickies in this section of the forum. [This one explains it all]("http://ubuntuforums.org/showthread.php?t=772490").
Unfortunately the sticky is not up-to-date. Sun has released a 64-bit Java plug-in a while ago (it is not beta anymore as the sticky says).

There are several howto's in the forum. Look at this one, for example:
[http://ubuntuforums.org/showthread.php?t=1063635](http://ubuntuforums.org/showthread.php?t=1063635)

---

### Post by SketchyClown on 2009-03-17
> **cariboo907 said:**
> Use the script I have attached to install the 64-bit java plugin. I can't seem to find the thread I got it from at the moment, but it works well.

Jim

Jim,

That's a great script and I cannot remember which thread I got it from either. I recently modified it so it will grab the newest March '09 64-bit plugin.

Here is the updated script for auto-installation of 64-bit Java.

---

### Post by jocko on 2009-03-17
> **jespdj said:**
> Unfortunately the sticky is not up-to-date. Sun has released a 64-bit Java plug-in a while ago (it is not beta anymore as the sticky says).

There are several howto's in the forum. Look at this one, for example:
[http://ubuntuforums.org/showthread.php?t=1063635](http://ubuntuforums.org/showthread.php?t=1063635)

You are correct, but I replied to cariboo907's statement that he did not remember where he got the script. It is the exact same script as the one in the sticky, and it downloads and installs the beta version released in december.

---

### Post by zika on 2009-03-17
You might want to try what was checked several times by several users:[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59).
in JJ it is, now, much easier.

---

### Post by jespdj on 2009-03-17
> **jocko said:**
> You are correct, but I replied to cariboo907's statement that he did not remember where he got the script. It is the exact same script as the one in the sticky, and it downloads and installs the beta version released in december.
But you don't want the beta version that came out in december, because there is now an official release that's newer than the beta version from december.....

---

### Post by jocko on 2009-03-17
> **jespdj said:**
> But you don't want the beta version that came out in december, because there is now an official release that's newer than the beta version from december.....
Also true.

---

### Post by GeneralCody on 2009-03-17
Here is the way to get your java plugin working. Some other ways exist, but many sites, such as home banking solutions etc, demand the official Sun Java plugin for secure applets.

Be sure to uninstall the icedtea plugin first, then follow these instructions carefully:

Install a working sun java jre from the standard repos so you can execute the .jar file properly.

then:
download the early access java jar file from sun

[http://www.java.net/download/jdk6/6u14/promoted/b03/binaries/jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar](http://www.java.net/download/jdk6/6u14/promoted/b03/binaries/jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar)

```
sudo java -jar [path_to_jarfile you downloaded]
```choose to install in /usr/lib64/jvm/ in the graphical installer that pops up.

now make all files in the new directory executable (as mentioned on Sun's site):
```
sudo chmod +x /usr/lib64/jvm/jre1.6.0_14/lib/amd64/*
```then link the needed file to the right directory with the following commands:

```
sudo ln -s /usr/lib64/jvm/jre1.6.0_14/lib/amd64/libnpjp2.so /usr/lib64/mozilla/plugins/libnpjp2.so
```Make sure to use complete file paths when creating symbolic links, or you will get a cyclical link referring back to itself, in other words, it wont work.

Restart your browser and check with about:plugins in the url field, that the plugin is in fact installed! ;-)

Now, uninstall the sun jre from the repositories, and link the java executable to /usr/local/bin and give it execute permissions:

```
sudo ln -s /usr/lib64/jvm/jre1.6.0_14/bin/java /usr/local/bin/java
sudo chmod a+x /usr/local/bin/java
```

That should be it...

---

