---
title: "brother MFC-420cn printer"
date: 2007-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by roberts3000 on 2007-03-08
Has anyone ever got this to work with ubuntu 6.10 AMD64? I found a post on getting the scanner working but not the printer.

---

### Post by russell.h on 2007-03-08
I got my HL2070N to work by downloading the driver/wrapper to a folder, then going to command line, cd to the folder then:
```
sudo dpkg -i --force-all *.deb
```

That will force it to ignore the architecture thing. From then on out it was just a matter of setting things up just like in 32 bit (in the case of my printer I have to lie to the driver about what model I have, then tell it the printer's IP address.

---

### Post by roberts3000 on 2007-03-08
I tried that. if fact I have the drivers installed. the printer shows up under printers. it just doesn't work. I have a laptop with edgy 32-bit and it works fine, USB or network. its just a no-go on my edgy 64-bit desktop.

---

