---
title: "Kernel Update Issue"
date: 2008-12-09
forum: x86 64-bit Users
---

### Post by eyemou on 2008-12-09
Hi,

Ever since upgrading to the latest kernel (the newest in the repos... I am not in front of the machine, so I don't have the exact version handy), I have been unable to boot into it. 

It seems to get stuck when loading X, Somewhere between the Kubuntu splash/progress bar and the login screen. I briefly get an "X" mouse cursor, and then everything goes back to the terminal, but doesn't dump me at a prompt, but back to stuff like:

"Checking Battery State [OK]"
"TiMIDIty Alsa ... ... [OK]" <---- paraphrase

This is Kubuntu 8.10 AMD64 w/an Nvidia 7600GT. I have a feeling that this is a disagreement between the new kernel and the Nvidia card, as the problems occur when X is starting.

If I stop GRUB and opt to boot into the previous kernel version (the only other one, from a fresh install), everything works just fine.

I've tried installing envyng & booting into Recovery Mode for the latest kernel, however, I guess in Recovery Mode you do not have networking, so it is unable to install the new driver.

I guess my question is: am I barking up the right tree with this being an Nvidia issue? And how do I get networking up & running in Recovery Mode? 

Thanks

(On second thought, I believe I do still have the Nvidia 177 driver installer on my drive -- does envyng do anything that re-installing the driver wouldn't do?)

---

### Post by cariboo on 2008-12-09
If you restart in recovery mode and choose xfix from the menu this will recreate your /etc/x11/xorg.conf, and you should be able to boot into your desktop where you should be able to setup your video card.

If you need to isntall the driver from the console, to get networking start at the prompt type:

```
dhclient eth0
```

This assumes that eth0 is your network device, if it isn't substitute your device, and you should have networking.

Jim

---

### Post by eyemou on 2008-12-09
Thanks!

---

