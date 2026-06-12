---
title: "Java applets don't work (grey boxes)"
date: 2008-11-10
forum: x86 64-bit Users
---

### Post by enigmatichus on 2008-11-10
Hello everyone. I have a laptop with intrepid ibex 64-bit edition, and java packages installed (I have sun-java6-bin version 6-10-0-ubuntu2, icedtea and other related packages installed via synaptic). When I try to open something (for example, this: [http://coglab.wadsworth.com/experiments/AttentionalBlink.shtml](http://coglab.wadsworth.com/experiments/AttentionalBlink.shtml)), in the place where it should be the applet appear a grey box, and in the bottom bar in firefox there is "Applet loaded." I tried to reinstall everything, but without succeeding. The strange thing is that if I try this: [http://coglab.wadsworth.com/support/browsercheck.html](http://coglab.wadsworth.com/support/browsercheck.html) (which is the browser test of the same site I can't use), in the applet space successfully appears "Java 1.6.0_0 from Sun Microsystems Inc. Check for Pop up Blocker conflict", and if I push the button, the pop up blocker checker appears. So I don't understand why a little applets work, and others not. Please help me, I need java for my school. Thank you.
Luca

---

### Post by redbass on 2008-11-10
The SUN haven't distribute the JRE 6 64-bit plugin and will be available in only in 2009.
U can install IceTea and OpenJDK, but not all java programs works fine...
So, if u wonna know more about look the main thread [http://ubuntuforums.org/showthread.php?t=774956]("http://ubuntuforums.org/showthread.php?t=774956")

byez

---

### Post by Sef on 2008-11-11
Applets are working now with [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956").  Though Live connect is still not implemented.

---

### Post by enigmatichus on 2008-11-11
Mmh.. And assuming that OpenJDK is installed and run correctly, until the release of some kind of patch for 64-bit systems, I will not execute some applets? Is the problem in the Java Runtime Environment or in Icedtea or something else?? Anyway, thank you very much for the informations!

---

