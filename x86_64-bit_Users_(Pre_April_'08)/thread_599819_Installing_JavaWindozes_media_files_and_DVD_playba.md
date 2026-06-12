---
title: "Installing Java/Windozes media files and DVD playback in Gusty"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ianb72 on 2007-11-01
How do I install the following:

1. Java in Firefox
2. Codecs to play Windoze media files and MP3's etc
3. Play DVD's

I tried [HTML]sudo apt-get install sun-java6-plugin[/HTML] for the Java and I got the following error
[HTML] ian@ian-desktop:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
[/HTML]

Thanks
Ian

---

### Post by John.Michael.Kane on 2007-11-01
> **ianb72 said:**
> How do I install the following:
I will try to point you in the right direction.

> **ianb72 said:**
> 1. Java in Firefox

For java you have two options.

1) sudo aptitude install icedtea-java7-plugin
2) [Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64]("http://ubuntuforums.org/showthread.php?t=202537")

> **ianb72 said:**
> 2. Codecs to play Windoze media files and MP3's etc

3. Play DVD's
For codecs/flash/etc the information is listed in this sticky thread.[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by brianbarry on 2007-11-03
I used Automatix to install w64 codecs and decss.  getautomatix.com.

Brian

---

### Post by tubasoldier on 2007-11-03
also check out medibuntu. It simply adds W32codecs and flash and libdvdcss to your repository packagesme     [www.medibuntu.org](www.medibuntu.org)

---

### Post by Kilz on 2007-11-03
> **brianbarry said:**
> I used Automatix to install w64 codecs and decss.  getautomatix.com.

Brian

I would caution anyone who considers Automatix to not use it. [Automatix can break a Ubuntu system.]("http://mjg59.livejournal.com/77440.html") The applications you suggest can be easily installed with synaptic (libdvdcss2) or are no longer necessary (windows codecs).

---

