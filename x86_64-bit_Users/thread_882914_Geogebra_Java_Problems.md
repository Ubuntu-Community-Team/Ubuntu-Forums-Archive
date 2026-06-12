---
title: "Geogebra Java Problems"
date: 2008-08-07
forum: x86 64-bit Users
---

### Post by soxs on 2008-08-07
[www.geogebra.org](www.geogebra.org) (a math program I'd like to use)

SO I download the binary file.
but as soon as I try to run it with java, I get an arrow about requiering an 1.4.2 or newer javer version.
In fact I installed icedtea and sun jave and openjdk (jres ans all the other stuff) but it still keeps spitting that very same error on me.

Any ideas?? Mayy someone plx try this aswell, in case I only missed something.

---

### Post by soxs on 2008-08-07
all attempts to use the jar file with results in errors aswell:

```
java -jar GeoGebra_3_0_0_0.jar
Unable to access jarfile GeoGebra_3_0_0_0.jar
```

---

### Post by soxs on 2008-08-09
anyone?
anyone even ever heard of GeoGebra??

---

### Post by WhiteHorse on 2008-08-18
I got it to work by uninstalling openjdk and sun-java-5, and installing sun-java-6 in Synaptic.

At the command line, type java -version and you can see whether it's the Sun java or OpenJdk. Sun says 
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

I think this is a bug with the installer and it detects openjdk as Sun JRE<1.4.2. Oh well... Never knew I was running openjdk until this cropped up, but always having browser hangs with java...

---

