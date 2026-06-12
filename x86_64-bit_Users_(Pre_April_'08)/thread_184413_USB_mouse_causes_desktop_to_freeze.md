---
title: "USB mouse causes desktop to freeze"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Uta on 2006-05-29
I am using Dapper on my iBook and it's great, I have the wifi stable, everything works (except Flash and Realplayer and that's not Dapper's fault) but if I have my USB mouse (targus mini mouse) plugged in at boot time, the system boots but the desktop is frozen, even if I unplug the mouse at that point, touchpad doesn't work either). If I reboot without the mouse plugged in, there isn't an issue. I can plug the mouse in after boot and there isn't a problem. Why is this happening, is there a fix? Thanks.

---

### Post by ssam on 2006-05-30
you should file a bug. its too late for it to be fixed for the dapper release, but it may get fixed in an update, and can hopefully be fixed for dapper+1

---

### Post by nkbj on 2006-05-30
Try changing the lines

blacklist usbmouse
blacklist usbkbd

to

#blacklist usbmouse
#blacklist usbkbd
blacklist usbhid

in /etc/modprobe.d/blacklist

Regards,
Niels Kristian

---

### Post by Uta on 2006-05-30
Niels, Thank you it worked! I did your recommended edit, left the mouse plugged in and did a restart and everything functioned normally, no desktop freeze. again thank you.

---

### Post by ssam on 2006-05-30
it would be good if you'd still file a bug so this can be fixed properly. mention this work around.

---

### Post by nkbj on 2006-05-30
I'm glad the work-around worked. It seems to be a known bug in Dapper:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36339](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36339)

As Sam said you should add your experience to that bug report.

Regards,
Niels Kristian

---

### Post by Uta on 2006-05-30
Thanks again for your help, I have filed a report. Cheers.

---

