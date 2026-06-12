---
title: "HOWTO: Get Eclipse Europa working with a 64 bit ubuntu installation"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ajaygautam on 2007-09-03
Here is a hack to get Eclipse Europa 64:

[LIST=1]
[*] Download Europa 32 bit from eclipse.org / mirrors.

[*] Download the 64 bit version of Eclipse 3.3. I downloaded it from [http://www.mirrorservice.org/sites/download.eclipse.org/eclipseMirror/eclipse/downloads/drops/R-3.3-200706251500/](http://www.mirrorservice.org/sites/download.eclipse.org/eclipseMirror/eclipse/downloads/drops/R-3.3-200706251500/)

[*] Untar Europa 32 bit

[*] Untar Eclipse 3.3 64 bit in a way that overwrites the stuff in the Europa 32.

[*]5. Start eclipse. Enjoy.
[/LIST]

Reasoning:
[LIST]
[*] Java is pretty much platform independent.
[*] More likely than not, the plugins included in Europa will be platform / arch independent.
[*] Therefore, the only dependent parts would be the eclipse app / sdk itself.
[/LIST]

I tested this theory with the above steps, and eclipse has been working for the past 5 minutes. If anything breaks, I will post it here.

Feed back welcome and appreciated.

Ajay Gautam
PS: I hope Eclipse.org starts providing an official 64 bit bundled release.
PPS: This is also being posted to Eclipse newsgroup.

---

### Post by lucaa on 2007-10-17
Thanks a lot!

It worked for me too, and besides that, it is a very easy set of steps that anyone can follow!

---

### Post by ajaygautam on 2007-10-17
Well.. great.

I had some other apps that only supported 32 bit.

So, I got rid of my 64 bit install.
Had to install ubuntu 32 bit on my 64 bit machine ...sigh...

---

### Post by trulore on 2007-10-21
Actually there's another way:

The actual problem (at least in my case) was caused by the JVM that comes native with Ubuntu.  It's not quite 100% compatible with the way the Sun JVM works, and that causes issues.

Simply download the latest 64-bit JVM from sun, and start up eclipse with the "-vm" argument.

eclipse -vm /YourJavaPathHere

And for the vm path, you have specify the full location of the "java" command, not just the home directory for java.  

This has worked fine for me, and resolved the errors I got previously when trying to run 64-bit Eclipse 3.3.1 on 64-bit Ubuntu 7.10

Eclipse is now running perfectly well for me.

---

### Post by Bokonon on 2007-10-22
Using jRockit might also be an option for some users.

My eclipse install (binary) seems to work better with jRockit than any of the recent Sun JVM's (1.6 u2/u3)  

Eclipse 3.2.2 (and 3.3) would crash on me periodically with the sun jvm.  I don't really have that problem with jRockit

[BEA jRockit]("http://www.bea.com/framework.jsp?CNT=index.htm&FP=/content/products/weblogic/jrockit/")

---

### Post by tamagotchi on 2008-03-08
JRockit seems to do the trick. Eclipse didn't crash after 2 minutes opening closing projects and doing random stuff.

JRockit Rocks!!! :guitar:

Thanks BEA.

Cheers,

Tamagotchi

---

