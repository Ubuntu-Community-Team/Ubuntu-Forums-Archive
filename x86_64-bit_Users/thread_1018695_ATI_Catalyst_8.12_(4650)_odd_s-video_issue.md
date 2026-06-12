---
title: "ATI Catalyst 8.12 (4650) odd s-video issue"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by pluto7777 on 2008-12-22
I recently bought an ATI 4650. 

I installed the Catalyst 8.12 drivers on Ubuntu x64 8.10 and for the past couple days I had two perfectly working displays. 

1) PC monitor on dvi 
2) TV on s-video

Last night I tried to open a video file in VLC on display 2. VLC stopped responding so I tried to kill it via terminal. That didn't work and at some point I believe the display froze. I did a system restart and after the Ubuntu load screen, both displays flickered and went black. 

I had to restart again and hit escape to do recover boot. I used xfix to reset the display and was able to startx again. I enabled Catalyst drivers again, unplugged s-video, and restarted. The PC monitor works fine with Catalyst, but when I tried to enable s-video I got a hard freeze and gray and orange horizontal lines on the TV. 

I reinstalled the Catalyst drivers again for good measure, but that didn't fix anything. It's almost as though the TV goes out of range immediately upon detection and everything locks up.

I know there's nothing wrong with my tv set, and the video card mirrors perfectly on both PC monitor and TV up until after the Ubuntu loading screen then everything goes black.

I would really like to be able to watch video on a separate display again and I have no idea how VLC crapping out would kill the ability to display anything after Ubuntu loads.

---

### Post by pluto7777 on 2008-12-22
I think I managed to some how activate an older driver in Hardware Drivers. 
Deleting /etc/ati and reinstalling Catalyst 8.12 fixed the problem.

---

