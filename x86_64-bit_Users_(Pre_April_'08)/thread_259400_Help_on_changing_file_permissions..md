---
title: "Help on changing file permissions."
date: 2006-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-09-17
I need to chmod /dev/parport0 to get my printer working in vmware. Permissions reset at boot. What configuration file needs to be edited to reset permissions permamently?

---

### Post by baldy1324 on 2006-09-17
hmmmm. make sure you're running ```
sudo chmod +x filename
``` however i think that the /dev file tree isn't actually on the filesystem and virtual like proc, so maybe it will always reset on boot since it dosent reside on the hd. my recommendation is to add a script at bootup to run chmod...

---

### Post by mrw on 2006-09-17
the dev file is in the real filesystem and I can change it with sudo chmod getting the  port and printer to work in vmware. Trouble is it keeps reseting when I reboot. How do I add a script file at bootup?

---

### Post by kuja on 2006-09-17
You could make a file that looks like this

```

#!/bin/sh

chmod +x /dev/parport0

```

Lets save it as, hmm, lets say "parport0"

```

sudo mv parport0 /etc/init.d
sudo update-rc.d parport0 defaults

```

Voila, it's a startup script now.

---

