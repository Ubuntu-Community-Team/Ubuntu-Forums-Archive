---
title: "nvidia driver dilemma"
date: 2007-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by nate_nightroad on 2007-05-29
hi i downloaded the nvidia driver for my graphic card and i run it at xserver, the installer told me to exit x server to install...then i start ubuntu 7.04 at the recovery mode to install but it halts and says tat i require to have runlevel 3 to install...

as far as i know, if i runlevel 3 i will enter into xserver mode again...so wat should i do?

thanks for the time and have a nice day

---

### Post by Tanker Bob on 2007-05-29
Change to run level 3, then as the system starts loading hit CTRL-C to stop the loading script.  That worked for me.  If you don't get it on the first try, give it another shot.  Success probability on any one attempt decreases as the speed of your PC increases.  Although, I have also installed the NVIDIA drivers without changing to level 3 and did not have any problems.

---

### Post by nate_nightroad on 2007-05-29
i tried to install without level 3 but fails...it says my kernel does not match or something....

---

### Post by Tanker Bob on 2007-05-29
Hmmm, doesn't sound like a level 3 issue.  You may already have a driver installed.  If you installed the drivers from the repositories, uninstall those first.  Then I'd recommend using the Envy script, 0.92 or newer, and first telling it to uninstall the nvidia drivers, then use Envy to install them from scratch.

---

### Post by gbesso on 2007-05-29
I always install by just booting normally, then switching to a terminal (Ctrl+Alt+F1) and then: 
```
sudo /etc/init.d/gdm stop
```
or for Kubuntu:
```
sudo /etc/init.d/kdm stop
```
Then just run the installer normally, when it finishes do
```
sudo /etc/init.d/gdm restart
```
or for Kubuntu:
```
sudo /etc/init.d/kdm restart
```
to restart the x server.
Note: you might have to click ctrl+alt+f7 to go back to X

As for the kernel thing, make sure you have the build-essential and linux-headers packages installed
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by Cappy on 2007-05-29
DO NOT INSTALL THE DRIVERS FROM THE NVIDIA SITE. The drivers have to compile on your system and they do not work nearly as well as the precompiled drivers in the repos. I've [personally] found the performance from these drivers on games to be very jerky.

If you goto (System-->Administration-->Restricted Drivers Manager) it should automatically be able to install drivers if you check the "enabled" box. That's all you need to do.

---

### Post by nate_nightroad on 2007-05-30
hi.i downloaded envy and the problem is solved....is so automated tat is simple..dont even have to stop X to do it....

many thanks to tanker bob for helping me...anyway thanks again for all the ppl tat spent time reading my thread and helping me out

---

