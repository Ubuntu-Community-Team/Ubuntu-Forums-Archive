---
title: "Java 6 not available yet?"
date: 2007-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aruna on 2007-02-25
I have read that java6 is already in 32bits repos.
How long are we suppose to wait?

---

### Post by kleeman on 2007-02-25
It is I have it installed on a 64bit system (it is a 32bit app).

On edgy enable the multiverse repository and then

sudo apt-get install sun-java6-jre

---

### Post by John Jason Jordan on 2007-02-25
> **kleeman said:**
> It is I have it installed on a 54bit system (it is a 32bit app).
On edgy enable the multiverse repository and then
sudo apt-get install sun-java6-jre
I found that it didn't work very well. If I enable it in OpenOffice.org nothing that OOo requires Java for works at all. Best is Sun Java 5.0.

---

### Post by incubus on 2007-02-25
Yeah, I also found Java 6.0 behaving a little weirdly with some programs.  With others (e.g. eclipse), it works fine.  If you prefer stability, Java 5.0 may still be the one to go here.  That said, I still use 6.0 because I rarely run any Java program.

incubus

---

### Post by kleeman on 2007-02-25
> **John Jason Jordan said:**
> I found that it didn't work very well. If I enable it in OpenOffice.org nothing that OOo requires Java for works at all. Best is Sun Java 5.0.

What things did not work? I just tried it with a word doc and a sideshow for an odp file and it seemed fine.......

---

### Post by Aruna on 2007-02-25
> **kleeman said:**
> It is I have it installed on a 64bit system (it is a 32bit app).

On edgy enable the multiverse repository and then

sudo apt-get install sun-java6-jre

Multiverse repository is enabled.
:~$ apt-cache show sun-java6-jre
W: Unable to locate package sun-java6-jre
E: No packages found

---

### Post by kleeman on 2007-02-25
Hmmm I get

apt-cache show sun-java6-jre
Package: sun-java6-jre
Priority: optional
Section: multiverse/libs
Installed-Size: 14144
Maintainer: Matthias Klose <doko@ubuntu.com>
Architecture: all
Source: sun-java6
Version: 6-00-0ubuntu1~edgy1
Replaces: sun-java6-bin, ia32-sun-java6-bin
Provides: java-virtual-machine, java2-runtime, java1-runtime
Depends: java-common (>= 0.24), locales, sun-java6-bin (= 6-00-0ubuntu1~edgy1) | ia32-sun-java6-bin (= 6-00-0ubuntu1~edgy1), debconf (>= 0.5) | debconf-2.0
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Recommends: gsfonts-x11
Suggests: sun-java6-plugin | ia32-sun-java6-plugin, sun-java6-fonts, ttf-baekmuk, ttf-sazanami-gothic, ttf-sazanami-mincho, ttf-arphic-bsmi00lp
Conflicts: j2se-common
Filename: pool/multiverse/s/sun-java6/sun-java6-jre_6-00-0ubuntu1~edgy1_all.deb
Size: 6322356
MD5sum: 7b58f90b56ba2d48597ad89b730399be
SHA1: 60ee76952b556629dfbbdba2783c81b67407d45e
SHA256: cfddd4a358cb2028fe16cc5c14bc8f08a85efac4bbbb90bd9914c698a7df1bbf
Description: Sun Java(TM) Runtime Environment (JRE) 6
 The Sun Java Platform Standard Edition Runtime Environment (JRE) 6
 contains the Java virtual machine, runtime class libraries, and
 Java application launcher that are necessary to run programs written
 in the Java progamming language. It is not a development environment and
 doesn't contain development tools such as compilers or debuggers.
 For development tools, see the Java Development Kit JDK(TM) 6
 (package sun-java6-jdk).
 .
 NOTE: You must accept Sun's EULA prior to successfully installing
 this package
 .
 This package contains architecture independent files.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

It is listed on the Ubuntu packages site..

Which distro version are you using?

---

### Post by Aruna on 2007-02-26
I am using 6.10 Edgy 64-bit PC (AMD64).
I just made an update. Same answer.

I am connecting to the multiverse repositories.

From my sources list:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

In fact, I get this after searching for java5:

apt-cache search java5
ia32-sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0 (32-bit)
sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-demo - Sun Java(TM) Development Kit (JDK) 5.0 demos and examples
sun-java5-doc - Sun JDK(TM) Documention -- integration installer
sun-java5-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java5-jdk - Sun Java(TM) Development Kit (JDK) 5.0
sun-java5-jre - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-source - Sun Java(TM) Development Kit (JDK) 5.0 source files

Why not java6?:confused: 

Thank you for your interest.

---

### Post by kleeman on 2007-02-26
Try the edgy-backports archive as well i.e. duplicate your second line with edgy-backports replacing edgy-updates

---

### Post by Aruna on 2007-02-26
I got it.
Thank you Kleeman.

---

