---
title: "Can't get to X on first boot"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jaripetteri on 2005-10-27
I have following hw setup:

- AMD64 3200+
- Abit KN8 Ultra
- 2x Kingston DDR400/512MB's
- Saphire x550 PCI-e
- Eizo L550 TFT
- Hauppauge Nova-T WinTV PCI
- 1x Samsung 160GB PATA as boot and backup
- 4x Samsung 250GB SATA's on RAID5

I'm building fileserver with MythTV and also adding someother services with Breezy but now I can't even get x running. After installation on the first boot I get message that graphic card is not found or miss configured. Even the login screen does not show up. Straight to the console login. I have tried everything I can think off to get x running. 

I have given a try with Ati and Vesa drivers, without Nova-T, with only one memory and even tried the x86 installation. no go... also used memtest and no errors there. Live does not help but Knoppix was able to get up with no errors so HW should work. Right?

Now I'm getting quite desperate. Any idea what I'm missing here?

---

### Post by RAOF on 2005-10-27
We can't really help you very well without knowing the precise problem, and that's much easier to work out if you post the exact error messages.  Could you post the contents of the xorg log (it's /var/log/xorg.log.0, or something similar) and possibly the contents of your xorg.conf (/etc/X11/xorg.conf)?

---

### Post by jaripetteri on 2005-10-27
heh... I need to learn to read those log files... problem solved wrong horisontal frequency on monitor configurations. Now its working, thanks for the tip... :)

---

