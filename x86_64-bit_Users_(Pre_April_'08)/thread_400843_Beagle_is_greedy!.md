---
title: "Beagle is greedy!"
date: 2007-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mongoose on 2007-04-04
We all enjoy how beagle can use 100% CPU utilization indexing text files, but with current feisty more joy ensues.  It seems a few beagle plugins are reporting various errors over and over in the Logs -- to the point of exhausting disk space.  I was wondering if anyone else is having this problem, since it only happens on my x86_64 box.


.beagle/Logs:
-rw-r--r-- 1 mongoose mongoose 1.9G 2007-04-04 00:05 2007-04-03-23-13-21-Beagle

Currently my workaround has ~/.beagle/Logs symlinked to /tmp/Logs and rm -f the followed current-Beagle symlink and killall -HUP beagled ever so often.   I'm just curious if anyone else has this issue, since I've upgraded several times this week and it still happens.  I have some extra libmono and mono dev packages installed, but other than that it's bog standard install in terms of mono.  I'll have to start altering the fitlers or disabling beagle on new installs at this rate.  I also have workaround scripts for network-manager, and I'm starting to feel like I'm on slackware from the Linux 1.x days.  If some can confirm I can file a bug at least.  =(

---

### Post by Kilz on 2007-04-04
Feisty Fawn is under development.[ As such it has its own section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=179"). It also isnt recommended for use as a desktop for every day use. It should only be used to check for bugs, to be reported on launchpad, and its own section of the forum. You might want to post this there.

---

### Post by Mongoose on 2007-04-04
Thanks I clicked in the wrong section.  I shouldn't post after midnight.  ;)

---

