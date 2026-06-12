---
title: "iced tea vs. blackdown"
date: 2008-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by shane2peru on 2008-02-03
OK, I'm new to the 64bit world, and content to be here.  I was looking at the problem of no java for 64bit, I know I can use a 32 bit work around, but wondered, which is better, Iced Tea, Blackdown, or 32bit FireFox with 32bit Java?  I'm just curious about other's experiences.  Is it worth my time to give the two open source java ones?  Is anyone still developing these open source java deals?  If I use them, would that be helping the open source developers, or do they know the problems and are just trying to find solutions?  Thanks.

Shane

---

### Post by Kilz on 2008-02-03
> **shane2peru said:**
> OK, I'm new to the 64bit world, and content to be here.  I was looking at the problem of no java for 64bit, I know I can use a 32 bit work around, but wondered, which is better, Iced Tea, Blackdown, or 32bit FireFox with 32bit Java?  I'm just curious about other's experiences.  Is it worth my time to give the two open source java ones?  Is anyone still developing these open source java deals?  If I use them, would that be helping the open source developers, or do they know the problems and are just trying to find solutions?  Thanks.

Shane

I would suggest icedtea over Blackdown. Icedtea is a newer java, Blackdown is java 1.4 and has a tendancy to crash the browser. If you go to a site where icedtea doesnt work ( there are a few) and you need to use that site then install the 32bit firefox [with my script.]("http://ubuntuforums.org/showthread.php?p=1174435")
At this point 32bit firefox is a last resort. But I will support my script and the 32bit firefox packages (and varations) until Sun Java 7 is released. Sun Java 7 will have a 64bit plugin, but 7 is still under development.

---

### Post by shane2peru on 2008-02-03
> **Kilz said:**
> I would suggest icedtea over Blackdown. Icedtea is a newer java, Blackdown is java 1.4 and has a tendancy to crash the browser. If you go to a site where icedtea doesnt work ( there are a few) and you need to use that site then install the 32bit firefox [with my script.]("http://ubuntuforums.org/showthread.php?p=1174435")
At this point 32bit firefox is a last resort. But I will support my script and the 32bit firefox packages (and varations) until Sun Java 7 is released. Sun Java 7 will have a 64bit plugin, but 7 is still under development.

Wonderfull!  Thanks, that is the one I happened to install.  To give it a try, I don't care to install 32 bit Firefox if I don't have to, so I will give it a good try.  I'm happy overall with the installation, the running of it, and all.  Seems to run fine thus far.  

Shane

---

### Post by Kilz on 2008-02-03
> **shane2peru said:**
> Wonderfull!  Thanks, that is the one I happened to install.  To give it a try, I don't care to install 32 bit Firefox if I don't have to, so I will give it a good try.  I'm happy overall with the installation, the running of it, and all.  Seems to run fine thus far.  

Shane

But even if you did, it wouldn't make any difference. You wouldn't lose anything. The reason is, Firefox is 32bit code and not optimized for 64bit. While its compiled for 64bit , it doesn't receive any performance boost. Also Firefox is not a number crunching application, so if it were true 64bit code the benefits would be low. The install script is mostly painless and only takes a few minutes to answer a few yes/no questions. So if you find icedtea has any issues, just remember 32bit firefox is available.

---

