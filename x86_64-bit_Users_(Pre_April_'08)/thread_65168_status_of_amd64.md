---
title: "status of amd64"
date: 2005-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by rdwtux on 2005-09-13
Hi, 

It's been a while since I tried amd64 on my compaq presario laptop and thought i'd ask for others opinions of the maturity of it.  

Specifically I'm interested in: 

- nvidia drivers support (commercial)
- ndiswrapper w/64 bit windows drivers 
- broadcom 64bit drivers?
- general application availability
- java, shockwave flash, etc support
- other caveats?

Thanks.

---

### Post by mlomker on 2005-09-13
[QUOTE=rdwtux]- java, shockwave flash, etc support[/QUOTE]

Blackdown for the browser and Sun for apps.  
Only gpl flash and it isn't 100%.  
No soft-modem support.  
You end up compiling a lot more stuff for yourself.

---

### Post by tseliot on 2005-09-13
[QUOTE=rdwtux]Specifically I'm interested in: 

- nvidia drivers support (commercial)[/QUOTE]

They work fine (obut you can't install the 32bit opengl compatibility libraries but Opengl screensavers and other applications run fine though). I've made a guide about that.

---

### Post by DancingSun on 2005-09-13
Since it's only 1 month away, I  think you should ask this question after we tried out the Breezy release.  Or you could do that yourself too.

Generally, I think the Hoary release leaves a lot to be desired on the AMD64 platform.  Although unofficial community efforts, like Tamir's AMD64 repository and tseliot's guides are making Ubuntu64 easier to cope with.

Commercial application support is also very frustrating (flash, java plugin).  Although there are community efforts (gplflash, blackdown java), they don't work in all cases.  Yesterday, I was helping a forumer to get her blackdown java plugin working.  While the plugin did work, a specific piece of java code on the website of her bank's account login handling causes the blackdown java virtual machine to crash.  On windows, with Sun's JVM this doesn't happen.

Realistically, I don't think commercial application support will become prevalent until one of MS's Windows (64-bit XP, or Vista) becomes popular.  Or, fails miserably, and somehow 64-bit Linux takes over.

---

### Post by mlomker on 2005-09-13
[QUOTE=DancingSun]Since it's only 1 month away, I  think you should ask this question after we tried out the Breezy release.  [/QUOTE]

The Kubuntu version is a trainwreck at the moment.  They are make a lot of changes in kcontrol and as of last week many of the applets were broken.

---

