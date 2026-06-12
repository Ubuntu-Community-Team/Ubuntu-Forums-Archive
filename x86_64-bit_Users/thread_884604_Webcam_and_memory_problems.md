---
title: "Webcam and memory problems"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by Uzelth on 2008-08-09
Heya,

Since installing Ubuntu, I installed the uvcvideo module for my HP Webcam which seems to semi work... The cam outputs an image/video Cheese just fine... but with aMSN and flash chat services the cam doesn't even power on...

Other problem is I have 4Gb RAM in this laptop - It registers 4096Mb during the post, so it's all there... But top says theres only 3890120k total... So I'm missing some RAM somewhere... My graphics card is an nVidia GeForce 8400 GS (256Mb dedicated)... I'm wondering if somehow Ubuntu is assigning it shared memory as the sysinfo app says there's an unknown amount of video RAM available/in use...  My xorg.conf has VideoRam set to 262144 also btw.

Any ideas on how to solve these problems?

---

### Post by Crafty Kisses on 2008-08-30
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

### Post by freackout on 2009-07-13
> **Uzelth said:**
> Heya,

Since installing Ubuntu, I installed the uvcvideo module for my HP Webcam which seems to semi work... The cam outputs an image/video Cheese just fine... but with aMSN and flash chat services the cam doesn't even power on...

Other problem is I have 4Gb RAM in this laptop - It registers 4096Mb during the post, so it's all there... But top says theres only 3890120k total... So I'm missing some RAM somewhere... My graphics card is an nVidia GeForce 8400 GS (256Mb dedicated)... I'm wondering if somehow Ubuntu is assigning it shared memory as the sysinfo app says there's an unknown amount of video RAM available/in use...  My xorg.conf has VideoRam set to 262144 also btw.

Any ideas on how to solve these problems?remove and plug back in the camera the module should be picked up, another very fine programe to consider guvcview it has more settings available and consider UVC compatible camera ie plug n play linux. however it needs pluging in every time to see it unless you give commands to pick it up on boot.

---

