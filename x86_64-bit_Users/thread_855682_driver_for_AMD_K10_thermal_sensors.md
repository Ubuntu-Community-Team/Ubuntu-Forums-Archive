---
title: "driver for AMD K10 thermal sensors"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by larka06 on 2008-07-10
Everything is detected in lm-sensors but it says there is no driver for my CPU. I have been looking for drivers for the AMD K10 sensor. I have not found one does anyone know of where to get one.

---

### Post by forger on 2008-07-10
did you try this: sudo sensors-detect

---

### Post by soxs on 2008-07-11
**For sensors do:**
Go though detection (pressing retunr N times)
```
sudo sensors-detect
```

check wether it works or not:
```
sensors
```

**For powernow do:**

```
sudo apt-get install powernowd 
sudo dpkg-reconfigure gnome-applets 
sudo apt-get install sensors-applet 
sudo nano /etc/modules

```
# add 
```
powernow-k8
```
# in a new line

reboot:
```
sudo init 6
```


**[COLOR="YellowGreen"]PHENOM ROXXS[/COLOR]**

---

### Post by soxs on 2008-07-19
[http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA](http://www.phoronix.com/scan.php?page=news_item&px=NjYwMA)

---

### Post by hanbin973 on 2008-12-22
but I'm using cpudyn and cpufrequtils. is there any way for this?

---

### Post by eloydark on 2009-06-27
Is the lm-sensors website offline? I am trying to enable the K10 sensors but I cannot download the binary file from the mailing list (nor connect to the official website)

---

