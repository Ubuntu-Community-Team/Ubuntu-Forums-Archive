---
title: "Error messages during bootup"
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by teixidoj on 2009-04-23
Hi,

 I see what looks like 4 error messages while bootup, but it goes so fast that I am not able to read them. Is there a way to look at them after the OS boots up?

---

### Post by lensman3 on 2009-04-23
From a command line do:

"dmesg | more"

This should have the error messages.  Hit a space-bar to advance to the next screen.  Also look at the tail end of the "/var/log/messages" file.  It also should have any messages logged from the kernel during reboot/boot.

Hope this helps.

---

### Post by teixidoj on 2009-04-24
Thank you, this really helped.

John...

---

