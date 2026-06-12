---
title: "sudo commands are producing nothing"
date: 2007-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by rouggio on 2007-04-02
hi folks,

something very odd is happening here on a fresh installation of ubuntu server 6.10 on a AMD 64 bit dual core box:

no matter which command I try to execute with sudo, it produces no effect!

for example, "ls" produces a non empty list, while sudo ls just returns the prompt. 
No error message at all is displayed.

I am a bit confused... any ideas?

---

### Post by John Jason Jordan on 2007-04-02
> **rouggio said:**
> hi folks,

something very odd is happening here on a fresh installation of ubuntu server 6.10 on a AMD 64 bit dual core box:

no matter which command I try to execute with sudo, it produces no effect!

for example, "ls" produces a non empty list, while sudo ls just returns the prompt. 
No error message at all is displayed.

I am a bit confused... any ideas?
The first time you do sudo it should prompt for the root password. Thereafter it does not need the password until after a period of time has elapsed. Sudo is normally used to run a command as root, so if you just type "sudo" without a command after it, it will do nothing.

---

### Post by yabbadabbadont on 2007-04-02
What happens if you run: ```
sudo -s -H
```  Does it drop you to a root prompt?  If so, can you run commands then that work as expected?

---

### Post by rouggio on 2007-04-02
Hi John,

I tried your suggestion, here is the trace:

```


login as: dario
dario@openguild's password:
Linux openguild 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Mon Apr  2 21:07:02 2007 from 192.168.1.5
dario@openguild:~$ ls
SugarWorkshop  wiki
dario@openguild:~$ sudo ls
dario@openguild:~$ sudo -s -H
dario@openguild:~$ ls
SugarWorkshop  wiki
dario@openguild:~$ sudo pwd
dario@openguild:~$


```

I am stuck.

---

### Post by rouggio on 2007-04-02
It seems that the only thing I am able to do as root is to reboot with the CTRL-ALT-DEL sequence from the server itself.

I accessed the root file system with the rescue CD and I could perform some root operations, but when I get back to normal mode the behavior is the same :confused: 

Any help very appreciated!

---

### Post by rouggio on 2007-04-02
Ok ok... I have solved...


...and it was a very silly error I did! shame on me.

I unadvertently removed my only non-root user from the admin group. 

This caused the removal from the sudoers list as well.. and that's where the troubles start.

The solution is simple:

 - restart the system from CD in rescue mode, you'll enter a shell with root privileges - no need for password

 - adduser <myuser> admin

 - reboot - that's it!

sooo dumb! at least I hope somebody could find this useful.

Ciao!

---

