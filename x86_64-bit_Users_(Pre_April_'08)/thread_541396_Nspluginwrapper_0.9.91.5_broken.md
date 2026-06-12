---
title: "Nspluginwrapper 0.9.91.5 broken?"
date: 2007-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Matakoo on 2007-09-02
Okay, first things first. I'm using the version of nspluginwrapper that is available through the Pure64 repo ([http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-upure64/main-amd64), and I usually keep my packages up-to-date.

I only use the wrapper for flash (which is the only plugin I have at all for that matter), and it has worked great since the computer was installed.

A few days ago, firefox started to behave odd. It kept locking up at worst, and was usually a lot slower than it usually is. To make a long story short, I managed to find what was wrong. On my machine that is...the latest update to nspluginwrapper seems to be broken. Not only did it slow down my firefox, it also managed to make flash not being able to show anything anymore. I just got a blank wherever the video was supposed to be. No complaints from firefox about a missing plugin or anything like that. 

I reverted back to the previous version (0.9.91.4) and the problem was gone.

Did anyone else notice this with 0.9.91.5?

---

### Post by jamesford on 2007-09-02
ive noticed firefox crashing a bit lately. never occured to me it could be nspluginwrapper. maybe it is, maybe it isnt. otherwise i have none of your sympthoms

---

### Post by Michael Matthews on 2007-09-02
received large update and flash stopped working. Reinstalled nspluginwrapper using script and started working again. Had no firefox  crash problem. Annoying.

---

### Post by Mochino on 2007-09-02
yep, it's broken right here too

---

### Post by Applegeek on 2007-09-02
I think it was the update Friday.  I completely removed, then re-installed the wrapper and it seems stable now.

---

### Post by John.Michael.Kane on 2007-09-03
Personally i have been unable to reproduce this issue at this time. That being said I have filed a bug report here [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/136991) .

Please add to report any information you have including any error msg's. Make sure to be as detailed as you can in explaining the issues your having.

---

### Post by Kilz on 2007-09-03
I have removed the test script (2.0) of the nspluginwrapper install script that installs that version of the wrapper. At least until we learn more.

---

### Post by Applegeek on 2007-09-03
This just happened 5 minutes ago on a Feisty -amd64 install, Firefox 2, manual install of nspluginwrapper -5  and Flash 9, little else installed.  System was working 100% fine all last week.

Just checked update manager, all packages updated.  System had to have nspluginwrapper -5 reinstalled after Friday's package update, then seemed to be working again.

Watching "TMNT - Don's Transofrmation" video at YouTube, over my daughter's shoulder. 

She just moved the mouse off the video window, and the system crashed.  No clicking or anything.  Scrambled lines on a video window that you can't kill, no keyboard, had to restart system.

Rebooted system, went back to the same video, and can't get it to happen again, moving mouse all over the place.

I can't tell if the mouse-move event caused the problem, or if it was coincidence.

Just reporting a possible clue.

Will send this to bug reports as well.

---

### Post by Applegeek on 2007-09-03
I loaded up a box with Gutsy-64 T5, NVidia -100 drivers, Firefox and Flash (as little as I could get away with).  Number2 Daughter is busy trying to break the Internet right now.  Aside from no full flash video window, it seems to be behaving itself for the moment...

Jeepers...I know there's still some bugs in Gutsy, but from what I've seen, its nice.  Haven't tried out Compiz/Emerald yet but we'll get there.

---

### Post by rubbsdecvik on 2007-09-08
I think this is because on my Gutsy install, the new update removes the linux32 package.  If I remember correctly nspluginwrapper depends on that.  When I tried to reinstall linux32, I got a really nasty warning, and I didn't go through with it.

Is this consistent with anyone else?

---

### Post by Kilz on 2007-09-08
> **rubbsdecvik said:**
> I think this is because on my Gutsy install, the new update removes the linux32 package.  If I remember correctly nspluginwrapper depends on that.  When I tried to reinstall linux32, I got a really nasty warning, and I didn't go through with it.

Is this consistent with anyone else?

Did you report the bug on launchpad?

---

### Post by rubbsdecvik on 2007-09-08
> **rubbsdecvik said:**
> 

Is this consistent with anyone else?

Found some info on this:

[http://ubuntuforums.org/showthread.php?t=545478&highlight=gutsy+nspluginwrapper]("http://ubuntuforums.org/showthread.php?t=545478&highlight=gutsy+nspluginwrapper")

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/138145]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/138145")

hopefully that helps someone.

---

### Post by Kilz on 2007-09-08
> **rubbsdecvik said:**
> Found some info on this:

[http://ubuntuforums.org/showthread.php?t=545478&highlight=gutsy+nspluginwrapper]("http://ubuntuforums.org/showthread.php?t=545478&highlight=gutsy+nspluginwrapper")

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/138145]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/138145")

hopefully that helps someone.

Did you add a comment that you were experiencing the problem? Every voice and comment helps.  :D

---

