---
title: "Blank screen after nvidia update."
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by n2oboost1 on 2008-04-25
I installed Ubuntu using Wubi today and everything went fine.  Afterwards, I opened a terminal and got the NVIDIA update.

```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
sudo reboot
```

Now, after Ubuntu goes through loading, it comes up to a black screen.  What do I need to do?

---

### Post by chebuntu on 2008-04-25
Hi there, I have the same problem.

Every time I boot up I have to choose recovery mode, then type "init 5" at the command prompt.

This takes you to login screen where you can login as normal.

There may be a better solution but I haven't gone looking - this works for me.

---

### Post by Unterseeboot_234 on 2008-04-26
Hey, AMD-64 at this end with Gutsy, nVidia GE7500. I've been holding off on Hardy until I have more time. I troll the forum boards.

Lots of enthusiasm from people using this following forum posting howto...

**[install nVidia]("http://ubuntuforums.org/showthread.php?t=596875")**

I will be trying the above when I get into tweaking. See if it helps you. Post back if it does.

cheers!

---

