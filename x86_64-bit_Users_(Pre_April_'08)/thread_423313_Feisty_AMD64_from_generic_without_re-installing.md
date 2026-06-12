---
title: "Feisty AMD64 from generic without re-installing?"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicklogan on 2007-04-25
After reading about the reasonably good success others have had with Feisty AMD64 and trying the live cd with my hardware, I'd like to try it. Can it be done without re-installing? I have the Feisty generic version I installed via an Edgy upgrade running fine now. Seems I remember there was a How-to on doing this in Dapper but I can't locate it.

---

### Post by kuja on 2007-04-29
To do a direct update via cd you have to be using the alternate cd. Else you'll have to do a reinstall. Only other option would be an online upgrade.

---

### Post by nicklogan on 2007-05-01
Thanks for the advice. Unfortunately, when trying to upgrade from the gui  I get: 

There was a error adding the CD, the upgrade will abort. Please report this as a bug if this is a valid Ubuntu CD.

The error message was:
'E:Unable to locate any package files, perhaps this is not a Debian Disc'

Trying to add the cdrom as a source to Synaptic gives the same error and the disk checks ok. This problem has been posted a number of times as far back as Hoary with no good solution that I can find.

---

### Post by kuja on 2007-05-01
Try using apt-cdrom add, then apt-get update, apt-get dist-upgrade, instead.

---

### Post by vitalik on 2007-05-01
> **kuja said:**
> Try using apt-cdrom add, then apt-get update, apt-get dist-upgrade, instead.

Hello. What do you mean by upgrading from generic. If you mean from 32 bit to 64 bit, then the answer is no. You will have to do a clean install for 64 bit.

---

### Post by nicklogan on 2007-05-02
Yes, I already have Feisty generic 32 bit and want to go to AMD 64 bit (actually with SMP as it's a dual Opteron system) - thanks for saving me a lot of time. I guess I need to do a re-install.

---

