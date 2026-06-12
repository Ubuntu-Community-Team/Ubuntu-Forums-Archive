---
title: "64 bit NVIDIA graphics drivers - X won't start"
date: 2007-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by bilbravo on 2007-04-11
I followed this [faq]("http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia"), which was for the newest 32-bit drivers installed from NVIDIA's website, not from the package manager.  The only difference was that I downloaded the 64 bit drivers (I have a Core2Duo).

Now, when I do a restart I get a DOS-esque GUI (ASCII text, but drawn into "windows").  It says X could not start.  The reason is "No screens found", and further investigation shows that it could not load the NVIDIA module.  The error pertains to not being able to find one.

So, it stops X and I re-install the driver:

```
sudo sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
```

It says it cannot find an interface, but it can try a to download one, I click OK and it installs, then I install the 32bit GLX libraries.

```
startx
```

X starts fine, all is well until I reboot--this is frequent because I need Windows for work.

Any ideas how to correct this?  Should I just go with the NVIDIA drivers in Synaptic package manager?

Thanks in advance.

EDIT:  Updated the link to the HOWTO/faq

---

### Post by dabl on 2007-04-12
Have you tried (after you re-installed your driver) to run ```
sudo nvidia-xconfig
``` in a console window?  This will overwrite your xorg.conf file with the newer driver info.  If you want glx and composite enabled, then it is

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

Then restart the xserver.

HTH

---

### Post by kragen on 2007-04-12
I had a problem where I had the wrong version of the linux-restricted-modules package.  i used the drivers from synaptic, but it might still be needed by the drirvers you use - worth a try at least.

---

### Post by bilbravo on 2007-04-12
dabl:  It runs the config tool automatically.  However, I'll try to do it myself, manually.

Also, I tried to re-install the drivers from synaptic, but it gave me the same result.  I guess I really got this thing fubar. :-)

I'll try to update the restricted modules, I'm running 2.6.17-11 kernel.

---

### Post by dabl on 2007-04-12
I wonder if it could be a problem with just the screen/monitor configuration in xorg.conf, and not the Nvidia driver. Here's an experiment for you - once you have installed the driver and the GUI is correct, can you open a console window and enter ```
sudo nvidia-settings
```?  If so, it should bring up the Nvidia configuration utility.  Click the "Xserver Display Configuration" (approximately) menu item, and then down at the lower right is a "Save configuration to Xorg" button.  Click that and see if you can get it to save your screen settings that way.  (that is why you had to make it a "sudo" command).

---

### Post by bilbravo on 2007-04-12
Well, after I did that in X, I get the same result (have to install drive on boot up, X won't start on it's own).  However, I did get the NVIDIA log, which means 1 of 2 things to me--it is installed properly this time after doing it on boot-up (but NOT from X), or the nologo option wasn't set up this time.  Didn't have time to investigate which one it was.

---

### Post by brunis on 2007-04-13
after driver install i usually do a /etc/init.d/gdm restart .. NOT startx ..

I installed the latest NVIDIA-Linux-x86_64-1.0-9755-pkg2.run from nvidias site..  it works fine.. but after every reboot i have to reinstall it.. or i get an X error.. something about version mismatch in the kernel modules.. 

any ideas ?

(this is on Ubuntu7.04 x64 btw)

---

### Post by dabl on 2007-04-13
Possibly -- if you're installing the proprietary driver directly from the download, I believe you need to do it after shutting down both the xserver and gdm (or kdm).  Observe the "Method" 2 steps here:

[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2)

---

### Post by v3ll0us on 2007-04-13
hey, i've installed the driver same as u are n it said dat i don't have a system utility called 'ld' and ask me to make sure that i've the paskage 'binutils' installed.. any help?

---

### Post by krusk on 2007-04-19
I have the exact same problem as brunis. 

I tried to follow the guide over, but my installer won't start when I use the command given in the guide:

```
sudo sh NVIDIA-Linux-x86_64-1.0-8776-pkg2.run -n -s --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`
```

The driver is currently installed with only "sh NVIDIA-Linux-x86_64-1.0-8776-pkg2.run", which i have to install on every boot. Very annoying!

Any ideas?

---

### Post by jizo on 2007-04-27
> **v3ll0us said:**
> hey, i've installed the driver same as u are n it said dat i don't have a system utility called 'ld' and ask me to make sure that i've the paskage 'binutils' installed.. any help?

v3ll0ous - ld is a "linker" which is used by the NVIDIA install program when it build the module it is trying to install, you don't have it installed on the system try:

```

sudo apt-get install binutils

```

once that completes rerun the nvidia installer if you get another error in the same step of the installer you might be missing some other packages, the easiest way to find these packages is to run synaptic "System->Administration->Synaptic" and search for the program listed in the error message, then install the package from synaptic.

Good luck

---

### Post by jizo on 2007-04-27
.

---

### Post by jizo on 2007-04-28
I had the exact same problem, having to reinstall nvidia drivers every time I reboot.  It comes down to Ubuntu trying to load it's own restricted kernel module at boot time.  this can be stopped by editing the file

/etc/default/linux-restricted-modules-common

and adding a line

DISABLED_MODULES="nv"

this will prevent the older kernel module from being loaded during boot up.  After I added the line I re-installed the nvidia driver and now I can reboot to my hearts content. :)

There is a good bit of information on the subject at the NVIDA disccusion forms here:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

Hope that helps.

Cheers,

jizo

---

