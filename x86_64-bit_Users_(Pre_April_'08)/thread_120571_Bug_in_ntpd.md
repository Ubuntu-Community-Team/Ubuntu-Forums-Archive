---
title: "Bug in ntpd?"
date: 2006-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ktindle on 2006-01-22
I have the network time protocol daemon running, which goes to ntp.ubuntulinux.org by default- and won't go anywhere else.

I have a stratum one ntp server running on the network with this machine, which I'd like to use.  Inserting a correct "server" stanza into /etc/ntp.conf is ignored.

Bug in the AMD64 version of ntpd?

---

### Post by ktindle on 2006-01-23
OK, first of all, I'm not running ntpd, because I'm only a client to an already existing (very good) ntp server.  Sorry about that.  I should have said "ntpdate" where I actually said "ntpd."

And, I found the /etc/default directory.  What /etc/ntp.conf does is unclear to me at this minute, but if you want to change to a different time server, you set the shell variable in /etc/default/ntpdate, and you are good to go.

---

