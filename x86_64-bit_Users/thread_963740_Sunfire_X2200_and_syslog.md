---
title: "Sunfire X2200 and syslog"
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by KaneHau on 2008-10-30
Aloha:

I am running a Sunfire X2200 server (AMD) running Ubuntu 8.0.4 64 bit server edition.

I've modified my syslog.conf file to send all messages to a user named "bob" as such:

*.*                    bob

The above line *should* send ALL syslog messages to the user named 'bob'.  When I restart syslogd, 'bob' indeed sees the restart message appear on his terminal - but that's it... no other messages ever appear to user bob, even though things are being written to syslog, and other log files.  Rebooting doesn't help, trying other user names doesn't help.

I've the same configuration on other (solaris) systems and it works fine.

Can anyone else with a X2200 server confirm this for me please, or offer a fix?

Thanks!

---

