---
title: "Need help with upgrade and nvidia"
date: 2009-06-21
forum: x86 64-bit Users
---

### Post by mercules2178 on 2009-06-21
I am using 8.04 right now and nvidia and compiz work just fine. I have tried upgrading and clean install of 8.10 and 9.04 and can not seem to get nvidia to work. I get to the line "checking battery state" and it just hangs. I had this problem with 8.04 when it was released and a couple of months later the restricted drivers worked for me. I have used the latest release and it seems to be a little more stable and fluid to me. The nvidia driver that I am currently using is 169.12+2.6.24.17-24.1! I believe that on boot nvidia has a problem with my monitor. It is a dell 20in widescreen and even with the current setup it is still not using the correct refresh rate. I am using an sli config with 8500gt cards. I would like to upgrade and need help, is anyone willing?

---

### Post by Arup on 2009-06-21
If you are going to stick to repos, thats the price to pay, suggest you remove that and use nvidia drivers from web to get the latest features or use a ppa and install from there. Currently you are loosing all the features of your nvidia cards. Sadly 8500GT doesnt' support VDPAU. For ppa install check out [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html) or [https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa)

---

### Post by mercules2178 on 2009-06-21
What do I need to do to remove it correctly and install the new driver?

---

### Post by Arup on 2009-06-21
> **mercules2178 said:**
> What do I need to do to remove it correctly and install the new driver?

Download the drivers and keep it in your home folder.If you installed your existing drivers via administration>hardware drivers, remove it from there, go to synaptic, remove by marking complete uninstall linux restricted modules and linux restricted modules common. Then go to terminal and type sudo apt-get install build-essential after its done, do ctrl+alt+F1, it will take you to a terminal window, login and do a sudo /etc/init.d/gdm stop after that type sudo sh NVIDIAxxxx and it will start the install process, say yes to all and then after its done, do sudo reboot, you will have the latest drivers for your card.

---

### Post by SuperSonic4 on 2009-06-21
Note that you can use tab completion to put in the name of the script. Just type in NVI and press tab

---

### Post by mercules2178 on 2009-06-21
what about Modaliases?
which driver should i use?

---

### Post by Arup on 2009-06-21
> **mercules2178 said:**
> what about Modaliases?
which driver should i use?

Modaliases are for drivers from repo, the nvidia driver which you download from their site doesn't need those.

---

### Post by mercules2178 on 2009-06-21
should i leave or remove them?
when I ran the command
sudo apt-get install build-essential
it did not install anything so I should be goog?

---

### Post by mercules2178 on 2009-06-21
now i can not boot into my .13 kernel but i can with the .11 kernel. I do not get nvidia to run on either.

---

### Post by Arup on 2009-06-21
> **mercules2178 said:**
> now i can not boot into my .13 kernel but i can with the .11 kernel. I do not get nvidia to run on either.


Did you boot into the latest kernel and remove the drivers? Also did you remove linux restricted modules and linux restricted modules common, also what driver did you download? You have to install the driver while booted into the latest kernel. If your system couldn't install build-essential that means you haven't enabled source files in synaptic repos.

---

### Post by mercules2178 on 2009-06-21
I did remove the drivers, linux restricted moduels and linux restricted modules common from the latest kernel. i tried the 173, 180, and 185 driver and how do i enable the source files.

---

### Post by Arup on 2009-06-21
> **mercules2178 said:**
> I did remove the drivers, linux restricted moduels and linux restricted modules common from the latest kernel. i tried the 173, 180, and 185 driver and how do i enable the source files.

The 173, 180 drivers should be in repos but the 185 is only available from nvidia. Did you remove previous drivers before trying out the latest?

---

### Post by mercules2178 on 2009-06-21
I started with 173 and worked my way up. During install the previous version was removed by the installer, at least that is what it said it would do. 173 failed due to the kernel version. 180 did install but it just hangs at "checking battery state". the monitor flashes three times and then sits there. How do i remove the driver and reset x so that i can log in? From there I can try again and maybe get it right?

---

