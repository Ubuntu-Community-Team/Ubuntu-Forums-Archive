---
title: "Realtek HD audio drivers"
date: 2009-11-14
forum: x86 64-bit Users
---

### Post by s1mp13m4n on 2009-11-14
Hello everyone.  I went from Xubuntu 9.10 32bit to 9.10 64bit and my audio is not working.  How do I install Realtek HD audio drivers for 64bit Linux?  I am a newbie so be gentle. Also, in my 32bit install when I plugged in my headphones the main speakers do not turn off like in Windows...and there is no switch or button to turn them off in the mixer.  Thanks for the help.

---

### Post by HappyFeet on 2009-11-14
Do:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Then, at the end of the file paste in **options snd-hda-intel model=3stack**

Save file and Reboot.

---

### Post by s1mp13m4n on 2009-11-14
> **HappyFeet said:**
> Do:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Then, at the end of the file paste in **options snd-hda-intel model=3stack**

Save file and Reboot.

OK, sorry but I do not understand.  The laptop is a Chembook so when I go to their website it does not tell me which Realtek card is in the laptop.  Linux does not tell me either.  Xubuntu found the NVIDIA video card and found a driver for it, so why will it not do the same for sound?  :)

I clicked on the above link [www.linuxcommand.org](www.linuxcommand.org) so I can learn the command line.  I will learn this over time because it seems in Linux you must kno it.  :0

---

### Post by Digikid on 2009-11-14
This MIGHT work...it might now.

I found that the 56k modem driver was stopping my sound from working....I deactivated the modem driver ( who uses 56k anymore anyways? ) and my sound works.  Some conflict between the two devices I guess.

---

