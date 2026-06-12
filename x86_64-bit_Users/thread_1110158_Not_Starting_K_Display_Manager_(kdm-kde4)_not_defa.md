---
title: "Not Starting K Display Manager (kdm-kde4) not default display manager"
date: 2009-03-29
forum: x86 64-bit Users
---

### Post by westonwilson08 on 2009-03-29
I was trying to upgrade from Kubuntu 8.04 to 8.10 but keep getting errors and I have not been able to find a solution yet. after booting I get into ctrl-alt-f8 with error 

"grep: /usr/lib/kde4/kdm/kdmrc: No such file or directory
Not starting K Display Manager (kdm-kde4); it is not the default display manager."

When I go to tty1 and "startx" I get error

"Error: API mismatch: the NVIDIA kernel module has version 177.82, but this NVIDIA driver component has version 180.29. Please make sure that kernel module and all NVIDIA driver components have the same version
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for details.
*** Aborting ***"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/(user)/.Xauthority

BTW I have a Geforce 6600 GT
Sorry, I am new to this site so tell me any information you need to help.

---

### Post by 3Miro on 2009-03-29
KDE 3 to KDE 4 is such a big change that a clean install would have been a better option (perhaps).

Having said that, it looks like you have a mismatch fro the components of your nVidia driver that are installed. How did you install your driver in the first place, did you use the HW manager, or download it form nVidia.

Anyway, you can try to fix things from the shell, by typing:
> 
sudo dpkg -i nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180


I hope this helps.

---

