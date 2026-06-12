---
title: "Strange sound problem"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by danieljay on 2007-04-27
I am running Feisty AMD64 on a compaq v3000z laptop. Just recently I have noticed a strange issue with the sound. If I am in the sound recorder and try selecting a drop down, the login sound starts playing. If I do any other navigation in the File Browser besides double click on a folder, the sound plays again. I have not modified any sound config files yet (I need to so I can get the headphone jack to work properly), but would like to figure this out first. Do I need to use apt to uninstall alsa and then hand compile alsa from source?

I just installed this about 2 weeks ago and have only configured the desktop effects, ndiswrapper.

---

### Post by Kilz on 2007-04-27
Try this. Click System > Preferences > Sound and make sure that one of click on something isnt set to Login.

---

### Post by danieljay on 2007-04-28
Thanks, that seemed to take care of it. I thought that I changed that but it took a reboot for some reason to apply the settings.

---

