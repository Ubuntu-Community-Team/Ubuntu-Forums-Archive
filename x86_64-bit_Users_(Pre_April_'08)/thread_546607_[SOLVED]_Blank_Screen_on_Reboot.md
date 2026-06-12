---
title: "[SOLVED] Blank Screen on Reboot"
date: 2007-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by glee on 2007-09-09
OK, this is bizarre. I have a fresh Feisty build that does not send a signal to the monitor after a reboot. Worse, it seems to interact with my hardware in such a way as to prevent display to the monitor during POST. This is a dual boot machine which has been reliably running XP for many months. By guessing the time when the GRUB menu is displayed I can boot into XP, and have the graphics resume as expected. 

[LIST]
[*]Reboot from XP shows full details during POST, and display works as normal. 
[*]Reboot XP -> Feisty, displays during POST and loses signal shortly after GRUB menu. After this, signal remains absent until next XP boot.
[/LIST]

It gets even stranger, let me outline the history:   

I have spent the day building and configuring fresh Ubuntu AMD64 box, on a Gigabyte GA-K8NF-9 board with an NVIDIA 8600 GTS graphics card. Install was straightforward. I then set about updating the NVIDIA drivers, which I did by downloading the driver and running the utility via

sh NV*

I had to manually edit xorg.conf to set the screen resolution to 1600x1200, but all seemed to work well enough. 

I installed flash into firefox, and started to wonder about the lack of sound. After some forum trawling, I downloaded the latest ALSA drivers and recompiled them to run my Intel8x0 onboard soundcard. Reboot. ...Nothing. No input seems to trigger monitor wake up. No response from Ctl-Alt-Fn or Cntl-Alt-Backspace. Cntl-Alt-Delete rebooted the machine, as evidenced by disk activity, POST beep, and device probing, but zero response from the monitor. Many reboots, no change. In disgust, I turned the machine off and had lunch. After 30 minutes down time, restart still produced no graphics.

Suspecting hardware issues, i thought to try guessing the boot time into XP. To my amazement, it worked. Monitor did not respond immediately but came good as the Welcome screen appeared. Graphics remain stable until next attempt to boot Feisty, with symptoms as described above. These symptoms are reliably reproducible, as several iterations have revealed.  

Anyone got suggestions on this one? Seems to me as if something about the way the video driver is interacting with the card sets things awry in a way that is able to persist through power cycling. I find that a bit of stretch, quite frankly, but the symptoms do appear to be consistent with that idea. 

Obviously, I am posting this from my XP partition, and have limited capacity to debug the issue. 

Any insight appreciated.

---

### Post by glee on 2007-09-09
Ah, booting into Feisty recovery mode and running startx reveals:

> ERROR: API mismatch. NVIDIA driver component has version 100.14.11 but the NVIDIA kernel module's version does not match. 

This at least gives me hope. Can anyone suggest what's required here?

---

### Post by pnotequalsnp on 2007-09-09
I had a similar symptom that it would be a blank screen on a reboot(see problem #2 at [http://ubuntuforums.org/showthread.php?t=545870]("http://ubuntuforums.org/showthread.php?t=545870") ) and the way it was resolved was to remove the "splash" part in the grub menu.  Of course you need access to grub, so if you cannot edit /boot/grub/menu.lst directly you could try to use the super grub cd ([http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")).  I hope this gives you at least one option to try.

---

### Post by glee on 2007-09-09
Aha! Thank you for that, most helpful (if somewhat perplexing). By removing the "splash" from the end of the kernel lines in menu,lst I was able to boot the generic kernel into console mode, edit /etc/X11/xorg.conf to replace Driver "nvidia" with "nv", and successfully run startx (albeit in reduced resolution). At least now I have a semi-functioning system to work on as I try to debug this issue.

I'm still quite at a loss for how to match the kernel module with the recently built driver, though. Any help appreciated. I'm not sure that running Envy at this point would be a helpful thing to try.

---

### Post by glee on 2007-09-09
The NVIDIA AMD64 README at [http://www.nvidia.com/object/linux_display_amd64_100.14.11.html]("http://www.nvidia.com/object/linux_display_amd64_100.14.11.html") is very detailed and helpful.

Following the details found under **Debian GNU/Linux or [K]Ubuntu with Xorg 7.x** on [http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490").

I did the following:

> sudo apt-get install xserver-xorg-dev 

> sudo rm /etc/init.d/nvidia-kernel

> sudo nano -w /etc/default/linux-restricted-modules-common 

DISABLED_MODULES="nv nvidia_new"

I also noticed in passing that apt reported a now unnecessary nvidia-kernel-common package, and removed it with 

> sudo apt-get autoremove

I reset /etc/X11/xorg.conf by running
> sudo nvidia-xconfig

Attempting to restart X with Ctl-Alt-Backspace at this point produced the same error as post #2.

Failing any other suggestions I re-ran NVIDIA driver installer
> sh NV*

This produced the ominous sounding
> ERROR: Unable to create /lib/modules/2.6.20-16-generic/volatile/nvidia.ko for copying. No such file or directory.

WARNING: Unable to restore file lib/modules/2.6.20-16-generic/volatile/nvidia.ko

But I restarted X and everything works!! :) Reboot behaves just as one would hope. 

Aside: One as yet inexplicable side effect of this adventure is that running the Feisty installer disk now (and still, even after the installed version is fixed) produces the blank screen symptoms reported above (!!?).

---

