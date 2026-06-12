---
title: "nVidia + AMD64 + Ubuntu = Fail :("
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by smacky_wolf on 2006-05-10
Hi all,

I am a fairly established Ubuntu user, and just recently got a new PC. THe rig uses the ASUS A8N-(VN?) MoBo, which has a builtin nVidia 6100 Geforce (I think) and an nForce soundcard. I have an AMD Athlon 64 3000+, and can't compile the drivers for sound and video.

Which kernel headers do I need? The software I grabbed from the nVidia site just tells me I am using the wrong GCC, because my kernel was compiled on a different one. If I ignore this, then it just fails to install. 

I'm using the 64bit Ubuntu distro. Anyone have any ideas? I am on dialup, so I can't just grab any of the header packages, and the updates that the system wants are out of the question.

<3 Smacky

---

### Post by maury on 2006-05-10
This works for me
Ubuntu AMD_64 you just install nvidia.glx using synaptic
and change nv to nvidia in /etc/x11/xorg.conf and then Reboot.

---

### Post by iTrendsNET on 2006-05-10
I have been fortunate with nforce 2 and 3 boards not needing me to do anything special to get sound and networking working as I guess everything was built into the kernel.  

For your solution, try tseliot's guide, option 2 for per his posts here in the forums.  He claims this should work for your your system.

---

