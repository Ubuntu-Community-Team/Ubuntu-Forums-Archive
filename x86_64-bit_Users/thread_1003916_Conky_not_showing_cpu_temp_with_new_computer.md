---
title: "Conky not showing cpu temp with new computer"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by killer2239 on 2008-12-06
Hey guys. I used to have ubuntu 8.10 32-bit with conky installed. I had it setup, and just made copy of my conf file for new machine. I have new Phenom quad core 2.6ghz version with asus motherboard. The cpu temp just reads 0. Is this an issue with 64bit ubuntu or with conky and lack of support for reading that processor temp? 

Also, my speed of each core is at 2607mhz, on my previous dual core AMD X2, it would always run at 1000mhz and then run 1800 or 2200mhz when i would install things.

Im am still new to ubuntu, and did a few searches but came up empty. Please let me know guys if im posting in wrong category. I figured since i knew things worked fine in 32bit with AMD X2, maybe its a 64bit thing with my new machine.

---

### Post by easybake on 2008-12-06
> **killer2239 said:**
> Hey guys. I used to have ubuntu 8.10 32-bit with conky installed. I had it setup, and just made copy of my conf file for new machine. I have new Phenom quad core 2.6ghz version with asus motherboard. The cpu temp just reads 0. Is this an issue with 64bit ubuntu or with conky and lack of support for reading that processor temp? 

Also, my speed of each core is at 2607mhz, on my previous dual core AMD X2, it would always run at 1000mhz and then run 1800 or 2200mhz when i would install things.

Im am still new to ubuntu, and did a few searches but came up empty. Please let me know guys if im posting in wrong category. I figured since i knew things worked fine in 32bit with AMD X2, maybe its a 64bit thing with my new machine.

Your problems are most likely from a problem in your config file. The variables most likely need to only be changed slightly. I would suggest you post this problem in the [conky mega-thread]("http://ubuntuforums.org/showthread.php?t=281865&page=491") along with your conkyrc file.

---

### Post by soxs on 2008-12-07
Does that script depend upon lmsensors?
if so you could do:```

sudo sensorsdetect
```For me a gnome-panal plugin shows temps of my cpu (Pehnom 9500):

EDIT:

To use powernow, you have to autoload one more module.
Do
```

sudo nano /etc/modules

```and add this line at the end:
```
*powernow*-k8
```reboot and you should be fine.

Note: By default, it will run in "performance" mode, which meens no core downspeeding.
To adjust that behavior, it's easiest to add the pending gnome-panel "applet". This will ask you to run with with superuserrights, accept that, and set it via rightclick to "on-demand". This should do the trick.

Note: Do this four times for all of your 4 cores.

EDIT: And don't blame 64bit Arch for everything that is not working unless it's the exact same machine/setup.

---

### Post by killer2239 on 2008-12-07
Thanks for the info. Im not blaming 64bit for it, i was just curious if it was due to the 64bit. I know it could very well be the motherboard and other settings.

---

### Post by killer2239 on 2008-12-07
Sensors detect code says command not found.

Also i added the powernow-k8 line and that didnt change anything. If there is a site that explains the plugins for gnome-panel or anything please link me. I appreciate your help.

---

### Post by graysky on 2008-12-07
```
# sensors-detect
```

---

### Post by killer2239 on 2008-12-07
Cool, i noticed when running it, it came up saying AMD Thermal something was not available yet for what i have.

---

### Post by killer2239 on 2008-12-07
Ok i figured out the CPU scaling thing. Im still learning ubuntu/linux here. The applets can monitor my cpu temp. I added cpu scaling, and received warning that i am unable to change Freq it runs on. So i assume since i have new asus motherboard with new 9950 quad core that ubuntu/linux in general does not have that support for me yet. Am i right? i just have to wait for update?

Once again thanks for everyones help.

---

### Post by soxs on 2008-12-08
well, of course you should first install ```
sudo apt-get install lm-sensors sensors-applet

```
afterwards do ```
sudo sensors-detect
``` again

---

### Post by Kilz on 2008-12-08
Since I just got conky setup on my new phenom 9950 setup I may be able to shed some light. During sensor-detect this is shown.

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Chip `AMD K10 thermal sensors' (confidence: 9)

#----cut here----
# Chip drivers
it87
# no driver for AMD K10 thermal sensors yet
#----cut here----


To me this says the sensor is detected, but there is no software for it yet. I just figure its part of having bleeding edge hardware (for once). This is not a 32bit thing, it wont work in 32bit either because the driver isnt written. I also have to believe that the driver for this 64bit chip will show up in the 64bit version first.

---

### Post by soxs on 2008-12-08
As far as I know, there was some thingy about K10 support at phoronix.. but it didn't show up in any cvs of lm-sensors...
[http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA](http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA)

---

### Post by killer2239 on 2008-12-08
Hmmm.. Well its good to know its not just me :) , if you get yours working please let me know!

---

### Post by sweetsinse on 2009-01-01
there has been talk of a K10 module that will, i think should already, be out soon.

[http://lists.lm-sensors.org/pipermail/lm-sensors/2008-July/023816.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2008-July/023816.html)

there is also a link to that on Phoronix...

[http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA](http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA)

I used the attachment provided in the first link (the next guy in the list has a 9950 like me and said it worked fine):

[http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin](http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin)

after doing that i *semi* followed these instructions:

[http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html)

1) i downloaded attachment.bin and renamed it to k10temp.c
2) i issued this command in the same directory as k10temp.c

make -C /lib/modules/$(uname -r)/build M=$(pwd) modules

3) i then made sure the module loaded ok

sudo insmod k10temp.ko

4) if that succeeds, and lm-sensors now sees a temp, i copy k10temp.ko to the appropriate modules folder

sudo cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon

5) and update the module cache/dependencies

sudo depmod

6) and lastly add the module 'k10temp' to /etc/modules


after all this i just rebooted and everything was working fine.  the readings have been spot on to my bios readings, after either hours of mprime or idling.

hope it helps

---

### Post by soxs on 2009-01-02
If this works, you get my personal hero, gonna try on sunday.

---

### Post by sweetsinse on 2009-01-06
i did it again after installing to another partition, and it looks like creating the makefile is a necessary step. i didnt think it was using the makefile in any way since only issuing `make` does nothing; you have to use the full command. either way the above works fine.

---

