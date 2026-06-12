---
title: "[SOLVED] boots until splash screen then nothing"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by gm04030276 on 2008-02-04
Hi, I had k/ubuntu 32bit installed and needed to upgrade to 64bit for some apps i wanted to run. Eventually convinced myself it wouldn't be to big a job, multiple HDD's mean all my data was on another drive, backed up all configs and got list of all installed packages.

Downloaded and tried to install from graphical installer....didn't like it
Downloaded and tried to install from text installer...worked!

However! when i tried to boot to standard login, it got passed GRUB and just sat there. Nothing happening. I tried booting to recovery mode thinking it might be ok with just upgrading everything from there, did so but still no standard login, not even splash screen.

* Tried reinstall
* Tried upgrading everything
* its not an xserver problem as i can run startx from recovery mode and it works fine

any thoughts anyone?!!?

thanks

---

### Post by Jouke74 on 2008-02-04
Do you have an Nvidia 8*00 card? Then please type "Blank Screen Nvidia" in search.

---

### Post by gm04030276 on 2008-02-04
Ok, the solution.

(means you don't get the splash screen but i like to see masses of console text flying up my screen anyway!)

Download and install x86_64bit alternate (naturally, cause this is what doesn;t work)
Boot to recovery mode
```

cd /boot/grub
pico/nano/vi/whatever-else-you-want-texteditor menu.list

```
delete ```
quiet splash
``` from the normal boot entry near the bottom
```
shutdown -r now
```

and there you go.

---

