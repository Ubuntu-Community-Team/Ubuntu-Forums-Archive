---
title: "Wine logs ubuntu out"
date: 2007-12-18
forum: Wine
---

### Post by Nate53085 on 2007-12-18
I am running Gusty.

Updated to the newest wine.  When I go to run wine or any application through wine, it logs me out of Ubuntu.

I believe I narrowed it down to my nvidia driver.  I remove nvidia-glx-new and it works ok.

I read somewhere on the forums that usually this was due to a kernel update causing a driver mismatch but I have reinstalled the nvidia driver with both the restricted drivers manager and with envy with no success.

Any help would be greatly appreciated.

Thank you.

**Edit**
I also wanted to note that keeping nvidia-glx uninstalled is not really a solution as I'm trying to get Steam running in wine so I can play portal

---

### Post by cogadh on 2007-12-19
Chances are, it is not actually logging you out (Wine does not have that ability), but it is actually restarting the X server, which will bring you back to the GDM/KDM prompt. You will need to get the Nvidia restricted driver working in order to get Wine functional. Unfortunately, the fact that you have used multiple install methods including Envy may have polluted the system a bit and could make this difficult. Your best bet is to use the default restricted driver. If just enabling the driver doesn't seem to work, then you might try following the old Nvidia how-to:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

It was written for Ubuntu Feisty, but all of the info still applies to Gutsy.

---

