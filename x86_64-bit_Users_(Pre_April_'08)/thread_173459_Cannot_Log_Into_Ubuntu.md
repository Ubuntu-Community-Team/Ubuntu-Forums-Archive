---
title: "Cannot Log Into Ubuntu"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by veganrunner9 on 2006-05-10
Hello,
When I try to log into Ubuntu without the internet the desktop does not show up and the brownish screen just stays there. This problem does not happen if I have my ethernet cable attached. I am running Ubuntu on a iBook G3. Any advice would be greatly appreciated.
Thanks

---

### Post by glotz on 2006-05-10
This is kinda silly but your background picture wouldn't happen to be on the network? ;)

---

### Post by veganrunner9 on 2006-05-10
What do you mean by this?

---

### Post by linear on 2006-05-10
The symptom sounds like the [date bug]("https://wiki.ubuntu.com/UbuntuDateBug"), but I don't know why the network would make a difference...
 
(I mean, I think that Ubuntu attempts to sync to a time server, but never heard that this would affect the date bug.)

---

### Post by jdp on 2006-05-10
With the network cable attached, it could be properly syncing time with NTP, and with it detached it might be losing the date and showing the date bug.  Does this iBook have a dead main battery?  iBooks don't have PRAM batteries, so if the main battery dies you lose PRAM settings.

---

### Post by farruinn on 2006-05-11
Coincidentally I had this same exact problem just yesterday, only I didn't realize it was related to the date. Rebooting to OS X and allowing OS X to reset the date fixed it for me, but you should be able to resolve this by following the instructions at the [http://wiki.ubuntu.com/UbuntuDateBug]("http://wiki.ubuntu.com/UbuntuDateBug").
 
*glad to know why he couldn't get into Gnome yesterday :)*

---

