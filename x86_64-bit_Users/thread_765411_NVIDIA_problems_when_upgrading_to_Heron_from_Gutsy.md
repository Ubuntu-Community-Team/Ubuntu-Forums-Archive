---
title: "NVIDIA problems when upgrading to Heron from Gutsy"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by eludlow on 2008-04-24
Upgraded today from Gutsy to Hardy Heron using the update manager.

All fine apart from problems with my graphic cards.  I've got an nvidia GeForce FX 5600, and when I first booted with Heron it told me I had to use low graphics settings, so can't get out of 800 x 600, and this is all I can get.  I've tried installing the drivers using EnvyNg but I still get the same thing.

Anyone else had problems?

Thanks,
Ed Ludlow

---

### Post by GeekGirl1 on 2008-04-24
EnvyNG worked for me OK. GeForce 7900GTX. Did you reboot after the install? 

Did you use the NVidia X-Server Settings to change resolution? It's just like the MS Windows control panel version. In KDE, it's under System --> NVidia Settings.

If it's missing, then find it in the package manager under "nvidia-settings".

---

### Post by eludlow on 2008-04-24
Yup restarted after installing EnvyNG, and then once the drivers installed with Envy, it tells me operation complete OK and I restart again.

When I launch NVidia X-Server settings, I get "you do not appear to be using the nvidia X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server"

So I run nvidia-xconfig as root, and I get:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

So I then run:
sudo /etc/init.d/gdm restart
and the X server restarts, and then the same thing happens again! "low graphic settings" and I still get the same when I try and go to the NVIDIA x server settings.

Any more ideas?

Ed

---

### Post by Falcorian on 2008-04-24
I'm using a 8800 GTS 640, and it worked fine on my first start up, but then complained about low graphics mode every other time.

I fixed this by installing the drivers nVidia provides on their site ([http://www.nvidia.com/object/linux_display_amd64_169.12.html](http://www.nvidia.com/object/linux_display_amd64_169.12.html)). Note, they may use a different driver for your card.

I haven't tried using apt-get to install the drivers, I plan to when I get home though.

---

### Post by GeekGirl1 on 2008-04-24
You might want to try editing your xorg.conf file. I did a google search on "you do not appear to be using the nvidia X driver" and got a bunch of hits.

See if your video driver is "nv" instead of "nvidia".

Caution: if the file doesn't work, you crash the X-server (ctl-alt-backspace to exit), or better to search this forum on how to start / stop the X-server from a terminal.

I can't help much further, as I don't have the problem.

Update to Falcorian: Additional info - EnvyNG installs the latest drivers direct from NVidia.

---

### Post by Falcorian on 2008-04-24
> **GeekGirl1 said:**
> You might want to try editing your xorg.conf file. I did a google search on "you do not appear to be using the nvidia X driver" and got a bunch of hits.

See if your video driver is "nv" instead of "nvidia".

Caution: if the file doesn't work, you crash the X-server (ctl-alt-backspace to exit), or better to search this forum on how to start / stop the X-server from a terminal.

I can't help much further, as I don't have the problem.

nv or nvidia tells it what drivers to use. If they drivers are infact installed though that will probably work!

> **GeekGirl1 said:**
> 
Update to Falcorian: Additional info - EnvyNG installs the latest drivers direct from NVidia.

Thanks, but I prefer not to use scripts. I'd rather hand install (so I know what's been done) or use apt (so I can forget it). ;)

---

### Post by eludlow on 2008-04-26
Still having massive problems with this - getting nowhere :(

I've tried installing the drivers using Envy, installing them manually from nvidia (despite problems with compiler mismatch versions, sorted now..) and I'm still getting nowhere.

All methods say they've installed successfully, but I'm still only able to run in low-graphics mode, using the graphics card driver "vesa - Generic VESA-compliant video cards".  As soon as I try and select either nv or nvidia drivers, the graphics test fails.

Help!

Thanks,
Ed Ludlow

---

### Post by allywilson on 2008-04-26
eludlow - I had EXACTLY the same issue. I'll go through my steps to see if it helps you.

After Hardy installed and rebooted, I got the low-graphics message.
I copied my backup xorg.conf to be the live file again - no luck.
I ran Envy - no luck.
I downloaded and installed EnvyNG - no luck.
I manually selected the v96 driver in EnvyNG (defaults to v169). No luck.
After numerous beers, I scrapped EnvyNG as it just wasn't working. Downloaded the latest (169.***) driver from Nvidia, booted into init 3 mode ran their driver installation and followed ALL of their default settings. Rebooted. Et voila. Atleast for me anyways :-\ 

I'm guessing that the 169.whatever that Envy downloads is perhaps different from the 169.whatever driver that Nvidia currently have on their site?

Oh, I'm using an Nvidia 5200 128Mb on Hardy 64-bit. Having sound problems still...but that's for another forum ;-)

Hope the above helps mate.

Cheers,

Ally

---

