---
title: "Problem in linking for JNI (Java Native Interface)"
date: 2008-08-10
forum: x86 64-bit Users
---

### Post by Vesa Paatero on 2008-08-10
Hello,

I tried to link native code compiled with g++ into JNI in Edubuntu 7.04 (Feisty). However, I got the error "undefined symbol: __gxx_personality_v0" when my Java code tried to link the .so package created with ld. The problem is addressed on website 

[http://www.cse.iitb.ac.in/~soumen/download/JNITricks.html](http://www.cse.iitb.ac.in/~soumen/download/JNITricks.html)

which suggests that it has to do with incompatibility between GNU compiler/linker utilities and the JVM of Sun Java. The page advises you to install  java-1.5.0-sun-compat-1.5.0.08-1jpp  (with version numbers replaced with the timely ones) for compatibility. However, I couldn't find a package like that among the packages available in Synaptic. So, my question is: Is that package or its equivalent available for Ubuntu somewhere?  Or is there some other way around the problem?

Thank you for any help you can give.

Vesa

---

