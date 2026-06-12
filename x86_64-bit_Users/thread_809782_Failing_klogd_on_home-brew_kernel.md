---
title: "Failing klogd on home-brew kernel"
date: 2008-05-27
forum: x86 64-bit Users
---

### Post by Alexis Phoenix on 2008-05-27
Another of those strange things I can't figure out...

I've been trying to boot a 2.6.24.4 kernel from kernel.org source, using a well tested and working configuration.  Things work until it gets to "Starting kernel logger...".  Then it stops booting, however after a 5 minute timeout it continues with the [FAIL] for the logger.  A look over syslog reveals the following:
May 25 21:51:00 tomkitten kernel: Symbols match kernel version 2.6.24.
May 25 21:51:00 tomkitten kernel: No module symbols loaded - kernel modules not enabled
which is just before the kernel logger tries to start.

This on a Dell Inspiron 1501 with dual core AMD Turion 64bit.

Does anyone have any suggestions as to how I can fix this?

Thanks in advance
Alexis Phoenix

---

