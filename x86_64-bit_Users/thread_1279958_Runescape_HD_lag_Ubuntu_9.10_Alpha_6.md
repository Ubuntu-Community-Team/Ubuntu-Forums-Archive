---
title: "Runescape HD lag Ubuntu 9.10 Alpha 6"
date: 2009-10-01
forum: x86 64-bit Users
---

### Post by yaiyuy8W on 2009-10-01
I have graphic drivers installed, the java plugin (from sun) and update-java-alternatives is set to suns, and I still receive massive amounts of lag in RS low detail. The game will not even switch to HD mode. 

Any suggestions?

---

### Post by yaiyuy8W on 2009-10-01
What I did to fix this problem was:


[LIST=1]
[*]Used apt-get to uninstall all versions of Java.
[*]Used apt-get to install sun-java including jdk
[*]update-java-alternatives -l to get java list, then : sudo update-java-alternatives -s [suns java]
[*]Went to mozilla and installed firefox (this is 32 bit!)
[*]apt-get install ia32-java
[*]sym linked 32 bit java plugin link to 32 bit firefox /mozilla/plugins
[*]Restart firefox (even if you have 64 bit version running)
[*]This fixed RS not being able to go into HD mode. This also fixed the massive amount of lag.
[/LIST]

---

### Post by doorknob60 on 2009-10-01
In the future, If anyone else has the same problem, here's a more detailed guide to the the steps mentioned above: [http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu](http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu)

---

