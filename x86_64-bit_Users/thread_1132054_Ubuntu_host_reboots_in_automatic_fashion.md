---
title: "Ubuntu host reboots in automatic fashion"
date: 2009-04-21
forum: x86 64-bit Users
---

### Post by beagle197 on 2009-04-21
Folks,

My Hardy 8.04, x86_64 2.6.24-16-generic #1 SMP, Ubuntu host reboots almost every day for unknown reasons, but typically in the mornings around 7:40 am as strange as that sounds. Sometimes it reboots after leaving the system idle for a while (e.g. for lunch).  I don't see I have automatic updates set anywhere (of course I may be not looking in the right place). I looked briefly around log messages, changed passwords, but could not find a definite cause. Any ideas?

Thanks,
BEA

/var/log/messages

Apr 20 07:42:04 bea syslogd 1.5.0#1ubuntu1: restart.
Apr 20 07:55:59 bea -- MARK --
...
Apr 21 07:57:03 bea syslogd 1.5.0#1ubuntu1: restart.
Apr 21 08:15:59 bea -- MARK --

---

### Post by dabl on 2009-04-21
That sounds like a hardware problem.  Could be a thermal shutdown (are the fans all working?), a failing/intermittent power supply, RAM going flaky -- hard to tell. There's nothing about default Ubuntu Linux that automatically reboots a computer.

---

### Post by beagle197 on 2009-04-30
I removed the stack of papers littering the top of the 'puter. Also I updated to the latest for this release to see if that helps.

Thanks

bea@slice:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
bea@slice:~$

---

### Post by beagle197 on 2009-04-30
Is it possible to detect a thermal shutdown? e.g. if thermal shutdown was triggered, that a log report was saved.

Thanks

---

### Post by cariboo on 2009-04-30
Is your computer phyiscally restarting? The syslogd message is normal as the deamon needs to be restarted every day.

---

### Post by beagle197 on 2009-05-01
Yes it is physically restarting. Instead of unlocking the system and returning to my work of the previous day (e.g. open xterms, xchats, pidgin sessions, tora, etc), I return to my desk to have to login from scratch, with uptime reset.

---

