---
title: "+javahome J/maanova issue in Dapper AMD64"
date: 2006-10-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by powerofslack on 2006-10-06
Hi all, I have a Dapper AMD64 question that I haven't been able to Google up any answer to so far- thanks very much in advance for any help you can provide.  I've tried to run J/maanova (  [http://www.jax.org/staff/churchill/labsite/software/Jmaanova/index.html](http://www.jax.org/staff/churchill/labsite/software/Jmaanova/index.html) ) on Ubuntu 6.06 (Dapper) AMD64, on 3 different machines (AMDK8 3200, AMDK8 3400, Intel Core2Extreme) and I always run into the same problem.  When I try ./Jmaanova-linux in its directory (after chmoding it +x), I always get "Unable to find a supported JDK or JRE version. Version 1.3.1 or higher is required.  Check your installation and use +javahome to specify the JDK or JRE location" - My R, Rserve, and Java installations work fine for everything else on all of these machines- looking in /usr/lib/jvm/ , in all cases I see three installations (2 64 bit and one 32 bit), and none seems to work when specified via +javahome.  I've also copied Jmaanova and its directories to each of the jvm directories and tried to run it from there as well but no help.  The jvms I have installed are:  ia32-java-1.5.0-sun-1.5.0.06 , java-1.5.0-sun-1.5.0.06, and java-1.4.2-gcj-
4.1-1.4.2.0 .  I'm also going to forward the question to the Jmaanova developers and the google group for Jmaanova, but I haven't seen anything on the web about it so I thought I'd check here. Thanks again for any help you can provide!

---

