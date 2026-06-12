---
title: "clock doesn't show weather information"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by Grone1985 on 2008-05-05
I live in Santiago, Chile, and for some reason I don't get the weather information on the clock applet. I have this problem that the same applet will not remember my location (America/Santiago) and always change it for Asia/Kolkata after each reboot and I think those might be connected but even when I correct this (after each reboot) the information doesn't show up. Any suggestions?
Thanks in advance!

BTW I'm using Ubuntu Hardy 64x with all updates installed on a Dell Inspiron 1501.

---

### Post by 0x656b694d on 2008-05-06
Hi,

try to check that your system time zone is set appropriately (right click by the clock, select Adjust Date & Time).
I feel they fixed saving location in the latest update.

good luck!

-Mike

---

### Post by Grone1985 on 2008-05-07
No... It's still the same, the time zone was set to Asia/Kolkata and after changing it to the right time zone, the weather information still didn't showed up. I read on another thread that it could have to do with network proxy settings and firewalls and I'm behind a router, can that affect the connection of the applet with the internet server? If so, how can I fix that? Thanks in advance!

---

### Post by infinito on 2008-07-17
Do you have this file? /etc/timezone
It should contain America/Santiago, if not, create it and try again.

Look at this bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/216197](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/216197)

---

### Post by soxs on 2008-07-17
right click on the panelclock -> prefernces. Goto the second tab and add your Location and select your time zone. after that you should get the correct coordinates of your city. Press the close button and the weather info should apper in you panel as it did in mine. Good Luck.

---

### Post by Enigmatic on 2008-07-25
I have the same problem. I have followed all steps correctly...after I select my location (correct timezone too), it expands slightly to allow for the weather icon, but never actually updates it with the weather.

---

### Post by EmilyRose on 2008-07-26
I have the same problem. Mine was working fine on dial up but as soon as I switched to "high speed" through a cell phone and router it hasn't worked. I'm pretty sure it must have something to do with my router settings, but I haven't a clue as to what could be wrong. It actually says "Retrieval failed" at some point.

ETA: Just wanted to add that I can infact get a radar map but not my actual forcast :(

---

### Post by YldGuy on 2008-08-15
i have a slightly different kind of problem. My weather pattern doesnt change!. Yesterday it was raining ouside.. Google Gadgets showed the temp at around 20 C but the hardy weather has stayed constant at 27 C for the past one week. It changes when i select a different city as my home but its not updating with the current weather changes. any ideas?:confused:

---

### Post by Yellow Pasque on 2008-08-16
I'm behind a router and the weather applet works fine for me without changing any settings in the Network Proxy dialog.

---

### Post by Grone1985 on 2008-08-16
Now it works totally fine for me for some weird reason... and I didn't change or fixed anything but the location on the clock preferences.

---

