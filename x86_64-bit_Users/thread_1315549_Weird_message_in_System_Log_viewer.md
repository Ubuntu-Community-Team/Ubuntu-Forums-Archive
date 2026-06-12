---
title: "Weird message in System Log viewer"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by whoop on 2009-11-05
When I start System Log viewer I always get this (slightly) concerning message:

```

Could not open the following files:
/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory
/var/log/user.log.0: Error stating file '/var/log/user.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/btmp: You don't have enough permissions to read the file.

```

I do not get this on any other machines. 
Any ideas?

---

### Post by dcstar on 2009-11-06
> **whoop said:**
> When I start System Log viewer I always get this (slightly) concerning message:

```

Could not open the following files:
/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory
/var/log/user.log.0: Error stating file '/var/log/user.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/btmp: You don't have enough permissions to read the file.

```

I do not get this on any other machines. 
Any ideas?

Do these files actually exist?

---

### Post by whoop on 2009-11-06
> **dcstar said:**
> Do these files actually exist?

No, they don't exist on this system. In fact, they don't exist on other of my systems as well. But then the question is, why does the application complain about this on one of my ubuntu installs?

---

