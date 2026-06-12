---
title: "Problem with Xorg.conf"
date: 2005-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gavd on 2005-04-13
Having installed the 64bit version of Ubuntu I cannot actually start up in the window environment, only command line. Once I enter my login and password the screen hangs with a brown screen and a working mouse pointer but nothing else. I tried sudo dpkg -reconfigure -xserver-xorg (I think that was it) and when selecting the screen colour depth got an error that it was "possibly overwriting xorg.conf" and telling me where the back up was and then its back to the command line prompt.  I have tried reinstalling xorg and also tried to install xfree86 but that didn't work. 

Any ideas?

Thanks


gavd

---

### Post by erkki70 on 2005-04-13
Hi,
You should try again to reconfigure your X server but try to use the Nvidia driver not the Nv, this might help.
Though, I don't know what's your card but the same issue has been sometimes solved this way.

If they don't appear in the list you'll have to install them probably like this:
sudo apt-get install nvidia-glx nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

Hope this helps and good luck!
Cheers,
Erkki

---

### Post by gavd on 2005-04-13
Thanks, I'll try that when I get back home from work.


gavd

---

