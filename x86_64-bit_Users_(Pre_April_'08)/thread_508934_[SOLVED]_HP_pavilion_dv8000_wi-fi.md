---
title: "[SOLVED] HP pavilion dv8000 wi-fi"
date: 2007-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by samexner on 2007-07-24
i used this guide: [http://ubuntuforums.org/showthread.php?t=504788](http://ubuntuforums.org/showthread.php?t=504788)
to set up wi-fi on someone else's laptop, a HP pavilion dv8000
i followed the instructions, just as they were said, and it detects my WPA network "imashoe" but when i try to connect to it with my key, it doesnt connect, and it goes back to using the wired connection. when i put my cursor over the network manager tray icon after i've given it the key, it says "Waiting for WPA network key" or something like that

can someone help?

---

### Post by samexner on 2007-07-24
yay!
solution!
restore the system back to the way it was (take bcm43xx off the blacklist, rename the driver back to normal, etc)
then...
open gnome-terminal, run "apt-get install bcm43xx-fwcutter", reboot, then open gnome-terminal
type "sudo modprobe bcm43xx"
then, you should be able to connect to your network

---

