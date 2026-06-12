---
title: "sudo = segfault error 6"
date: 2008-04-21
forum: x86 64-bit Users
---

### Post by vagrahb on 2008-04-21
I updated to hardy heron from gusty and when I did a reboot to the new system
I cannot log into gnome as it tells me that my session lasted less than 10 seconds and logs me out. when I log in with a kde session and if I try to do anything with sudo I get a segfault

output of /var/log/messages
sudo[9036]:segfault at 00007fffa0981db8 rip 00002b010a012c4f rsp oooo7ffa0981dc0 error 6
[http://www.uluga.ubuntuforums.org/index.php](http://www.uluga.ubuntuforums.org/index.php)
I get the same error 6 for gnome-settings aswell.

I am stuck with a broken update and cannot revert back to my old working system. The internet is also not working.

Any help to fix this problem would be great.

thanks

---

### Post by Tom Mann on 2008-04-22
This reminds me of the libc6 breakage we had earlier down the line in the Gutsy beta... I hope it's not for your sake.

Details here:
[http://ubuntuforums.org/showthread.php?t=722886]("http://ubuntuforums.org/showthread.php?t=722886")

---

### Post by Sense on 2008-04-22
I think it's worth a shot to report this at Launchpad. Would you please be so kind to go to [http://bugs.launchpad.net/ubuntu](http://bugs.launchpad.net/ubuntu) and report it? Sudo shouldn't crash and unless you've replaced binaries with self-compiled or manually downloaded ones it's a bug.

---

### Post by Remanifest on 2008-04-28
I've got the same issue with sudo segfaulting.  No resolution as of yet...  [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/220483](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/220483)

---

