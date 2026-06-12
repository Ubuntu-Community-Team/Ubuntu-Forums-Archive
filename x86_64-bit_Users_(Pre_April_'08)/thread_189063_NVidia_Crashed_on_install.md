---
title: "NVidia Crashed on install"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slurm on 2006-06-04
Well... it happened.  

I posted a thread about 4 weeks ago I posted a thread asking if there was anything I could do to prevent my nvidia driver from crashing when I upgrade to Dapper.  I got .... silence.  

SO.. I installed Dapper and lo and behold my driver crashed along with GDM and Xserver.  

So now I have to ask if Tseliot's method will work in redownloading my driver and bringing my system back to working again.  The question now is that I have to specifically use gcc 3.4 to get it to work when my system is now running 4.0 or higher.  OR is there a better method now in installing this driver and EasyUbuntu does not work (yet) for Dapper.  

Please let me know

Slurm

---

### Post by JoWilly on 2006-06-04
Only thing needed to install nvidia is:

1. install "nvidia-glx" , if you have no x "sudo apt-get install nvidia-glx"
2. replace nv with nvidia in /etc/X11/xorg.conf ( "sudo nvidia-glx-config enable" will also do this)

---

### Post by Slurm on 2006-06-04
Thank you,

I tried your suggestion and it did not work. Yes it downloaded the kernel and glx and seems to resolve the dependencies, but it still did not work.  I get a blank screen when I set it  up and I still am having to run my monitor through 'TV Out' to get a GUI.   I think that there is something the matter with my GDM, when I did the upgrade, the system seemed to hang there.  Do you know how to reconfigure or redownload the updated gdm?  

Slurm

---

### Post by JoWilly on 2006-06-04
[quote=Slurm]Thank you,

I tried your suggestion and it did not work. Yes it downloaded the kernel and glx and seems to resolve the dependencies, but it still did not work.  I get a blank screen when I set it  up and I still am having to run my monitor through 'TV Out' to get a GUI.   I think that there is something the matter with my GDM, when I did the upgrade, the system seemed to hang there.  Do you know how to reconfigure or redownload the updated gdm?  

Slurm[/quote] 
If you get a blank screen this means that X has started, otherwise you would get an error message. This is confirmed by the display on tv-out.

So, if you get X on tv-out but not on your monitor, there's something wrong with your monitor's config.

-> check xorg.conf to see if the refresh rates and the display modes are right for your screen.

EDIT : to reinstall gdm without x "sudo apt-get install --reinstall gdm"

---

