---
title: "nvidia 8600 + 3d accel + driver from nvidia site"
date: 2007-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fittersman on 2007-08-19
well, it seems like a maze to me with this nvidia driver, i cant do it in recovery mode because im not on the right level of some sort, so i have to type in somthting to get me on level 3, but once i get on level 3 the x server starts up and its like im in normal mode again, but the driver installation must be run when x isnt running.

how can i get x not running but still be on level 3? (if you know what im trying to say here)

is there a command for the command line that is like stopx or something? (instead of startx)

o yeah, and im running on 7.10

---

### Post by Sockerdrickan on 2007-08-19
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

---

