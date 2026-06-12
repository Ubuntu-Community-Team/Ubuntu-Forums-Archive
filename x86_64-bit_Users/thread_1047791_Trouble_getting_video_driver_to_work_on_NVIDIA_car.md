---
title: "Trouble getting video driver to work on NVIDIA card"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by jecco9 on 2009-01-22
I have a couple of NVIDIA Quadro NVS 290 video cards.  My goal is to set up dual-monitors.  I used to have them set up, but I think after an update, the settings disappeared.  Right now there is nothing under 
System->Administration->Hardware Drivers

I tried following the steps in [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html) again, but that messes up my graphics now.  I tried using EnvyNG, but that messes them up, too.  I also tried nvidia-settings, but I get an error:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  (I tried running nvidia-xconfig also, but it did nothing)

When the graphics get messed up, either the resolution will be set very low, with no option of increasing it or when I restart I get an error telling me there's a problem with my video output, and it gives me an option to configure my output device and graphics card;  that never works either.

Currently, my resolution is where I want it (1680 x 1050), but I have a cloned screen and sluggish graphics.  I'm running Ubuntu 8.04 x86_64.  I'm pretty new to Linux, so I'd appreciate a dumbed-down explanation.  
Thanks.

---

### Post by drs305 on 2009-01-22
First, welcome to the ubuntu forums.

I don't have a remedy for your video card, but here is a link *once you get your graphics working better*. It's a post I saw a couple of days ago regarding dual monitors/cards in 64-bit Intrepid. It may be useful, hopefully soon.

[http://ubuntuforums.org/showthread.php?t=1042426b#6]("http://ubuntuforums.org/showthread.php?t=1042426b#6")
Post 6 is the one with a solution to a problem he'd been having getting the dual nvidia setup to work.

---

### Post by jecco9 on 2009-01-22
Thanks for the tip.  I just tried what post #6 said on that thread, but it caused my screen to go completely black (consoles included).  I fixed it, but still nothing.

---

### Post by jecco9 on 2009-01-26
Does anyone have any other ideas?

By the way, thank you for welcoming me to the forums, drs305.

---

### Post by norwoods on 2009-01-26
updating the kernel ruins the nvidia driver installation.  what i found to work is use envyng to install the 177.xx driver, use envyng to uninstall the 177.xx driver, then install the nvidia 180.22 driver as described by nvidia.

---

### Post by jecco9 on 2009-01-27
Thanks a lot.  I just got it to work...

I had a problem with my sound driver.  Getting help for that lead me to realize that somehow a server kernel had downloaded and was being used when booting (I accept any update the system tells me about--because I don't really know better--so it was probably me that did it).  I removed it and it fixed the sound issue.  

After your post (norwoods) I decided to try using EnvyNG again to remove the current driver.  Then I followed the instructions for installing the 180.22 (something which I had tried several times before, but never worked) using the previous kernel (Ubuntu 8.04.2, kernel 2.6.24-23-generic).  I restarted X and I was able to use 'nvidia-settings' without a problem.  I enabled the TwinView option, and now I'm set.

Thanks norwoods and drs305 for your help.  :D

---

### Post by Crinos512 on 2009-04-08
what version are you running now?

I am having similar issues with a Quadro NVS 440 on a x64 install.

Neither 180.44, nor 173.14.16 work for me. I only get the command line, no gui.

---

### Post by jecco9 on 2009-04-08
I'm still running version 8.04.

---

### Post by dughutch on 2009-04-09
Bump - trying to install AMD64 9.04 on Dell T3400 with dual nVidia Quadro NVS 290... only command line... having no luck on gui at all...

I have run X -configure and using tha xorg.conf two of the four screens turn on but the gui hangs at the little white disk and the background is still black... the mouse does move the white disk... but not across screens...

---

