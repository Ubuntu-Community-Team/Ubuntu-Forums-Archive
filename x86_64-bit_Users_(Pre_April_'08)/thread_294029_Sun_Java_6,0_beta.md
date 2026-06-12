---
title: "Sun Java 6,0 beta"
date: 2006-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by igknighted on 2006-11-06
Has anyone tried the sun java version 6.0, esp. the JDK (the current lack of which being the main reason I am still using 32 bit)?  Does it work well with ubuntu?  For basic stuff does it play nice with 5.0?

---

### Post by FluffyElmo on 2006-11-06
I've installed and used the Mustang JDK for the last first beta of 6.0. Everything works as well as I'd expected, Netbeans and Eclipse both run well and use it as the default JDK for instance. I built and ran the Aerith project with both IDEs without problems.

I still use 5.0 day-to-day so I can't say there aren't problems I didn't encounter. I use 5.0 because some of the projects I work on don't like 6.0, but that isn't a 64bit issue, more of a laziness issue on my part :)

Some caveats, the EE server installer didn't like 64bit but Glassfish itself (and other J2EE servers) runs fine. I also had a glitch with a Netbeans Enterprise Pack beta, but it's unclear whether it was a 64bit issue. That was all quite some time ago so these may be fixed. I mostly use Eclipse but sometimes like to see how Netbeans is coming along. Also, there are still no Java WebStart or Applet plug-ins so if that is a real issue it's not for you. I run 32bit Ubuntu and Windows in the free VMWare Server VMs for times when I have to test WebStart. 

I should note that I use the JDK downloaded from Sun, and I download all my tools and IDEs directly. I tried the Eclipse in the repository once and didn't care to repeat the experience so I make a point of downloading it manually.

Overall, I've always found Java development (particularly in Eclipse) to be faster and more responsive on 64bit whether you're using 5.0 or 6.0. Assuming you have enough RAM I think it's worth the upgrade. Since you can still run 32bit when needed it's pretty much a no lose situation.

Sorry for the length, but hopefully it was of some help. If you have any questions I didn't touch on fire away :)

---

