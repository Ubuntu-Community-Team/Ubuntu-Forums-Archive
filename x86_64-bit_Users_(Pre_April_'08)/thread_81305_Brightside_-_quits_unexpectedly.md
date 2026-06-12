---
title: "Brightside - quits unexpectedly"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by pjs_flyer on 2005-10-24
Minor issue - when I shut down, a message comes up that Brightside has quit unexpectedly.  I close the dialog box, shutdown completes as normal.  More a niggle than anything critical, but as it's only just started happening I wondered if anyone had any ideas on how to sort it out.

Ta!

P

---

### Post by shooterae5 on 2005-11-02
I'm having the same problem, same results. I'm having these troubles on my Toshiba laptop but not on my e-machine desktop. any help would be welcome.

Shooter

---

### Post by michael_salcher on 2005-11-07
you need to disable gnome session managment when starting brightside. put 'brightside --sm-disable' into the gome startup applications.

you can see more brightside switches by typing 'brightside --help' on the command line (note that --disable-crash-dialog does not seem to solve the problem, but --sm-disable does).

---

