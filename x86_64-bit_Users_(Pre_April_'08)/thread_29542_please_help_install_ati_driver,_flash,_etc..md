---
title: "please help install ati driver, flash, etc."
date: 2005-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by pelikan on 2005-04-24
I'm new to Linux and am having trouble installing the ati driver for my x800 pro, java and flash.

For example, when I try this: 

sudo apt-get install xorg-driver-fglrx

I get this error: 

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

I have run apt-get update. 

Can anyone help?

Thanks.

---

### Post by dewey on 2005-04-27
Try commenting out the Marillat repos (Nerim), and run apt-get update again.

---

### Post by Robuis on 2005-04-28
I got the Ati drivers to work, you will need to follow this thread. [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

---

### Post by pelikan on 2005-04-28
Thanks for the link. It worked.

---

