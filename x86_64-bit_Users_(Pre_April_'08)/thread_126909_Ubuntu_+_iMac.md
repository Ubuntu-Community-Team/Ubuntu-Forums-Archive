---
title: "Ubuntu + iMac"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by xkenneth on 2006-02-07
Hello all,

   I've just got Ubuntu installed on my iMac (this model: [http://www.everymac.com/systems/apple/imac/stats/imac_600_graphite.html](http://www.everymac.com/systems/apple/imac/stats/imac_600_graphite.html)) and i'm having some problems with it. I'm fairly experienced with linux on x86 and i've done a PPC before, but didn't stick with it for very long. I moved to Ubuntu because a friend recommended it (used to use SUSE.) The problem i'm having is i've done the normal install, entered all of the setup parameters as to what seemed fairly straightforward and got the thing to boot. Now i've done this twice and i've had the same problem both times. What happens is that the OS will boot just fine, and allow you to login. No once you enter a user/pass and login, the system becomes unuseably slow if not dead. It takes about 15-20minutes for the desktop to finish loading. I apologize if this is a common problem and I missed the solution. Any help would be appreciated.

Regards,
Ken

---

### Post by linear on 2006-02-07
You need to disable dri in xorg.conf. (Comment out the 'load "dri"' line in the Modules section.)

A more detailed set of instructions, covering other problems you don't have, here:

[http://ubuntuforums.org/showpost.php?p=642271&postcount=2]("http://ubuntuforums.org/showpost.php?p=642271&postcount=2")

---

