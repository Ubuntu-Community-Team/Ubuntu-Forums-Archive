---
title: "/usr/bin/java : doesn't exist???"
date: 2008-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by HgBoy on 2008-04-08
I am currently running 7.10 x64.  I am in a java programming class that requires me to have sun-java6-jdk and netbeans 6.0.1 installed on my computer for course work.  I removed iced tea, and install the packages through synaptic (also tried command line).  Everything says it installed fine, but when i type in 

```
 java -version 
```

the system tells me that /usr/bin/java doesn't exist.  Where would the sun java have been installed? Am I missing something completely?

---

### Post by Kilz on 2008-04-08
look in
/usr/lib/jvm/

---

### Post by HgBoy on 2008-04-09
it is installed in /usr/lib/jvm.   Question now is, how do I get my system to look there instead of /usr/bin/java ?  I tried making a link using ln, but the link is broken after it is created...

---

### Post by HgBoy on 2008-04-09
Nevermind.  Got netbeans installed and pointed it to the jvm directory. Thanks for the help :)

---

