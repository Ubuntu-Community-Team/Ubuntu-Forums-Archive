---
title: "new U_6.06 x64 install"
date: 2007-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by nss0000 on 2007-03-23
Gents:

U_6.06x64 scratch install ( 'factory' CD ) succeeded on AMD5400 / ASUS-m2n / NV7600gs  self-built system. Patition-format OKey. Both CPUs enabled. FFox worked OOTB. Autoupdate followed without issue.  WooHoo!
( FYI:: U_6.10 install failed horribly  with GUI unfunctional ) 
( My  7vt600/2600+ box cranks away with U_5.1 so nothing is a rush )

 So, I've got a speedy,  happily working U_6.06x64 system. However, I have no sound, and no NVidia drivers.  Other stuff too, I imagine. I'd really like to keep this box native x64 code, and yet build-out a robust generally useful system. 

  I can be patient, if untalented  :( . What MUST I do next? What ought to be avoided?? How do I proceed ???

nss
******:confused:

---

### Post by dptxp on 2007-03-24
maybe you post this in beginners forum, that is always very active.

---

### Post by rajeev1204 on 2007-03-24
hi

for nvidia u can install package nvidia-glx from repositories.

then u have to enable the drivers like so ----" sudo nvidia-glx-config enable"


now u will get some message about xorg being changed. 

now type "sudo gedit /etc/X11/xorg.conf" ( case sensitive so careful)

now look for a section that says nv and change it to nvidia

save the file.

reboot.

If something is wrong or u dont get display or error about xserver wont start ,

type this -- "sudo dpkg-reconfigure xserver-xorg"

just select nvidia in first option - select defaults for the rest ( do not change anything)



nvidia is set


regards
rajeev

---

### Post by nss0000 on 2007-03-24
BigR:

Thanks for the comments. I need to hold up a bit. According to another post on this forum there could be complications because of my  ASUS-M2M mobo nv430 chipset.  The nvidia-glx drivers don't seem to like U_6.06 ( 2.6.15 ) , but behave well for the 2.6.19.x kernel.

Think I need to wait a bit -- before touching graphics that work OKey with the supplied drivers.

Thanks again:

nss
*******

---

### Post by nss0000 on 2007-03-26
U_6.06x64 fails to detect onboard soundchip. Will try to bypass by installing legacy SoundBlaster card.  

nss
*****

---

