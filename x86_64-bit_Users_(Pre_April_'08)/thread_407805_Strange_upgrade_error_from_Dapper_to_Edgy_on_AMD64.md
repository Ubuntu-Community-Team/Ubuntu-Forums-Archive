---
title: "Strange upgrade error from Dapper to Edgy on AMD64"
date: 2007-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by a-musing amazon on 2007-04-12
I've been running Dapper 6.06 ever since last April. I use the latest Dapper AMD64-k8 kernel.

I've been reluctant to try and upgrade to Edgy because everything basically works, however I have noticed that the packages I use only seem to get security updates and when I've tried compiling newer version of software they often break becuase they are intendned to run against a later version of Gnome/GTK.

Anyway with Feisty 7.04 coming very soon I was even more reluctant to try a 2 generation at once upgrade, so I backed up my Ubunt partitions and tried to do an official upgrade to Edgy 6.10 using gksu "update-manager -c".

Everything seemed to work OK - it took about 1/2 an hour to download (on an 8Mb connection) and another 1/2 hour to configure, the problem came when I got to reboot at the end. Initially it seemed to hang on the reboot (no vvisible or audible disk activity), I pressed the externsl reboot button and it came up in grub showing, as first choice, a non-AMD64 2.6.17 generic kernel. This did boot into my normal login screen and then most of my normal desktop (the background has gone to brown rather than the photo I normally use). However all the apps were the old Dapper versions and when I checked the config files (e.g ntp.conf)  that I had asked to be updated they were the old config files. The other odd things was that the keyboard worked but the mouse didn't. Rebooting and choosing my standard 2.6.15 kernel and I was back in my standard Dapper config.and apps (mouse now working)
The only changes seemed to have been the added kernel non-amd64 2.6.17 generic images etc. in /boot (which were not showing up in synaptic).

So, does anyone with any suggestions as to why this did not work and what I need to do to make it work?

---

### Post by a-musing amazon on 2007-04-13
Just to report that on having another go the upgrade to Edgy did work the second time :-).

Needless to say on reboot it crashed the X-Server :-(, fortunately I did have a backed-up pre-fglrx xorg.conf which allowed me to restart the graphical interface. 

I've since downloaded and run the latest Envy to get fglrx 3D working again, including googleearth (for which I keep an old 32-bit libGL.so.1.2).

However I have been getting some display freezes, which were rare on Dapper, and I still have to check whether flash, realplayer and mplayer still work.

NB there don't seem to be any specific AMD-k8 kernels in the repos for 2.6.17 - I used to use them for 2.6.15 - are they now unneccessary?

---

