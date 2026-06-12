---
title: "cron running crontab problems"
date: 2007-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by outsider2222 on 2007-11-25
hi; i'm a 12 year Linux user, but can't get cron to work properly on 7.10 64bit ...
script runs directly from console , no evidence of any /var/log/cron* file ....
no evidence that cron actually executes anything in my crontab file :

cron seems to be running :
ps -edf | grep cron
root     12841     1  0 17:16 ?        00:00:00 /usr/sbin/cron

I've restarted cron service many times.. rebooted several times ....

my test crontab entry is:
25,35,45,55,05,15 *  * * *           /home/robert/xx_sh

[bob@oberon /home/robert]: more xx_sh
###!/bin/sh -f
/bin/ls /home/robert >> /home/robert/x.lis  (no x.lis ever created)

[bob@oberon /home/robert]: ls -alrt  xx_sh
-rwxrwxr-x 1 bob robert 58 2007-11-25 10:14 xx_sh

so what am i doing wrong ( I/m about to desert Ubuntu and move back to Mandriva/Red-Hat world), please help

---

### Post by chippy99 on 2007-11-25
Hi, this is not going to be a great help but I have just copied your program and run it on my system and it all works fine. So maybe there is some issue with cron, are you a member of the crontab group ?  Also look in /var/log/syslog, there should be an entry every time you edit your crontab file and each time it executes a job.

Good luck, John

---

### Post by outsider2222 on 2007-11-26
there is some evidence that cron tried running a job that i had commented out about 6 hours before (in other words cron it seemed to have an old copy of crontab in memory ??)

where is this crontab group ???

looks like a bug to me :(

---

### Post by outsider2222 on 2007-11-26
okay; it looks like a bug (adding a newline at end of file seems to get the simple "ls" script to work) . now to get the big stuff to work ..... 

[https://bugs.launchpad.net/ubuntu/+source/cron/+bug/73398](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/73398)

---

### Post by outsider2222 on 2007-11-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/cron/+bug/73398](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/73398) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **outsider2222 said:**
> okay; it looks like a bug (adding a newline at end of file seems to get the simple "ls" script to work) . now to get the big stuff to work ..... 

[https://bugs.launchpad.net/ubuntu/+source/cron/+bug/73398](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/73398)

just though i should make my solution visible to the developers , so they know there is a problem, i don't think most newbies would be able to solve this :mad:

---

