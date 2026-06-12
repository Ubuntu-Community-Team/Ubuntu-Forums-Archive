---
title: "[SOLVED] Update appears to lock up."
date: 2008-05-12
forum: x86 64-bit Users
---

### Post by bilijoe on 2008-05-12
Early this morning, my 64 bit Ubuntu 8.04 system (a Compaq Presario 2000V notrbook, w/ AMD Turion 64, and 1 Gb ram) put up the little star alerting me that updates were available.  I clicked on it, as I have so many times before--the update manager started up, and announced that there were 30 updates available.  Seemed like a lot, but then this is a new version, so I clicked "Install".  The update manager window went gray, and nothing appeared to happen.  I've noticed different behavior from the update manager on this system before, compared to my other systems.  I haven't taken the time to determine if it's a 64 vs 32 bit issue, or 7.10 vs 8.40.  Anyway the slightly odd behavior didn't bother me, so I went about doing things on one of my other computers.  An hour later, however, the screen hadn't changed.  So I decided the update was hung, and tried to close the window. Wouldn't close.  So I decided to kill the process, but, according to the jobs list, there was nothing running, so there was nothing to kill.  After several attempts to get the dead window off my screen, I finally resorted to rebooting (I hate to do that--it reminds me so much of windows).  Got a clean reboot, and the little update star was still there.  Hoping it was just some transient glitch, I tried the update again--same result.  Is anyone else having this problem?  Does anyone know what to do about it?  If it's a problem with the update itself, or a bug in the update manager?  Any suggestions would be appreciated.

---

### Post by philinux on 2008-05-12
I've not got any updates today. Have you got proposed repo as a source?

---

### Post by bilijoe on 2008-05-12
I just got the standard "updates are available" notice, and clicked on the little orange star-like icon in the top panel.  That launched the update manager, as it always does, which then checked for updates, and said 30 were available.  The list started out with: apparmor, apparmor-utils, bsdutils, capplets-data, compiz-fusion-plugins-main, foomatic filters, and gnome-about.  I clicked the "Install Updates" button, and the Update Manager window went gray, and the cursor turned into a wristwatch (which is new:confused:), so I assumed the process had started.  Shortly though, it was obvious that nothing was happening.  I can move the window around, but can't close it.  I let it run all night, just to see if anything would happen.  It didn't.  I just now ran, in a terminal window, "sudo jobs" and got the "sudo: unable to resolve host Shelby" bug.  Just running "jobs" results in nothing, no list, so I can't get info I'd need to kill the update manager.  I just remembered the icon that can be added to a panel, to force an application to quit.  I installed that and was able to kill the Update Manager window that way, so I guess I don't have to go the old Windows route, and reboot after all.  I'm so glad I switched to Linux!:)  Anyway, if anyone else runs across this situation, or finds out what's going on, please let me know.

---

### Post by bilijoe on 2008-05-12
I just tried running Update Manager from the menu, instead of clicking the little notification icon, and it appears to be working correctly.  Don't know if running it from the menu made the difference, or if whatever was wrong got fixed, overnight.  Anyway, this problem seems to be solved for now.:)

---

### Post by sissn on 2008-05-15
I had the same problem but found this fix!

Worked fine for me!

> **brown705 said:**
> I was having the same problem myself, but I just found the answer at the bottom of this thread:

[https://answers.launchpad.net/ubuntu/+question/29446](https://answers.launchpad.net/ubuntu/+question/29446)

For your reference, I'll paste the post with the fix from the launchpad.net forum here:

[QUOTE=brown705;4895802]
SwissMike said on 2008-04-18:

Problem solved.

Turns out that the localhost setting in /etc/hosts was incorrect. The fix is going to menu ' System', then 'Administration', then 'Network'. Select the tab Hosts, enter password in dialog box, then change the localhost name:

127.0.0.1 PCName.networkName

to

127.0.0.1 PCName

and save it. Done. Whole problem gone. Interestingly, Bug #195308 confirms the same problem. Hope this small issue gets fixed before the Apr 21 release as it was nasty while it lasted.

Greetings from Switzerland,
Mike. 

Worked for me! \\:D/

Michael[/QUOTE]

---

