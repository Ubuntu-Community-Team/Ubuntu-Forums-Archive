---
title: "wine taskbar dual monitor problem"
date: 2008-03-27
forum: Wine
---

### Post by Elle Stone on 2008-03-27
Hi All,

I have a dual-monitor (nvidia twinview) setup that is working just fine, UNTIL I start wine 0.98.  Wine starts and runs beautifully, EXCEPT it repositions my icewm taskbar from the bottom of the second monitor to the bottom of the first monitor.  

And then I no longer have access to the second monitor, EXCEPT for the wine application, which quite nicely can be resized and repositioned to cover part or all of one or both monitors.  All other applications are confined to the first monitor (well, they can be moved down until the title bar hits the repositioned task bar - somehow the system seems to think there is only one monitor, except for wine, which gets to use both monitors).

And the only way to get full use of both of my monitors back is to log out of X and then back in.  I've searched the internet to no avail and really hope someone here on the wine forum might have an answer.

Thanks!

Elle

---

### Post by Elle Stone on 2008-04-04
The problem was with my xorg.conf file.  I am posting the "cure" to my
"nvidia icewm twinview dual-screen wine woes", in case anyone else has the same
problem.  I needed to add the following line under Section "Device" 

Option "NoTwinViewXineramaInfo" "True"

According to
[http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/README/appendix-b.html),
"Some window mangers get confused by this information, so this option is
provided to disable this behavior."  It seems icewm is one of "those" wms.  I
don't know what other consequences there may be to using this option with
twinview.

---

