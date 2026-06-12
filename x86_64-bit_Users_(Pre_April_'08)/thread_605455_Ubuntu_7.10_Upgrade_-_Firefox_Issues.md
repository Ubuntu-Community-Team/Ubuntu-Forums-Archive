---
title: "Ubuntu 7.10 Upgrade - Firefox Issues"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sxjast on 2007-11-07
Hello,

Yesterday I upgraded my current ubuntu installation with 7.10 which I wish I didn't do it. After that my firefox started giving problems. If I open gmail or yahoo mail, it stucks forever. If I open CNN, it comes up. Looks like something is seriously wrong. 

Using Synaptic package manager, I completely removed and reinstalled it which also didn't help. Does any one have any ideas on how to fix my firefox? I'm using 64 bit processor.

Thanks,
sxjast

---

### Post by azbarcea on 2007-11-09
hi

> 
Using Synaptic package manager, I completely removed and reinstalled it which also didn't help. Does any one have any ideas on how to fix my firefox? I'm using 64 bit processor.


Probably the settings you had for firefox do not match the next version of firefox ... plugins usual are the source of this issue. I recomand:

```

sudo apt-get remove -y firefox
sudo apt-get autoremove
rm -r ./mozilla/firefox
sudo apt-get install firefox

```

bye

---

### Post by sxjast on 2007-11-12
Thank you very much. It did work.

---

