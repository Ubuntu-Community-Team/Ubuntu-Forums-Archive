---
title: "Normal vs Recovery"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by k8bebop on 2007-05-02
What else gets loaded when you run Normal mode.

I am thinking, that something else must load because my keyboard & mouse stops working. Plus, if I start gdm at the command prompt, I get a error message saying "failed to initialize HAL"

Thanks

---

### Post by dannyboy79 on 2007-05-02
check out this bug report and you should get this resolved. good luck

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/24029](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/24029)

---

### Post by k8bebop on 2007-05-02
I figured out my problem and it didn't have to do with that bug per se. I was running gdm thru single mode. In single mode alot of the stuff that starts doesn't get started.

I figured this out when, since I couldn't get the keyboard to work, I might as well try to figure out my video problems. I started to reinstall NVIDIA-Linux_x96_64-100.14.03-pkg0.run, when it told me I should be in init 3. So I changed to that, and saw that Bluetooth services were running.

---

