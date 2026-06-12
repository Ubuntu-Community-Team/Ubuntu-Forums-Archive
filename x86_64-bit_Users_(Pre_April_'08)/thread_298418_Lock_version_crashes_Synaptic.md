---
title: "Lock version crashes Synaptic"
date: 2006-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2006-11-12
Hello, I have a problem with edgy Synaptic.
I have a package that I want to lock the version, but everytime I click in "Lock Version" in Synaptic, it just closes Synaptic, and the package stays unlocked. Have anyone had this bug? Is there any workaround?

---

### Post by puppy on 2006-11-13
I posted a thread about this problem a few days ago friend - had no advice so far, I think it was actually reported as a #bug, but I can't find the thread that gave the bug reference - I know it's not fixed because I'm having exactly the same problem - extremely annoying! :mad:

---

### Post by darkshadow on 2006-11-13
Same problem and I have spent hours searching and have yet to find a fix.

---

### Post by earobinson on 2006-11-13
report it!

---

### Post by darkshadow on 2006-11-13
I remember seeing it reported multiple time but I forget the launchpad numbers.

---

### Post by xstaticxgpx on 2006-11-13
i reported this to launchpad 2 months ago, yet nothing has been done so far.

---

### Post by earobinson on 2006-11-13
there might be a way to lock it using apt-get in the command line

---

### Post by rogeriovinhal on 2006-11-13
Locking it with aptitude doesn't lock it with the update-manager, which is the main reason for me to want to lock a package, so it will stop asking me to upgrade a package I know is newer, but only because it isn't in the repositories, it thinks it is older...

---

### Post by rogerioferro on 2006-11-23
use this:

sudo su
echo "pkg-name hold" | dpkg --set-selections

it will lock your package...

---

### Post by darkshadow on 2006-11-24
Thank you, It is nice for the update notification to be gone for the first time in over a month.

---

