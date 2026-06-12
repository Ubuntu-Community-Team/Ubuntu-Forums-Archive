---
title: "Serious problems"
date: 2007-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by phelixnyc on 2007-10-15
I just uninstalled nvidia driver's which I installed using Envy, now I get x-server error message when I boot. I also get this error "mounting local filesystem, mount special device /dev/hda1 does not exist". Is there any way to fix this

---

### Post by dabl on 2007-10-15
> **phelixnyc said:**
> I just uninstalled nvidia driver's which I installed using Envy



Exactly how did you do that -- did you use Envy to remove the driver?  What did you install or configure to replace the Nvidia driver?

You should be able to configure a basic VESA display using the ```
sudo dpkg-reconfigure xserver-xorg 
```script. If the Nvidia driver doesn't work, tell it to use the "VESA" driver.  :)

---

