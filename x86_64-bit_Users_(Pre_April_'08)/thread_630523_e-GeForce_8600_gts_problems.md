---
title: "e-GeForce 8600 gts problems"
date: 2007-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ozenbac on 2007-12-03
OK so I got a 800 gts graphics card from NVidia for my x86_64 gusty box.  I've installed the NVidia drivers but only the pre-grub boot displays, as soon as gusty should be starting up the monitor just goes into standby.

---

### Post by Gunner_Sr on 2007-12-04
I had a similar problem to this. I used the Envy installer and then selected the restricted driver option and it seem to work okay. The only problem now is that it is not holding the resolution after I sudo it.

You can get envy at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Cheerio,

Gunner_Sr :)

---

### Post by saru411 on 2007-12-04
> **Gunner_Sr said:**
> I had a similar problem to this. I used the Envy installer and then selected the restricted driver option and it seem to work okay. The only problem now is that it is not holding the resolution after I sudo it.

You can get envy at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Cheerio,

Gunner_Sr :)

are you setting up your resolution this way

```
sudo nvidia-settings
```

then saving the xorg file?

---

### Post by Ozenbac on 2007-12-04
Got it. between the sudo and restarting the x-server with alt-ctrl-backspace while the nvidia-settings manager was running the dell figured starting working.  Thanks a lot to everyone.

---

