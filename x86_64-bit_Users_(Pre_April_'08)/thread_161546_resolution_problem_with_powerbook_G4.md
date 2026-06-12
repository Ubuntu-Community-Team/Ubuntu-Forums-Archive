---
title: "resolution problem with powerbook G4"
date: 2006-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by wolfcub47 on 2006-04-17
hi, I've just installed ubuntu on my powerbook G4 with the following configuration, 500Mhz CPU, 512M RAM, 16M ATI Radeon M6 display card. Everything is working fine now, except there is only one display resolution which is 640x480, the powerbook works fine with MacOS Tiger. how can i  get a bigger and nicer resolution in ubuntu? should i download ATI driver for linux? Any suggestions?

---

### Post by Peter76 on 2006-04-17
type at the terminal:
sudo dpkg-reconfigure xserver-xorg
Follow instructions; most of the things you can leave at setting except of course for resolution configuration. When finished, reboot and, voila.
Could you please post how cdburning is working on your iBook?

---

### Post by wolfcub47 on 2006-04-17
sorry, since my notebook is an old one, it doesn't have a CD burner, so i didn't set anything with cd burning.

---

