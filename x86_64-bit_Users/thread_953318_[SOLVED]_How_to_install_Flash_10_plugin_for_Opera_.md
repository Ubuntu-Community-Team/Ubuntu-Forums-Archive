---
title: "[SOLVED] How to install Flash 10 plugin for Opera 9.60?"
date: 2008-10-20
forum: x86 64-bit Users
---

### Post by PC_load_letter on 2008-10-20
Title is self explanatory. I already installed Flash 10 player for FF with success using a script I found at Ubuntugeek.com, the script only works for FF. I upgraded Opera to the latest version but still no luck. I am running Ubuntu amd64 8.04.

Thanks.

---

### Post by TenPlus1 on 2008-10-20
In Opera, goto Tools -> Preferences -> Advanced (tab) -> Content -> Plugin Options (button) -> Change Path (button) and add one of these (depending on flash plugin you have):

/usr/lib/adobe-flashplugin   (make sure it's ticked)
/usr/lib/flash-nonfree

That'll add the flash plugin for Opera and work thereafter...

---

### Post by PC_load_letter on 2008-10-20
Thanks man. I didn't imagine it was that easy, worked like a charm.

---

### Post by razer22 on 2008-11-02
hi cant this to work whith opera 9.62.:confused:

---

### Post by nss0000 on 2008-11-02
For geeks only. Actually un-doably difficult without pre-established paths. But, nice try. Why Opera doesn't identify/search/go-fetch by itself is the real issue. It's not 2001.

---

### Post by henwyn on 2008-11-04
> **nss0000 said:**
> For geeks only. Actually un-doably difficult without pre-established paths. But, nice try. Why Opera doesn't identify/search/go-fetch by itself is the real issue. It's not 2001.
Opera 9.62 reports that it cannot find operapluginwrapper which is/should be part of the installation. The paths are already there and checked but it can't install/use plugins. Reinstalling doesn't help. 
Okay, on my copy of Opera 9.62 installed on Ubuntu 8.10 64-bit, Opera was looking for the operapluginwrapper in /usr/lib/Opera/9.6_0_ rather than ./9.62. Putting in a link in the above mentioned configuration section eliminated an error message but did not solve the problem for me. I'm checking further; will report back if I find anything.

---

### Post by razer22 on 2008-11-04
thanks for looking in to this.:)

---

### Post by linuxvacuum on 2009-02-14
Works great in Opera 10 alpha too!

---

