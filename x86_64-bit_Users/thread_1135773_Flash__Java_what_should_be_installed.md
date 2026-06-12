---
title: "Flash / Java what should be installed?"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by ed-koala on 2009-04-24
Apologies if this is answered somewhere, but in trying to make sure my flash and java are set up correctly, it seems I may be getting conflicts from different types of installs.  I run Jaunty 9.04, upgraded from 8.10. AMD 64 machine.

Here is the Java installations (from Synaptic):

    openjdk-6-jdk
    openjdk-6-jre
    openjdk-6-jre-lib
    openjdk-6-jre-headless

    icedtea-6-jre-cacao

    sun-java6-bin
    sun-java6-jre

    java-common

    libaccess-bridge-java

    rhino

    tzdata-java

    ca-certificates-java

    ubuntu-restricted-extras

and for Flash:

    flashplugin-nonfree

also, attached is the result of about:plugins for Firefox

Are any of these redundant?  Seems that way with java, and I'm not sure why flash doesn't use adobe ... or is shockwave better?

---

### Post by Thelasko on 2009-04-24
OpenJDK and Sun-Java are redundant.

---

### Post by ed-koala on 2009-04-24
ok, i'll do a complete removal of one, is there a preference as to which might work more smoothly?  and shockwave vs adobe?

---

### Post by Thelasko on 2009-04-24
> **ed-koala said:**
> ok, i'll do a complete removal of one, is there a preference as to which might work more smoothly?  and shockwave vs adobe?

Generally the Sun version works more smoothly.  If you prefer open source to closed source, use OpenJDK.

I don't know about the shockwave vs. adobe thing.  I can't view the file on my machine right now (on Windows at work).  If everything is working with Flash, then I would leave it alone.

---

### Post by cdwillis on 2009-04-24
I installed ubuntu-restricted-extras instead of each individual package and everything is golden for me.

---

### Post by Arup on 2009-04-25
Open JDK is needed by Open Office and removing it would make OO loose its Java functionality, you can keep both installed, just select Sun in Java tab in OO and other apps.

---

### Post by Zyrshnikashnu on 2009-04-25
> and for Flash:

flashplugin-nonfree

also, attached is the result of aboutlugins for Firefox

Are any of these redundant? Seems that way with java, and I'm not sure why flash doesn't use adobe ... or is shockwave better?
Flash is an Adobe product. Shockwave was the predecessor to Flash, and the name sort of stuck around over the years.

Also, if you're running 64-bit, you may want to install Adobe's beta Flash plugin. It supports 64-bit browsers natively, without the help of ndiswrapper.

---

### Post by Thelasko on 2009-04-27
> **Arup said:**
> Open JDK is needed by Open Office and removing it would make OO loose its Java functionality, you can keep both installed, just select Sun in Java tab in OO and other apps.

[That doesn't appear to be true.]("http://packages.ubuntu.com/jaunty/openoffice.org-base")  I'm not running Jaunty, but I've had OpenOffice working without OpenJDK on other versions of Ubuntu.  You just need one type of Java Runtime Environment installed.  It doesn't matter which one.

You may have mistakenly come to this conclusion by trying to uninstall OpenJDK before or while you were installing Sun-Java.  In that case, Synaptic will tell you that Open Office will no longer work.  It's important to have the new version of Java installed before you try to remove the old one.

---

