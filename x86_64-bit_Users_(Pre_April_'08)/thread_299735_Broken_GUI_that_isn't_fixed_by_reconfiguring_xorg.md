---
title: "Broken GUI that isn't fixed by reconfiguring xorg"
date: 2006-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by spacepirates on 2006-11-14
So i recently tried to install and use Beryl with the latest NVIDIA drivers (version 9629), however my system crashed.

The GUI broke, so i tried to reload my backed up xorg.conf files, but that didn't work. I tried uninstalling the nvidia drivers, reinstalling the old ones (in the repos), and reconfiguring a new xorg.conf file. nothing has worked.

any ideas?

thanks.

---

### Post by kuja on 2006-11-14
To properly reconfigure the xorg config file when using the proprietary nvidia drivers, use the nvidia-xconfig command.

```
sudo nvidia-xconfig
```

---

