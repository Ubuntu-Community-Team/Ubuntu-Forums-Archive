---
title: "Xewn 3.0.2 windows"
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by sles on 2006-08-08
Hello! 

Do somebody installed windows in xen?

get following error during creation:

root@dm:~# xm create -c /etc/xen/winXP128
Using config file "/etc/xen/winXP128".
Started domain WinXP128
xenconsole: Could not read tty from store: No such file or directory


I looked to /var/log
and see in qemu log

/usr/lib/xen/bin/qemu-dm: invalid option -- '-vnc'


Is there any way to fix this?

---

### Post by siamvps on 2006-08-27
I have the same problem too. Mine is debian amd64 sarge. Is the problem related to vncserver on x86_64 environment? I am not if we have to get vncserver configured before running HVM or not. Has anybody get it fixed yet?

---

