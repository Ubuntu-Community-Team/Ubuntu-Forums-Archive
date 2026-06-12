---
title: "Messages log - what is this?"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by amstel78 on 2006-01-15
Found this entry in my messages log:

**Jan 15 13:23:19 localhost -- MARK -- **

Can someone tell me what this is?

---

### Post by [Rui] on 2006-01-15
It's a mark, like the string says :) It's meant to show you that syslog is really running.

From man syslog:
>        -m interval
              The syslogd logs a mark timestamp regularly.  The default interval between two -- MARK -- lines is 20  minutes.   This  can  be  changed  with  this option.  Setting the interval to zero turns it off entirely.


By default syslogd marks every 20 minutes.

---

