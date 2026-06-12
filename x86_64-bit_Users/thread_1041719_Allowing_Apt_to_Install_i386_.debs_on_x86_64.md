---
title: "Allowing Apt to Install i386 .debs on x86_64"
date: 2009-01-16
forum: x86 64-bit Users
---

### Post by Mogigoma on 2009-01-16
I have a Ubuntu machine that is x86_64, and there is a repository of software ([http://paparazzi.enac.fr/ubuntu/](http://paparazzi.enac.fr/ubuntu/)) I wish to access. Sadly, this repo has packages for i386 almost exclusively.

Currently, I have the following line in my sources.list:
```
deb http://paparazzi.enac.fr/ubuntu/dists/ intrepid/main/binary-i386/
``` But this approach, while allowing me to see the single package listed for 'all' architectures, doesn't let me install the i386 software that I require.

Is there a way to force Apt to display/recognize/allow the installation of these packages through apt-get/synaptic without some crazy method of downloading the .debs manually and forcibly installing them through dpkg, etc.?

Any help would be appreciated.

---

### Post by Kilz on 2009-01-17
> **Mogigoma said:**
> I have a Ubuntu machine that is x86_64, and there is a repository of software ([http://paparazzi.enac.fr/ubuntu/](http://paparazzi.enac.fr/ubuntu/)) I wish to access. Sadly, this repo has packages for i386 almost exclusively.

Currently, I have the following line in my sources.list:
```
deb http://paparazzi.enac.fr/ubuntu/dists/ intrepid/main/binary-i386/
``` But this approach, while allowing me to see the single package listed for 'all' architectures, doesn't let me install the i386 software that I require.

Is there a way to force Apt to display/recognize/allow the installation of these packages through apt-get/synaptic without some crazy method of downloading the .debs manually and forcibly installing them through dpkg, etc.?

Any help would be appreciated.

Even if you could, you may not want to. The reason is that libraries would be then automatically force installed. If that library is one your 64bit system needs you will get instability and most likely a crash. One that there is no restarting from, unless you call a wipe and reinstall restarting.
Better to use getlibs.

---

