---
title: "Nvidia restricted drivers"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by skivyg on 2009-05-06
I've just put 9.04 Jaunty Jackalope on my main rig (I've been running it on my laptop for quite a while now). It installs and runs fine until I activate the restricted Nvidia drivers.  I've tried the 180 and 170 drivers each time it tells me to reboot and it always ends up in the command line, with no Ubuntu GUI present.

I've tried Envy and the same things happens.  I'm running 2x Geforce 8800 in an SLI config.  

I've scoured the net up and down for ideas and none have worked so far.  If anybody has any suggestions please help me out.

Many Thanks

SKivyG

---

### Post by John.Michael.Kane on 2009-05-06
> **skivyg said:**
> I've just put 9.04 Jaunty Jackalope on my main rig (I've been running it on my laptop for quite a while now). It installs and runs fine until I activate the restricted Nvidia drivers.  I've tried the 180 and 170 drivers each time it tells me to reboot and it always ends up in the command line, with no Ubuntu GUI present.

I've tried Envy and the same things happens.  I'm running 2x Geforce 8800 in an SLI config.  

I've scoured the net up and down for ideas and none have worked so far.  If anybody has any suggestions please help me out.

Many Thanks

SKivyG

You can try the below method.

First remove Envy, also un-install any other drivers you may have tried to install.

Next backup your current xorg, and start with a clean xorg.conf using the command below.
```
dpkg-reconfigure -phigh xserver-xorg
```

Restart your machine.

Next install the 180 series driver. after which you can try one of the below commands.  

```
sudo nvidia-xconfig --sli=auto

sudo nvidia-xconfig --sli=on

sudo nvidia-xconfig --sli=AFR

```

The above should add the SLi option to your xorg.conf file, after that you can reboot your machine, and you should be golden.

---

### Post by skivyg on 2009-05-06
I tried that and no luck, I tried it again from a fresh install and still nothing, I'm ending up with it saying:

kinit: No resume image, doing normal boot...

Ubuntu 9.04 (computer name) tty1

and then it wants me to login, but no matter what I do I can't get the Ubuntu GUI to run.

SkivyG

---

### Post by AlecJ on 2009-05-06
> **skivyg said:**
> I tried that and no luck, I tried it again from a fresh install and still nothing, I'm ending up with it saying:

kinit: No resume image, doing normal boot...

Ubuntu 9.04 (computer name) tty1

and then it wants me to login, but no matter what I do I can't get the Ubuntu GUI to run.

SkivyG

I think this may help?
[http://ubuntuforums.org/showthread.php?t=1142976](http://ubuntuforums.org/showthread.php?t=1142976)

---

