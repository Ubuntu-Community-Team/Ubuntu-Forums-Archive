---
title: "Alternate cd upgrade 9.04 -&gt; 9.10 not working"
date: 2009-10-31
forum: x86 64-bit Users
---

### Post by shishka on 2009-10-31
Downloaded alternate CD of 9.10, attempted to upgrade by mounting the ISO.

first of all, nothing pops up asking me to upgrade after mounting. but even running

$ sudo /media/cdrom/cdromupgrade

(or, for that matter, alt+f2 and entering "gksu "sh /media/cdrom/cdromupgrade" as advised)

only only tries to connect to the internet, as if I had opted to do the network upgrade via the update manager. i've tried this connected to the internet and not, either way gets this result.

i'd do the network upgrade, but i don't have internet currently and can't sit in an inet cafe for 12 hours.

at first i tried to do the net upgrade, then had to cancel. would this be the problem?

so the problem is that the alternate cd seems to be trying to run the network upgrade, which is exactly what i'm trying to avoid right now.

any help is appreciated,

thanks!

---