### Post by eludlow on 2008-04-26
allywilson - thanks for that - still not getting me anywhere though :(

When you say you installed the drivers manually, I take it that was the NVIDIA-Linux-x86_64-169.12-pkg2.run package?  What default settings did you let it run, it's not really asking me much when I install..?

Thanks,
Ed

---

### Post by esdaniel on 2008-04-26
Ed, not sure this is best advice but... in my case after upgrading I was not booting into the latest kernel update as my grub had not been correctly configured during upgrade (ps. using grub2) thus when I came up against the challenge of video drivers I was on a goose chase i.e. problem wasn't drivers, it was correct driver for kernel - I can well imagine downloading the nvidia drivers from nvidia working for users as their setup pack normally compiles the driver client side for the kernel it is running on.

What you might like to do is purge all nvidia:
sudo apt-get --purge remove nvidia

Thus starting from a blank slate then:
sudo apt-get install nvidia-glx-new nvidia-settings

Then to ensure you can log in and fiddle with settings in GDM:
sudo dkpg configure -phigh xserver-xorg

Fyi I skipped the dpkg line and just did a cp of my xorg.conf backup to xorg.conf.

I don't think you need to reboot but some people have been saying so... otherwise:
sudo /etc/init.d/gdm restart

I hope that works for you and re-check your grub has correctly updated so you're booting into the latest kernel.

Also while EnvyNG and Automatix have a lot of fans it might be best you handle this manually to know exactly what you've tweaked/configured.

---

### Post by kvillage on 2008-04-26
I'm having a nvidia problem, too. Nvidia drivers did not work after having upgraded to 8.04. I'm running server kernel due to 4 GB RAM setup (instead of building new kernel) with Xubuntu-Desktop. Worked fine for me in 7.10. - Easy setup with envy.

I tried everything (nvidia.com drivers, envyng, reinstallation of OS). It seems that there exists no nvidia module for that kernel. The proprietary drivers setup encounters an error about a non-compatible kernel (message about using a Xen kernel or a modified kernel, both is not correct in my case) when trying to create nvidia module. I don't know how to fix this except of returning to 7.10.

--> nvidia and nv both work with standard generic kernel (but only 2.7 GB of RAM).

---

### Post by jblackhall on 2008-04-26
I think at least for me, esdaniel's comment nailed it.  I preserved my menu.lst during upgrade (because I didn't want to lose my option to boot into Windows, not realizing that this would screw things up for me.  Does anyone know how to get a correct menu.lst so I can boot into the correct kernel?

---

### Post by eludlow on 2008-04-26
I did the same as you jblackhall - I'm currently downloading 8.04 so I can burn a copy.  I think I can then boot from the CD and re-install GRUB.

Will let you know..!

---

### Post by jblackhall on 2008-04-26
I've got my kernel correct now eludlow, see here:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)

To check what version of the kernel you're booted into, run this from Terminal:
```
uname -a
```

Basically if you were upgrading to Hardy and when prompted about your menu.lst file you told it to "keep my version" as opposed to "use the package maintainer's version" it will keep you booting into the old gutsy kernel 2.6.22-14.  Even running sudo update-grub will not fix your menu.lst.  The way I fixed it was to open Synaptic and uninstall anything kernel related that was installed for version 2.6.22-14.  If you do this, make sure there is a current version of whatever you're uninstalling (version 2.6.24-16).  I believe there were 5 or 6 total things to remove, all packages had the first word "linux" (to help you locate them in Synaptic).

I will try the nvidia drivers next.  I just wanted to let you know about this.

---

### Post by jblackhall on 2008-04-26
I am verifying that running the correct kernel version for hardy (2.6.24-16) lets the nvidia restricted graphics drivers work correctly.  If you'd like to check if you're running the correct kernel version, run "uname -a" (without quotes) in the terminal.  If it shows 2.6.22-14 (or anything besides 2.6.24-16 or greater) you're not booted into the right one.

---

### Post by eludlow on 2008-04-26
Woo hoo problem solved!  Updated GRUB to point to the correct kernel version, and first boot and all is good.

Ed

---

### Post by mamanga on 2008-04-26
install:

 "sudo apt-get install displayconfig-gtk"

and

sudo displayconfig-gtk

change resolution Monitor

---

### Post by quantumkit on 2008-04-26
I had the same problem after upgrading and I was using the Nvidia driver from their website. But the fix is simply rerun the installer script (i.e. NVIDIA-Linux-x86_64-169.12-pkg2.run) and everything is fine now =)

---

### Post by kvillage on 2008-04-26
I've just built a new kernel and was able to compile nvidia modules for it using nvidia's driver setup but there is still the same problem when trying to load these modules while generic kernel works fine. 

Anyone else who tries to install nvidia driver in a 32 bit kernel with PAE enabled?

---

### Post by buzzbo on 2008-08-03
> **allywilson said:**
> eludlow - I had EXACTLY the same issue. I'll go through my steps to see if it helps you.

After Hardy installed and rebooted, I got the low-graphics message.
I copied my backup xorg.conf to be the live file again - no luck.
I ran Envy - no luck.
I downloaded and installed EnvyNG - no luck.
I manually selected the v96 driver in EnvyNG (defaults to v169). No luck.
After numerous beers, I scrapped EnvyNG as it just wasn't working. Downloaded the latest (169.***) driver from Nvidia, booted into init 3 mode ran their driver installation and followed ALL of their default settings. Rebooted. Et voila. Atleast for me anyways :-\ 

I'm guessing that the 169.whatever that Envy downloads is perhaps different from the 169.whatever driver that Nvidia currently have on their site?

Oh, I'm using an Nvidia 5200 128Mb on Hardy 64-bit. Having sound problems still...but that's for another forum ;-)

Hope the above helps mate.

Cheers,

Ally

This worked perfectly for me!  I was a little worried when the gcc versions didn't match up exactly, but here I am typing in 1440x900, so I am super happy now.

Buzz

---

