---
title: "PowerCenter Pro 210: getting ubuntu on it!"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mac_Switcher on 2005-12-02
Please close this thread.

---

### Post by linear on 2005-12-02
[QUOTE=Mac_Switcher]Is the CPU a G3 or something older?[/QUOTE]

Older, I think. Wouldn't qualify as a "NewWorld" Mac.

---

### Post by Ptero-4 on 2005-12-02
Don't even think about torrenting off that one unless you upgrade that HD, that 2gig drive won't have space for a nail once you put ubuntu on it.

---

### Post by Mac_Switcher on 2005-12-02
Please close this thread.

---

### Post by xslf on 2005-12-03
> Is it still possible to run Ubuntu on it even though the CPU is pre-G3?

I understand that there are poeple who done it, although I never tried myself.
See here:
[http://www.applefritter.com/node/8936](http://www.applefritter.com/node/8936)

---

### Post by Mac_Switcher on 2005-12-03
Please close this thread.

---

### Post by Mac_Switcher on 2005-12-10
Please close this thread.

---

### Post by ristosu on 2005-12-10
You cannot run Linux from inside Mac OS, but the bootloader BootX is started from there. When started, Linux runs natively.

But you can run Mac OS from inside Linux with MOL (Mac-on-Linux). But I wouldn't try to start another Linux from there...

It is possible to boot Linux without Mac OS. There is a bootloader for OldWorld Macs called quik. It's not included in Ubuntu, but an available rpm package can be installed with alien command. This should be done while installing, before rebooting, which might be problematic.

I think you would need a 500 MB partition for Mac OS 9.2.2. Ubuntu should fit in 2 GB. And 128 MB RAM, I guess, is minimum.

---

### Post by Mac_Switcher on 2005-12-30
Please close this thread.

---

### Post by Mac_Switcher on 2006-01-01
Please close this thread.

---

### Post by jdp on 2006-01-02
Hi, I wrote that guide on Applefritter.  I haven't taken the time to try it out on other machines, but I do have the 7600/132 I want to test more and a Power Center PowerWave (120MHz 604) that I'd like to test some day too.

[QUOTE=Mac_Switcher]any distros like DSL that will run on this thing?[/QUOTE]

You might try the basic **server** install and try the xfce4 desktop by installing the right package.  I think it's **sudo apt-get install xubuntu-desktop** but I'm not positive which PPC repositories it'd be in.

---

