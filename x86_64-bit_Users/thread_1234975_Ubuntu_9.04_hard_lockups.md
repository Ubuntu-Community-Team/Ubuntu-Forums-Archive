---
title: "Ubuntu 9.04 hard lockups"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by hiflyer on 2009-08-08
I have a HP Pavilion a1657c
It has been running Ubuntu desktop 8.10 reliably with no freeze ups. (I did have freeze up problems with 8.04 but the nvidia 177 driver solved that problem).
the unit has 2 gbyte of memory.
I use samba for the other computers to access the number of hard drives.

I recently upgraded to desktop 9.04. I have had regular freeze ups since then. I have tried the Repository NV drivers 173 and 180 but still got the freeze ups. I tried the Nvidia 185 driver from the Nvidia site. Still no luck. (yes I removed the previous versions of NVidia drivers before installing the new ones). I tried upgrading the kernal with these versions of NVidia drivers. still no luck. I tried the beta NVIDIA 190 driver with the 2063004 kernel but still no luck. 

In working with the system, I did notice that I could regularlly lock the system if I tried to copy large files (1 gbyte files always resulted in a freeze up). most times the cursor was also frozen but sometimes after the rest of the system locked up.

I decided to try stopping the gdm and copying large files. so far no lockup with gdm stopped.

Does anyone have a suggestion of what else to try? I would really like gdm interface to be working reliably again.

---

### Post by Arup on 2009-08-08
Can you enable AHCI mode in your BIOS? Also does the lock happen when you transfer files from hdd to usb drive? In that case, disable legacy usb support in BIOS and see.

---

### Post by hiflyer on 2009-08-08
sorry, I dont know what AHCI is or how to turn off.
I have 500 gb hard drives I am transferring to. I really dont want them turned off.

Yes if I transfer files from a internal drive to a usb drive the problem also happens.

---

### Post by hiflyer on 2009-08-08
I should have added that If I do not transfer any files it still locks up but it just takes longer.

---

### Post by Loosewheel on 2009-08-08
I have been having system lockups running 2.6.28-14-generic kernel.
I have been booting into 2.6.28-13-generic for two days now and have not had this problem.....When it froze up, the mouse and keyboard were unresponsive, and I had to power down by holding the power button in.

---

### Post by hiflyer on 2009-08-08
I did not try 6.28.13. It might be worth a try. In my case, it is a little better with the kernel and NVIDIA driver updates but no sufficient.

After the current file transfers finish (good or bad) think I will give a try.

thanks

---

### Post by Barafu Albino Cheetah on 2009-08-09
AHCI is a new protocol of exchanging between mainboard and HDD by serial interface. Because only Vista and Linux can install on such drives, there must be a setting to switch AHCI  off in BIOS. 
If downgrading the kernel helps you, please inform the kernel team - or they shall keep unusable(for you) changes forever.

---

### Post by hiflyer on 2009-08-09
I may have found my solution. It turns out that several versions ago (either 6 or 7) when I first started using Linux and selected Ubuntu I could only get my HP machine to boot up using the noacpi option in the grub boot menu. I fixed it so it has been permanent thru the various upgrades. I booted without the noacpi option and the system now seems stable with the 2.6.30-02063004 kernel and NVIDIA 190 driver. I have transferred over 10 GB of files and it is still working after 7 hours. I have not had this good of result before. After I let it runs overnight and assuming it is still working, will try downgrading to the highest version of the Synaptic kernel and NVIDIA drivers and see how that goes. Will let all know my results.
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

