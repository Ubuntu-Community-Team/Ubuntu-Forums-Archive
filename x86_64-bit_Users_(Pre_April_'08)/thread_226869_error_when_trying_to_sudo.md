---
title: "error when trying to sudo"
date: 2006-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by PoisoN2003 on 2006-07-31
i get an error each time i try to become root

```
poison@poison-desktop:~$ sudo dpkg -i /home/poison/Desktop/cedega-small_5.2.3_all.deb
sudo: unable to lookup poison-desktop via gethostbyname()

```

---

### Post by McMarley on 2006-07-31
try becoming superuser and then perform the action:

su

then give it you password and try again

---

### Post by juicemansam on 2006-08-01
> **PoisoN2003 said:**
> i get an error each time i try to become root

```
poison@poison-desktop:~$ sudo dpkg -i /home/poison/Desktop/cedega-small_5.2.3_all.deb
sudo: unable to lookup poison-desktop via gethostbyname()

```

Check that your /etc/hosts file has an entry with either```
127.0.0.1 localhost <hostname>
``` or ```
<ip address> <fully qualified hostname> <hostname>
```
I know I'm not really clear, so post back. Also, if you cannot get root access becasue root doesn't have a password, and booting in single user mode ("recovery") doesn't work because of the same problem, you can always boot the kernel with "init=/bin/bash" appended to the kernel command line. If you do the kernel command line part, you'll have to remember to remount the root partition (or the one that contains /etc/hosts) with read-write access, then remount it as read-only, and press the reset button to restart. It's a semi-complicated process, so post back for more details if that's your final option.

---

### Post by PoisoN2003 on 2006-08-01
i think it is the hosts thing coz i rewrote the hosts file when i was doing the block ads/popups so ill try that and reply here

---

