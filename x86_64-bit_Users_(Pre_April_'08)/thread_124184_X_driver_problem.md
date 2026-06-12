---
title: "X driver problem"
date: 2006-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by The_Rogue on 2006-01-31
I am very new to Linux but I realy want to learn. Thats why I ordered some of the Ubuntu CDs in the mail. I managed to partition and install just fine alongside Windows, but when I try to boot up Ubuntu, I get a about four screens that flicker for a split secend and then get a "Failed to start X server" message. 

I have read through the forums and a good number of people seem to be having graphics problems that are similar, but I can't find anyone with my card exactly. I'm running an intigrated ATI Radeon XPress 200 on a HP Pavilion a1210n with an AMD Athlon 3500+ and 512 MB or RAM. I REALY want to get this working and any advice would be GREATLY appreciated.

Thanks,
Rogue

---

### Post by RAOF on 2006-01-31
Well, you have two options:  

1) You can change the video driver to "vesa", which should get you into the GUI quickly & easily.  To do that, simply login at the console after it says "failed to start X server", and run "sudo dpkg-reconfigure -p high xserver-xorg".  Select the "vesa" driver when the list of drivers comes up (yours will probably default to "ati").  Then run "sudo /etc/init.d/gdm restart", and you should be away.

2) Install the ATI binary (called the fglrx, don't ask me why) drivers.  Check out the link in my sig.

---

### Post by The_Rogue on 2006-01-31
Thank you SOO much for the fast response! I'm going to try that right away. I'll let you know how it goes.

Rogue

---

