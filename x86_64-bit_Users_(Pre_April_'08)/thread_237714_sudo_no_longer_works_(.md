---
title: "sudo no longer works :("
date: 2006-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by clevershark on 2006-08-16
I'm a Ubuntu newbie, but long-time Linux user.

I was having issues with sudo not working for certain things earlier (namely, changing the permissions on a directory), so I rebooted into single user mode and set a root password.

Now sudo has stopped working altogether, and most of the items in my System > Administration menu have disappeared entirely. Some of the few items that are left don't work either (I get the message "The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.")

Has anyone else had this happen? What could have gone wrong here? What can I do to remedy this problem?

Thanks,
TAE

---

### Post by aysiu on 2006-08-16
This may help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by clevershark on 2006-08-16
Fortunately I was able to tinker around the /etc/sudoers file as root and add my normal user to the admin group; that restored sudo.

---

