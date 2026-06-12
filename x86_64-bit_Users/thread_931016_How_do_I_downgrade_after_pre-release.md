---
title: "How do I downgrade after pre-release"
date: 2008-09-26
forum: x86 64-bit Users
---

### Post by billstron on 2008-09-26
I'm on Ubuntu Hardy Heron.  After enabling the pre-release repository and upgrading, I now have all kinds of problems.  The first indication was that the new kernel broke my wifi.  I have since disabled the pre-release repo and downgraded my kernel.  Now I can't install octave and suspect that pre-release packages are to blame.  Is there any clean way of removing all of those pre-release packages?  


Thanks...

---

### Post by cariboo on 2008-09-26
To get rid of packages you no longer need you can use synaptic to completely remove a package (right click, select completely remove) or you can do it from the command line. If there are any servers that you intend to uninstall stop the service first then in a terminal:

```
sudo apt-get purge <packagename>
```

Where <packagename> is the name of the paackage you want to get rid of.

Jim

---

