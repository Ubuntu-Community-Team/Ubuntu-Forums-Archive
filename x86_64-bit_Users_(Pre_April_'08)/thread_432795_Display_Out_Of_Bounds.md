---
title: "Display Out Of Bounds"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by shreeram13 on 2007-05-04
Friends, am Linux newbie. I have installed Ubuntu Fiesty...X64 on my AMD Athon 3800+ machine. 

Machine Details are as follows:

Mainboard:
MSI - K9NU NEO-V [AMD K9 NVIDIA 1697]

CPU
• AMD® Athlon 64 3800+ in the Socket AM2 package.

FSB
• HyperTransport supporting speed up to 1GHz (2000MT/s)

Chipset
• NVIDIA® M1697 Chipset

RAM 1GB DDRII

Audio
• Chipset integrated by Realtek® ALC883
- Flexible 8-channel audio with jack sensing
- Compliant with Azalia 1.0 Spec

LAN
• 10/100 Fast Ethernet by NVIDIA® M1697 [ONBOARD LAN]

GPU:
NVIDIA Geforce 7300GS 256MB 

GOOGLED FOR NVIDIA AND INSTALLED NVIDIA FROM FOLLOWING
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

But my NVIDIA Display settings gives me just 4 options and 1280x720 goes out of bounds. 
I am attaching my NVIDIA Settings image and xorg.conf files here. Can somebody help.

With warm regards,

Harshal

---

### Post by kuja on 2007-05-04
I've got a few ideas. 1: make sure nvidia-settings is running as root (ie: kdesu/gksudo nvidia-settings) - 2: Add your desired resolution to the "mode" lines in the xorg.conf. Just add it like the others, with the biggest res on the left and the smallest on the right (by convention, not sure if it matters) - 3: after finished editing it as root, be sure to click save to x configuration file.

---

