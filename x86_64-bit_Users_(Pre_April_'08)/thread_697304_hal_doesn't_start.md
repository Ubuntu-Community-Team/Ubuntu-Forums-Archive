---
title: "hal doesn't start"
date: 2008-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by clarknova on 2008-02-15
I recently did a clean reinstall, formatting all partitions except /home, and now hal is not starting.

There is no warning that hal has not started (I recently had gutsy x86 on a laptop that would give me a warning every time I logged in, "Failed to initialize HAL!".), but this computer is silent about it. gnome-power-manager doesn't run and the NetworkManager doesn't recognize any interfaces.

If I do "/etc/init.d/hal start" then all is well. I did "update-rc.d hal defaults" but it tells me the startup links already exist. How is it that I can start hal manually but it doesn't start automatically?

Any idea where to start troubleshooting this?

db

---

### Post by prince_niceguy on 2008-02-24
install sysv-rc-conf from synaptic.

now run the command as

```
sudo sysv-rc-conf
```

check what mark hal is having it should be 2,3,4,5. if iit is not there try reinstall hal from synaptic.

---

### Post by clarknova on 2008-03-11
Thanks for the suggestion. 2,3,4,5 were checked for hal, so I reinstalled hal. I won't be rebooting for a bit, but I'll post an update when it happens.

db

---

### Post by clarknova on 2008-03-17
I found the solution in a closed gutsy development thread ([http://ubuntuforums.org/showthread.php?p=3545464](http://ubuntuforums.org/showthread.php?p=3545464)) so I'm replying to it here for closure.

I too have concurrency=shell for faster booting on an SMP system. I renamed /etc/rc2.d/S12hal to /etc/rc2.d/S13hal and hal is now starting automatically at boot.

I wonder if this isn't worth creating a bug report, if one doesn't already exist. I'll have to check into it another day.

db

---

### Post by Yellow Pasque on 2008-03-17
There is a Launchpad Bug report for this. It's a common bug. I'm glad you found the solution ;P
Here: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881)

---

