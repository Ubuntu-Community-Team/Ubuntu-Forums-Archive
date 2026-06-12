---
title: "Ubuntu Asus A8V-E SE Cool &amp; Quiet"
date: 2008-06-07
forum: x86 64-bit Users
---

### Post by stevenma188 on 2008-06-07
Hi, Im a new linux user and just installed Ubuntu 8.04LTS. I have the Asus A8V-E SE with a A64 3700+ cpu. I have cool & quiet and Q-Fan enabled in the bios. I am wondering what i need to do to make sure that Cool & quiet is actually working. (i think i saw somewhere using terminal that the cpu was clocked down to 1.1ghz which means it should be working, but i would like to confirm it again) Also, how do i get something similar to q-fan drivers or some sort of fan controller program so my fan is not always running at full blast. (its bloody noisy right now). 
Thanks for all your help.

---

### Post by slowcoach on 2008-06-07
Turn on Cool & Quiet in the BIOS.

Enter in a terminal  cat /proc/cpuinfo  when the machine is idle, cpu MHz should be around 1,000 then copy a large file and while it is copying enter the command again which should now show your cpu working at it's full speed.

---

### Post by stevenma188 on 2008-06-08
what about fan throttling? I dont mind running my computer at full speed, but i cant stand the fan noise. Thats the reason behind this.

---

### Post by slowcoach on 2008-06-08
I went water-cooled after not finding a method of effective and quiet air cooling.

---

### Post by vrangforestillinger on 2008-06-08
To monitor fans, temperatures ++ you can install lm-sensors. Its in the repos.
```

sudo apt-get install sensord
sudo sensors-detect

```
Sensors-detect will try to detect sensors on your computer. Its mostly OK to answer default on questions it might ask unless you know what you are doing. When its set up you can run ```
sensors
``` to check on the detected sensors. There are several GUI-frontends. I use sensors-applet (sits on my gnome panel).

For the GNOME panels there is also a CPU-speed monitor, I think its installed by default.

To actually control the fan-speed, I dont know if its possible to do it from software on your card. I havent tried on my ASUS KN8.

---

### Post by Yellow Pasque on 2008-06-08
This site is devoted to PC silencing and contains a wealth of info: [http://www.silentpcreview.com/](http://www.silentpcreview.com/)

As for fan control, you can try turning off the BIOS fan control (Qfan) and using this command:
```
sudo pwmconfig
```

---

### Post by stevenma188 on 2008-06-09
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


That is the response i got when i tried the pwmconfig

---

### Post by stevenma188 on 2008-06-09
actually if i enable q-fan in the bios, pwmconfig seems to work. However, it seems that my AI Overclock no longer works. I had AI OC enabled at 10% before as well as Cool n Quiet, allowing my cpu to run betwee 1.1ghz and 2.42ghz (stock 1.0ghz - 2.2ghz). Any insights on this?

---

