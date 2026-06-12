---
title: "Dual Monitors using 2 X Windows"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by ericson578 on 2008-07-08
When I first loaded hardy onto my laptop (HP Pavilion dv9000us) it detected my second monitor: a Samsung SyncMaster, and cloned the screen onto it, however the resolution on my laptop display was not filling the screen.

After disabling the second monitor I was able to set my laptop to the correct widescreen resolution of 1440x900 using screen resolution option from the system menu -> preferences.  To get the second monitor to work properly I had to install the latest nvidia drivers, and nvidia-settings from the package manager.  I chose two X windows (or x servers, not sure of the vernacular) because I wanted more screen real estate instead of just a cloned screen.

The video card is a GeForce 8600M GS.

Just posting this because it took me a while to figure out what I needed to do to get it to work, but once the correct packages were installed everything was detected and worked beautifully!  Hopefully this thread will help other users installing 64bit hardy on a HP laptop.  btw, dual booting with windows vista worked out of the box, very nice!

Here are the package names that needed to be installed:
  nvidia-glx-new
  nvidia-settings

One of the problems I had with trying to set the resolution was because I started playing around with it before I applied all of the outstanding updates to hardy after a fresh install.  I definitely recommend doing that before trying to setup dual monitors.

Note for beginners: after installing a package like nvidia-settings it doesn't create a menu option for you to click on.  Just open a terminal from the menu Applications->Accessories->terminal  then type "sudo nvidia-settings" followed by your password and then it'll open.  (gksudo might be more appropriate, but I'm not sure when you need to use that instead?)

---

