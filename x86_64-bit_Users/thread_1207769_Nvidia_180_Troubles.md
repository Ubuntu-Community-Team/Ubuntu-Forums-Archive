---
title: "Nvidia 180 Troubles"
date: 2009-07-08
forum: x86 64-bit Users
---

### Post by 02c3n on 2009-07-08
I've installed ubuntu on my amd x2 6400+ Black edition with 2x 9600GT's and when i went to install the Nvidia 180 Drivers the GUI won't load on restart. anyone know what i'm doing wrong? when the prompt loads up it asks for a hive login so i'll login and then i dont know what to do i tried reading into it a little but i've come up empty handed.

---

### Post by philinux on 2009-07-08
Sounds like something got messed up.

Boot up and press esc at grub.

Choose the recovery mode option.

At the recovery menu choose xfix then after that resume normal boot.

---

### Post by cariboo on 2009-07-08
I had a similar problem when I reinstalled Karmic alpha2 yesterday. The solution for me was to start in recovery mode and completely remove /etc/X11/xorg.conf, then restart without an xorg.conf file. Once I was back at the desktop, I just enabled the restricted drivers and all was ok.

---

### Post by 02c3n on 2009-07-08
alright i've tried everything that you guys said and it still gives me the Kinit: "No Resume Image, Doing normal boot", then when i uninstall the drivers it loads the GUI again ....

---

### Post by dagrump on 2009-07-08
Are the video cards in SLI? 
If so look for "GUI doesn't load after installing nvidia drivers." That thread might fix you up.

---

