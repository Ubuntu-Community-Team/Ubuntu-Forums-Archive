---
title: "Ubuntu Studio install Ubuntu 9.04Jaunty Ready"
date: 2009-09-05
forum: x86 64-bit Users
---

### Post by ken78724 on 2009-09-05
for Ubuntu Studio install see steps 2 & 3 but make sure you have a good install first.

---

### Post by ken78724 on 2009-09-06
My Ubuntu mentor Aaron Osmer says 
"Ken you build ubuntustudio on U 9.04 64 bit by going to terminal and do a 
1.sudo aptitude search ubuntu studio AMD 64 [input password & return]
2.sudo aptitude install ubuntustudio [input password & return] Then I followed the output by 
3.Yes continue

I still must create I believe a) menu 1sg or b) make “Rt” have different weight; then c) generic

if this works, I will report back...

---

### Post by ken78724 on 2009-09-06
didn't end up with a full working ubuntustudio but have followed with this in terminal 
#!/bin/sh

gksudo "aptitude -y install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-controls ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-graphics ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-video ubuntustudio-wallpapers usplash-theme-ubuntustudio linux-rt linux-restricted-modules-rt linux-image-rt linux-headers-rt";

Hey now I boot up in Ubuntu Studio and in administration > there's a "Ubuntu Studio Controls". The screen is not at all like that installed by 9.04 Jaunty. Over 300 packages were installed, meaning one gets a lot more than one may ever expect to use.

---

### Post by ken78724 on 2009-09-08
it's your decision; jack server or OSS4 sound aka &#8220;oss-linux-4.1-1052_amd64.deb&#8221; Visit  
[http://www.4front-tech.com/release/oss-linux-4.1-1052_amd64.deb](http://www.4front-tech.com/release/oss-linux-4.1-1052_amd64.deb)

for help see: 4front-tech.com.

---

### Post by ken78724 on 2009-09-08
don't fix what works if you have ALSA sound and someone talks up OSS4. be forewarned ... using that alternative can leave one wondering in the woods. if you get chirps at System>Sounds>tests set to OSS4 & hear a YouTube, etc., set ur toogles, etc. kick back, do something else..

---

### Post by ken78724 on 2009-09-26
back up data & OS

---

