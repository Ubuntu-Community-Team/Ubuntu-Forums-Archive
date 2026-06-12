---
title: "No sound after reboot every time!"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by norcim on 2009-04-30
I have an Asus mobo M3N78-MV with (00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
) Nvidia sound card built-in. Each time i reboot I lose sound so then I have to: 

  sudo modprobe snd-hda-intel 
  sudo alsa force-reload

The sound works fine until the next reboot. I have tried to save the settings:

sudo alsactl store 0
 
And I have tried to add:
  snd-hda-intel 
  to
  /etc/modules 

And I have tried to add: 
  options snd-hda-intel index=0
  to
  /etc/modprobe.d/alsa-base.conf

Anything else I can do the make the settings presistent?

---

### Post by Sef on 2009-05-01
What Ubuntu do you have?

---

### Post by norcim on 2009-05-01
The latetest 9.04. fresh install at this point.

---

