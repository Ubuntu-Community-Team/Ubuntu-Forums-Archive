---
title: "user account migration from REHAT FEDORA CORE 5 to UBUNTU AMD 64 BIT 7.04 server"
date: 2007-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by raghavendra on 2007-05-07
We have installed a REDHAT FEDORA CORE 5  server as a proxy and content filter server.  we are running squid proxy server and Dansguardian Content filter, for Squid Authentication we are using local Linux accounts with  PAM authentication. This works fine.

We saw the benefits of a Ubuntu Server and now installed SQUID and DANSGUARDIAN  but we are faced with a major hurdle w.r.t authentication. we  want  to migrate all the local user accounts and passwords from the Fedora Server into the ubuntu AMD 64 Bit 7.04 server 

We googled and got a procedure for the same 

[http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server]("http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server") 

from the above link we were successful to run the commands on the old server but when we tried the commands on the new Ubuntu server we were stopped

When we tried to execute the command 

cat passwd.mig >> /etc/passwd

we get a permission denied message

We tried changing the permissions but to no avail, We are new to Ubuntu File Security, we would be obliged  if someone could help us on this pls

---

### Post by dfreer on 2007-05-07
surely you ran this as root? as in:
sudo cat passwd.mig >> /etc/passwd

---

### Post by raghavendra on 2007-05-07
we have already tried this please

---

### Post by rai4shu2 on 2007-05-07
Maybe this:

sudo -i
cat passwd.mig >> /etc/passwd

---

### Post by raghavendra on 2007-05-07
rai4shu2


thanks lot now it is working

---

