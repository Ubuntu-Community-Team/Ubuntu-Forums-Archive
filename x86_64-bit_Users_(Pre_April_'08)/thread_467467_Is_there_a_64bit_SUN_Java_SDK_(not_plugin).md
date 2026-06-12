---
title: "Is there a 64bit SUN Java SDK (not plugin)?"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by macubo on 2007-06-07
Hi all, I just need to know if any of you ever tested the installation of a Java SDK. I don't need the browser plugin at the moment.

I know there are major problems in running a 64bit plugin in a 64bit browser (it simply doesn't exist, didn't it?), but this created some confusion in my mind:

what is the free-java-sdk (the one in the repo) for? Can it handle Java-DOC?
SUN do provide a [linux64 Java SDK version 5.0u12]("https://sdlc2b.sun.com/ECom/EComActionServlet;jsessionid=50EC061ACF48FD43F3004D691DE382EE#"), did anyone install it?

Thank you

---

### Post by jrocket on 2007-06-07
I've installed it, and as far as I can tell it works fine.
I don't think the link will work for others, so if you go to the Java(TM) SE Development Kit 6 downloads, scroll to the bottom where it says Linux x64 Platform - Java(TM) SE Development Kit 6 and download  jdk-6-linux-amd64.bin.

---

### Post by macubo on 2007-06-08
Thank you for your reply.
I actually installed the sun-java5-jdk from the ubuntu repos. It is still 5.0u11, though.
With eclipse it works perfectly.

It's incredible how powerful the synaptic packet manager is.
Linux has really improven a lot in the last years.. bye!

---

### Post by jrocket on 2007-06-08
I guess I'm so used to having to build everything from source or directly install the package that most of the time I don't even think to look in Synaptics.  Oops!

---

### Post by sel on 2007-06-08
Yup the real thing from Sun is in the repos but even after installing from there the nasty gcj still lurks as the nasty default until you 'sudo update-alternatives --config java'

---

### Post by macubo on 2007-06-09
well i had some minor problem with AWT and the GTK toolkit using SUN's Java.. Anyway got it working googling for the error message, as posted somewhere else in this forum. Just had to install another package..

---

### Post by Mr_bleu on 2007-06-09
> **sel said:**
> Yup the real thing from Sun is in the repos but even after installing from there the nasty gcj still lurks as the nasty default until you 'sudo update-alternatives --config java'

Thanks for the config tip.  I can now run frostwire.

---

### Post by sel on 2007-06-09
> **Mr_bleu said:**
> Thanks for the config tip.  I can now run frostwire.

;)

---

