---
title: "Suse Linux Problem"
date: 2008-02-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by someth on 2008-02-12
Hi anybody can help me?
I have a running postfix working with mailscanner+spamassassin and clamav on my suse linux professional 9.1. recently my harddisk has only 500Mb space left, so I add new harddisk as /dev/sdb1 which is mounted to /var/spool/mailstores then I change my postfix config mail_spool_directory from /var/spool/mail to /var/spool/mailstores but an error occur when my user try to retrieve his mail, here it is: (server4 popper[14467]: luontean at 202.93.14.170 (202.93.14.170): -ERR [SYS/TEMP] Failed to create /var/mail/.luontean.pop with uid 1266, gid 0. Change permissions. [pop_dropcopy.c:1495]). my /var/mail has a simbolic link to /var/spool/mail

Im getting confused what is the relation between /var/mail and /var/spool/mail , y these two folder is linked?

please help

---

