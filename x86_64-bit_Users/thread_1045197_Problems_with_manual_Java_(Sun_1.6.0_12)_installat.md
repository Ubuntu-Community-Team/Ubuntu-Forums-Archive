---
title: "Problems with manual Java (Sun 1.6.0_12) installation"
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by Chrigi on 2009-01-20
Hello

Because I wanted to have the new (still in testing) 64bit Java browser plugin from Sun, I installed jre1.6.0_12 manually to /usr/lib/jvm
I also made all the necessary links to be able to load it in my FF3.0.5 (don't know where I got the tutorial from) and that worked perfectly. It also helped me with Maple12 which did not run correctly with the bundled jre.
Now I want to set this as default for the whole system but "sudo update-alternatives --config java" does not show this jre:
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-cacao/jre/bin/java
          3    /etc/alternatives/kaffe-system/bin/java

Press enter to keep the default
[*], or type selection number: 

How can I get the manually installed jre1.6.0_12 as my systems default?
And a small side question: It appears that out of nothing another jre1.6.0_12 folder appeared in / with only a "desktop" folder in it which contains two files. Does this belong there? Or is this just junk?

I hope someone can help me :) 
Thank you

---

### Post by empty_tank on 2009-01-20
Please read [http://www.64bitjungle.com/](http://www.64bitjungle.com/)

I've tried the instructions and everything is okay.

---

### Post by ubun_two on 2009-01-20
Do you need other JVM?  Is uninstalling others an option?

---

### Post by Chrigi on 2009-01-21
Thank you.
The instructions at: [http://www.64bitjungle.com/ubuntu/finally-sun-release-64-bit-browser-plugin-support-for-jre-almost/](http://www.64bitjungle.com/ubuntu/finally-sun-release-64-bit-browser-plugin-support-for-jre-almost/)
worked great.

---

### Post by empty_tank on 2009-01-21
I also removed openjdk, cacao and kaffe. no problems so far

---

