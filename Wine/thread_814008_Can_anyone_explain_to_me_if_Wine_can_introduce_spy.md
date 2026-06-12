---
title: "Can anyone explain to me if Wine can introduce spyware or virus&gt;"
date: 2008-05-31
forum: Wine
---

### Post by cnbiz850 on 2008-05-31
I often wonder about the following:

If I always just run Wine with one trusted program, would it be possible that someday a malware could be introduced in the system and get started automatically whenever Wine is started?

---

### Post by Sam Lars on 2008-05-31
I think it's possible that a virus could be introduced into Wine, and it may screw up Wine, but I think someone would have to write a virus specifically to hurt Linux through Wine.

---

### Post by madjr on 2008-05-31
if that ever happens is just a matter of uninstalling windows, errr wine.

also, wine doesn't auto-launch programs.

---

### Post by cogadh on 2008-05-31
Viruses and malware can run in Wine, but unless you use a root account or sudo to run Wine (which you shouldn't), they can't do any damage to your system beyond screwing up the .wine directory (which can be fixed simply deleting it) or possibly your home directory (which would be a little harder to fix). Because of the inherent security of Linux, any malware or virus introduced into Wine would not actually be able to propagate or directly effect the OS. 

BTW - Wine does autolaunch programs, support for the "Run" and "RunOnce" registry keys was added a few versions ago. If you have installed any software that launches at boot by default in Windows, it will actually run every time you launch something else with Wine. I only discovered this when I tried installing something new after installing Steam. The new install errored out when Steam encountered a problem at launch.

---

### Post by cnbiz850 on 2008-05-31
> **cogadh said:**
> 
BTW - Wine does autolaunch programs, support for the "Run" and "RunOnce" registry keys was added a few versions ago. If you have installed any software that launches at boot by default in Windows, it will actually run every time you launch something else with Wine.

This is actually what I worry.  Most Windows malware are launched without your knowledge by default at boot time.  If this happens with Wine, then a program such as a key-tracker for instance can cause a lot of damage.  Is there a way to check about whether there are anythings other than my desired programs running under wine?

---

### Post by cogadh on 2008-05-31
The difference is, it won't happen at boot time in Linux with Wine, it will only happen when you actually run something in Wine. The initialization of the wineserver just prior to an application launch is similar to a Windows boot (i.e. it loads the registry, including the run keys). Not to mention, the only way malware can get into Wine is if you install it yourself. As long as you aren't installing any software from untrusted sources, you won't get any malware into Wine.

If you are that concerned about malware in Wine, you can see what is active by using System Monitor (in Ubutntu) or System Guard (in Kubuntu). Anything running with Wine will usually have an .exe on the end of the process name.

---

