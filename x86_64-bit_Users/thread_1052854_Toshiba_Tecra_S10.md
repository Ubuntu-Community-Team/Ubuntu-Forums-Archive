---
title: "Toshiba Tecra S10"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by redscorpion69 on 2009-01-28
Hi all, 
I'm fresh new forums, and Ubuntu. I installed 8.10 amd64 on my laptop Toshiba Tecra S10, and there are few things which are not working, such as sound card, and processor fan (which I believe is a priority to work). 

I need directions on where to find drivers for mentioned laptop, I'm grateful for anyone who can help me.

Have a nice day!

---

### Post by Tubes6al4v on 2009-01-28
Hi brother. I would suggest searching your sound card name either here or on google with Ubuntu after it. There is an astounding amount of information on the net for Ubuntu. As for the fan. This is a known issue. I forget which forum it is filed under, but there was a sticky about it. The only solution I remember is to disable powernowd or something. It is the power control module. I would have tried it, but my fan has the oposite problem: it won't shut off! But on an HP laptop, thats not that bad, it runs hot.

Got bored. Here it is for laptops: [http://ubuntuforums.org/showthread.php?t=1008478](http://ubuntuforums.org/showthread.php?t=1008478)

---

### Post by redscorpion69 on 2009-01-28
ty kind sir, will check it out. That's bad news for fan i guess, can't allow processor to burn, especially since i'll be running dynamips..

---

### Post by Tubes6al4v on 2009-01-28
Whoops! wrong thread. sorry!

---

### Post by redscorpion69 on 2009-01-30
Well, i tried pretty much every option, and i still have no sound :( Pretty frustrated at this point. 


redscorpion69@tecra69:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

this shows i have it installed? But no sound...

---

### Post by rationalperseus on 2009-06-19
With the 9.04 version (never tested 8.10) is enough to edit
/etc/modprobe.d/alsa-base file, and append to the end:

options snd-hda-intel model=toshiba

Reboot and voila!

---

