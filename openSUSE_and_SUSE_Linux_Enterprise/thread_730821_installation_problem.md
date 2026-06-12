---
title: "installation problem"
date: 2008-03-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by junaid.kollam on 2008-03-21
I installed open suse 10.3 with ubuntu(dual boot).But i could not log in.A black screen appieares when i boot into open suse.And blinking the power switch of lcd monitur.
Graphics card-ATI radeon xpress 200
Moniter-samsung SyncMaster 540N

---

### Post by 67GTA on 2008-03-22
Have you tried booting into failsafe mode? If you can get booted to a command prompt, we might be able to help you get it going. The first thing I would try is ```
sudo sax2
```. We need some kind of error to know where to start. Usually if you can boot into failsafe mode, it will spit errors at you.

---

### Post by junaid.kollam on 2008-03-23
i try sax2 but failed

---

### Post by 67GTA on 2008-03-23
Try running ```
sax2 -r -m 0=vesa
``` from failsafe to use the vesa driver in case the fglrx driver is causing issues. See if you can reboot into the desktop afterwards.

---

