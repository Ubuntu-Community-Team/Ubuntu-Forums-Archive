---
title: "[SOLVED] upgraded to 8.10 and have low resolution"
date: 2008-11-08
forum: x86 64-bit Users
---

### Post by jessemmy1963 on 2008-11-08
I just upgraded from 8.04 to 8.10 and can't get the resolution any better than 640x480.  I am running an NVIDIA based geforce 6150 card and an AMD 64 dual core processor. The latest NVIDIA proprietary driver (177) is installed and activated but still can't get better than 640x480.

I installed the drivers by going to HARDWARE DRIVERS which then searched for new drivers and recommended the 177 driver.

I am a fed up Windows XP owner who loves the stability of UBUNTU but my knowledge of UBUNTU is limited.  Please keep that in mind when replying because I am a newbie.



P.S.  After posting this I found a similar issue on another post and fixed the problem.

     I opened a terminal and entered: sudo nvidia-settings
     resolution was set at maximum of 640x480
     I changed it to: AUTO
     Restarted computer and it came up 800x600
     I then went to PREFERENCES then SCREEN RESOLUTION and now I can choose 1680x1050 resolution!!!
     Everything working great now.

---

