---
title: "SUSE fresh install-Dependency hell when upgrading"
date: 2008-02-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by odiseo77 on 2008-02-12
Hello people, I installed openSUSE 10.3 two days ago, but when I was going to upgrade it, I got an error with some package I had to install manually (koffice, to be specific), so I installed online through yast, then attempted to upgrade my system again and this time it was something about kdegraphics; I did the same (installing it through yast), and now I get this message as soon as the upgrades start:

> 2 Problems: Problem: No valid solution found with just resolvables of best architecture. Problem: No es posible instalar amarok-yauap Problem: No valid solution found with just resolvables of best architecture. With this run only resolvables with the best architecture have been regarded. Regarding all possible resolvables takes time, but can come to a valid result. Solution 1: Make a solver run with ALL possibilities. Regarding all resolvables with a compatible architecture

So, I went to yast again, attempted to install amarok-yauap, but got an error telling me it has unmet dependencies, which is weird since I have all the main repositories enabled (including packman). Anyway, what's the sense of an upgrade tool which doesn't do the job of automatically installing all the required dependencies for the packages it's upgrading? :confused: Am I possibly missing some important repository here?

So, does anyone know what could be the problem and how to solve it? Thanks a lot in advance.

---

### Post by odiseo77 on 2008-02-13
Well, somehow I forced the installation of amarok and some packages related to amarok through yast and this time the updates went fine. The only issue I'm noticing is that for some reason, amarok is permanently shown as an update but it won't update -not sure why; I checked the version and it's supposed to be the last available version (amarok-1.4.8-100.pm.2).
As long as my other updates are installed fine, the issue is somehow solved... Anyway, if someone knows how to solve the never ending amarok update, I'd appreciate it.

Regards.

---

### Post by mzembe on 2008-02-13
It's been a while, I remember having a problem once with some distro or other.. probably ubuntu. I had special repositories for studio stuff, mixers and beaters maybe some lash/jack - it might have been AGNULA. 
Many of the applications had cross dependencies but 
i would want some new toy beyond the scope of what was available when the distro was created. The package manager would insist upon installing a version that heavily leaned upon library like jack or alsa. At any given point in time, core libraries could be undergoing major developments that break compatibility because somebody is trying to conform to areas of rapid development sort of like the low latency stuff when it was happening so you get a confused package manager?? that wants to upgrade one thing but the only available package for an installed application may reside on a repository that has a slower development cycle due to, say, support for audio session management or a new timer mechanism, needs old hooks (without a major overhaul) will break if you update something flagged for installation that only understands the 'new way'. In order to have it you have to break something else and your box says, "I'm sorry Dave, I can't let you do that."
You might have a repository enabled for something highly specialised that shares a critical dependency with an application you want that doesn't have a version on any of the repositories to satisfy both. Or something like that.

---

### Post by 67GTA on 2008-02-13
Were you using the update applet? I've had problems with it. Try updating with Yast, or zypper(cli).

---

### Post by odiseo77 on 2008-02-13
> **67GTA said:**
> Were you using the update applet? I've had problems with it. Try updating with Yast, or zypper(cli).

Hi, yes, I was using the update applet. This time I used yast and it worked. The weird thing is I used it before, like two days ago to upgrade my system but it didn't work. Anyway, thanks for the advice, it worked fine :)

---

### Post by 67GTA on 2008-02-13
The update applet should work now. They had an update for the update applet. Say that three times fast:)

---

### Post by dca on 2008-02-13
Yes, indeedy.  They had a KDE bug affecting amaroK...  It'd constantly harass you  of a pending update that would never install (but actually it did).  The only way I knew of prior to the update/fix was to go into YaST package manager and manually install the updates.  After that the update applet would go back to the 'no pending updates' look...

---

