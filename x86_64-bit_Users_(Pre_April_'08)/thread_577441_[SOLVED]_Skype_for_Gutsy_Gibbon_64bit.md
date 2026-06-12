---
title: "[SOLVED] Skype for Gutsy Gibbon 64bit"
date: 2007-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Baby Boy on 2007-10-16
How do I install Skype in Gutsy 64 bit? Only the 32bit version is available.

---

### Post by John.Michael.Kane on 2007-10-16
> **Baby Boy said:**
> How do I install Skype in Gutsy 64 bit? Only the 32bit version is available.
You can try this.
[How to: Install Skype]("http://ubuntuforums.org/showthread.php?t=432295&highlight=skype")

---

### Post by Baby Boy on 2007-10-16
Thanks,  I managed to install it and run it. I haven't tried to actually talk/chat to anyone yet, but I think it will work. :)

---

### Post by ViRMiN on 2007-10-16
Cappy's "getlibs" script works a charm for installing the 32-bit libraries that Skype depends on.  You have to do a force-architecture install on Skype, and then run getlibs against the Skype binary.

---

### Post by dmjones500 on 2007-10-19
> **ViRMiN said:**
> Cappy's "getlibs" script works a charm for installing the 32-bit libraries that Skype depends on.  You have to do a force-architecture install on Skype, and then run getlibs against the Skype binary.
I agree, the getlibs route is the best way to do skype IMO.

See [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) for instructions on how to get the getlibs program, and an example that actually includes skye.

---

