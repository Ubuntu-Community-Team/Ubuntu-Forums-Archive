---
title: "how to uninstall nvidia drivers"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Herix on 2007-06-23
I Installed my nvidia drivers for my 7800 gtx card and now I cant start gdm. Can sombody tell me how to uninstall the nvidia drivers so I can start X again?

---

### Post by Cappy on 2007-06-23
```
sudo dpkg-reconfigure xserver-xorg
```
select "nv" for the first screen and hit enter until it's done.
Then you can
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```
and it should let you back in X.

---

### Post by Herix on 2007-06-23
I did that and I got x on again. However, I'm trying to reinstall my nvidia drivers but it detects a previous installation. Is there a way in which I can completely remove everything regarding the drivers so I can do a clean isntall?

---

### Post by Cappy on 2007-06-23
Here's what I use for my Feisty:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

---

### Post by Herix on 2007-06-24
Thx a lot. I did that and then reinstalled my drivers and everything is good. (I didnt install the restricted modules and glx though because I read in other forums that is not good).

Now, since Im new to ubuntu, I dont know how to test my card. Im talking about something similar to the way you can test direct3D in windows so you can see the graphics in action. Is there something like that in Ubuntu?

---

### Post by fakie_flip on 2007-06-25
Here's what I did. I removed all the ubuntu junk like you did and then I got the latest driver from here.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Then the gui must be shut down.

sudo /etc/init.d/gdm stop

You need gcc and other packages for building the nvidia kernel module.

sudo apt-get install build-essential pkg-config

Make the script executable and run the script that was downloaded from nvidia's website for example if you downloaded this one.

sudo chmod a+x NVIDIA-Linux-x86_64-100.14.11-pkg2.run

Then run it.

sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run

Then it will ask you questions and automatically configure your /etc/X11/xorg.conf file, so that you don't have to touch it.

Power back on the gui.

sudo /etc/init.d/gdm start.

Next time you want to update your driver, it is much easier.

Power down the gui.

sudo /etc/init.d/gdm stop

sudo nvidia-install --update

It will download a newer version if there is one and install it.

Bring the gui back up.

sudo /etc/init.d/gdm start.

---

### Post by Surkow on 2007-06-25
> **Herix said:**
> Thx a lot. I did that and then reinstalled my drivers and everything is good. (I didnt install the restricted modules and glx though because I read in other forums that is not good).

Now, since Im new to ubuntu, I dont know how to test my card. Im talking about something similar to the way you can test direct3D in windows so you can see the graphics in action. Is there something like that in Ubuntu?

You should try the command "glxgears". Type "man glxgears" for more info.

```
The glxgears program is a port of the ‘‘gears’’ demo to GLX. It displays
a set of rotating gears and prints out the frame rate at regular intervals.
It has become quite popular as basic benchmarking tool.
```

---

