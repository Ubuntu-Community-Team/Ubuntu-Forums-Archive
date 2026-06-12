---
title: "how to compile a custom version of Wine for an ARM processor"
date: 2017-04-28
forum: Wine
---

### Post by sebastian.vignone on 2017-04-28
I'm runnning Crouton with lxde desktop environment and I've been trying to find a way to get my hands on a working copy of Wine for my Acer Chromebook 13 (NVIDIA Kepler Tegra K1) but I'm coming up empty. I just read on the WineHQ website that it is possible to compile a custom copy of Wine specifially for an ARM based computer, but as I am new to Linux, I don't even know where to begin. Any help would be greatly appreciated!

---

### Post by Edward_Fish on 2017-04-30
You *can* compile Wine for an ARM processor, however you will only be able to run Windows applications compiled for ARM processors. You will *not* be able to run Windows applications compiled for Intel x86 or 64 processors (very likely every available .exe will be compiled for Intel processors). If this is what you want, follow the instructions below. If this is not what you want, you must look into a hardware virtualisation solution such as QEMU ([www.qemu-project.org]("http://www.qemu-project.org")) or Bochs ([http://bochs.sourceforge.net/](http://bochs.sourceforge.net/)) to emulate Windows or ReactOS. Operating system emulators such as VirtualBox and VMWare will *not* be able to run Windows or ReactOS.

Note: commands to type are indicated using backticks (`). For example if a message says to:
Display the current directory with `pwd`
then you would type into the terminal window:
pwd
Glad we've cleared that up.

First off, go to the target machine and open a terminal. Download the Wine source code with the command `git clone git://source.winehq.org/git/wine.git`. A new folder named wine will be created in the location that you ran the command (most likely the home directory). Change to this folder with `cd wine`, then build Wine with `./configure && make && sudo make install`. If all goes well, you should return the command prompt after a while (think in hours) without any errors. If you need to enter a password for sudo, do it. However the most likely outcome is that it will say that a package or some libraries aren't installed after being run for just a few seconds. When this happens, just search for the error message to find out what to install, then go back to running `./configure && make && sudo make install`. Let me know if there's an error that you don't know how to solve or can't find info on.

Good luck!

---

