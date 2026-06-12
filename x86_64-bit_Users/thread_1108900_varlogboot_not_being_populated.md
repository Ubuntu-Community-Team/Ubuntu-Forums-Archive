---
title: "/var/log/boot not being populated"
date: 2009-03-28
forum: x86 64-bit Users
---

### Post by oogie72 on 2009-03-28
Hi,

Lately on boot up, I've been noticing some extra text flashing by on the screen. I've been reading up in the forum on the boot log - /var/log/boot - and for the life of me, I cannot get it to populate.

I've read the threads on "enabling" boot time logging (*which is off by default? strange*), and enabled it as far as I know:

```
root@shrek:~# cat /etc/default/bootlogd 
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
```

But alas, even after many hot/cold reboots after above:

```
root@shrek:~# ls -l /var/log/boot
-rw-r----- 1 root adm 31 2008-10-29 18:05 /var/log/boot
root@shrek:~# 
root@shrek:~# cat /var/log/boot
(Nothing has been logged yet.)

```

Am I missing something in enabling it? Any thoughts or suggestions would be greatly appreciated.

Cheers!

```
root@shrek:~# uname -a
Linux shrek 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```

---

