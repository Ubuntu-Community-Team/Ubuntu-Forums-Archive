---
title: "Can't install JRE in Feisty Fawn"
date: 2007-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by jimbo11 on 2007-07-03
Hello, 

I've been trying tediously to install any version of JRE plugin for Firefox, but it just doesn't seem to work. I've tried installing it from the [www.java.com](www.java.com) site and following their instructions, installing it via Synaptic package manager (both j2re-x-x and sun-java-xxx, can't remember the exact numbers), installing it via Automatix and basically insering the linking file in every single plugin directory I can think of, still nothing. I did manage to install at one time jre 1.5.x but whenever I'd open a page in Firefox that had java, the browser would crash and close. 
I'm running Feisty Fawn, the lastest version of Firefox, all on an AMD Turion 64x2, on an HP Pavilion dv9000. Any help is appreciated....:p

Thanks

---

### Post by Kilz on 2007-07-03
> **jimbo11 said:**
> Hello, 

I've been trying tediously to install any version of JRE plugin for Firefox, but it just doesn't seem to work. I've tried installing it from the [www.java.com](www.java.com) site and following their instructions, installing it via Synaptic package manager (both j2re-x-x and sun-java-xxx, can't remember the exact numbers), installing it via Automatix and basically insering the linking file in every single plugin directory I can think of, still nothing. I did manage to install at one time jre 1.5.x but whenever I'd open a page in Firefox that had java, the browser would crash and close. 
I'm running Feisty Fawn, the lastest version of Firefox, all on an AMD Turion 64x2, on an HP Pavilion dv9000. Any help is appreciated....:p

Thanks

[ Please read the sticky post.]("http://ubuntuforums.org/showthread.php?t=368607") There is no safe way to install java to the 64bit browser. Other options are listed in that post.

---

### Post by jespdj on 2007-07-03
There is no 64-bit Java plug-in from Sun.

Look at [this bug in the Sun Java bug database](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695). It has been submitted on Jan 14, 2003 - more than FOUR YEARS ago... and finally Sun now seems to have promised to provide this in the next version of Java (version 7), which will be released in maybe 1.5 or 2 years... :mad: (see the remark at the top of the bug report: "This RFE has fianaly been comitted to the dolphin (JDK 1.7) release.").

Java 7 will be completely open-source, which means anybody can finally compile a 64-bit version.

At the bottom of the bug report Lord_Byte explains that he has a 64-bit GNU Java plug-in, but I'd recommend against it. GNU Java is a very weak and slow Java clone, you do not want to use it.

---

### Post by jimbo11 on 2007-07-03
Hello Jes and Kilz, 

Thank you very much for your responses, especially the sticky post by Kilz and the heads-up Sun's attempt to fix java for 64-bit. 
Well, I tried installing 32-bit firefox as per Kilz's sticky post and the installation went well, the firefox browser ran fine, the java plugin didn't. Sure, when I went to java.com and verified the installation, indeed it was there, albeit out of date, but it was still there. Then I went to a site to really test it ( a foreign exchange charting site [http://www.netdania.com](http://www.netdania.com) ) and it didn't work, all I saw was a little X up in the upper left hand corner of the page that used Java. 
Oh well, I have a new laptop 64-bit AMD, but all I've ever had with ubuntu 64-bit is problem after problem after problem, not just with Java, but also other apps. I'm going back to 32 bit ubuntu on my 64-bit laptop, at least I wont' have to pull anymore hair out and I can wait another year or two until the 64-bit world gets it right. 

Many thanks again for your help. :)

---

### Post by kuja on 2007-07-03
> **jespdj said:**
> ava 7 will be completely open-source, which means anybody can finally compile a 64-bit version. If it were that simple I'm certain it  would have already been done. There's certainly some sort of problems ... and, sadly, it probably has a low priority on Sun's agenda.

---

### Post by jespdj on 2007-07-04
> **kuja said:**
> If it were that simple I'm certain it  would have already been done. There's certainly some sort of problems ... and, sadly, it probably has a low priority on Sun's agenda.
Probably it's indeed more difficult than just compiling it to a 64-bit executable, but at least if the source is available someone could have a good look and fix it for 64-bit.

At least Sun seems to have promised that there will be a 64-bit Java plug-in with Java 7...

---

