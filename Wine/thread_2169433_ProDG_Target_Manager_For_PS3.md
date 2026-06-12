---
title: "ProDG Target Manager For PS3"
date: 2013-08-22
forum: Wine
---

### Post by jay21 on 2013-08-22
Hi all,

Just wondering if anyone has successfully installed and run ProDG TM via wine?

I have had slight success with making the following changes followed up and found by other users elsewhere:

setcap cap_net_raw+epi /usr/bin/wine-preloader  <- This was changed because it was complaining about ICMP.

Second change was mentioned by another user which stopped the internal error from occuring:

/etc/sysctl.d/10-ptrace.conf <- Changing the value 1 to 0


Now I have it up and running though for some odd reason its not finding the target IP "MY PS3".

If anyone has a workaround or an idea as to what it could be it'd be much appreciated.

Thanks guys.

---

