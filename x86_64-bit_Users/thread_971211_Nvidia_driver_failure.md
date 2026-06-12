---
title: "Nvidia driver failure"
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by pneumonic81 on 2008-11-04
So i know this may have been asked already, but I am still dealing with this issue. I updated to the newest version of Ubuntu 64, but now my nvidia video card doesnt work properly. 

I can edit m xorg file to use the "nv" driver but of course I cant use my second monitor. I installed the 177.8 driver but it doesnt seem to work. 

It seems like it doesnt understand what driver im using when i have "nvidia" as the driver. It claims it cant find the package and that no screens are configured. 

Has anyone solved this problem, I really dont want to have to do a fresh install.

---

### Post by dabl on 2008-11-04
> **pneumonic81 said:**
> 

I can edit m xorg file to use the "nv" driver 



With the new X.org version, editing xorg.conf comes pretty close to a waste of your time.

I use the EnvyNG package to install the Nvidia driver.  You need to install envyng-core, then run "sudo envyng -t" after you've exited X and shut down the X server with ```
sudo /etc/init.d/gdm stop
```

Once the driver is installed, and before you restart X, run the nvidia xorg.conf configuration utility ```
sudo nvidia-xconfig
```

Then restart X.

---

### Post by TheSamurai on 2008-11-04
i will second the suggestion of EnvyNG. i use that along with TwinView for dual monitors and it works great... very easy solution for beginners too.

---

### Post by pneumonic81 on 2008-11-05
that did it, good work dabl!

---

