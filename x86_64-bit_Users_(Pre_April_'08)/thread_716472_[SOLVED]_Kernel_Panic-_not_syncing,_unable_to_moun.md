---
title: "[SOLVED] Kernel Panic- not syncing, unable to mount root, permissions wrong"
date: 2008-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by caithness on 2008-03-05
I had a mysterious crash a couple days ago. Get basically that kernel panic message when I try to start up now. I made a fresh install on a different partition of the same disk, is there a way to fix the permissions from this install, or otherwise fix my old one? I can get all my data just fine, but it would be nice to not have to redo all my settings.

---

### Post by Defrector on 2008-03-06
Perhaps the first thing to try is attempt booting in recovery mode and see if you still get a panic. If you get a panic pay close attention to any complaining the console gives during the boot process before it panics and document it. Another thing to check is the /var/log directory of your flaky install-using your emergency install to view it- and check the logs to see if anything funky happened in the boot process that got documented. That would help us help you a lot.

EDIT: Are you 100% sure that there is a permissions problem?

---

### Post by caithness on 2008-03-06
It was giving a kernel panic in recovery mode too. But whe I tried it again it started up, but I couldn't access all my files right, but that doesn't matter anymore. After posting that last night I tried copying /boot from the reinstall to the panicky one, and since it started in recovery I decided to try regular start-up again, and it booted up fine. 
Thanks for trying to help even if I didn't give enough info, and I'm pretty sure the kernel panic message mentioned a problem with permissions.

---

