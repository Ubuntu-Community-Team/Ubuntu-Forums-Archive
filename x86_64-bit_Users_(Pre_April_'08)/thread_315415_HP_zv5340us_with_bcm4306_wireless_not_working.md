---
title: "HP zv5340us with bcm4306 wireless not working"
date: 2006-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by greenfrog on 2006-12-09
Running Edgy 64 bit and want to use kernel driver instead of ndiswrapper.

Anyone know how to get it working with the built in bcm43xx driver?

Thanks :???:

---

### Post by Nicks Spleen on 2006-12-09
I have a HP zv5200 with a bcm4306. I hated messing around with ndisrapper and found that with edgy its really easy to get the built drivers working. The only problem with them is that the max connection you are gonna get is 11 Mb/s.

type in:
sudo gedit /etc/apt/sources.list

add the firmware repository to the sources list and save:
## BCM43XX Firmware Repo
deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego bcm43xx

update the repos with this command:
sudo apt-get update

then install via synaptic the bcm43xx-firmware package or in a terminal type:
sudo apt-get install bcm43xxx-firmware

reboot and it should work, at least it did for me. I would also suggest installing the network manager. It really make changing wirless networks easier. 

You can do that with synaptic or in a terminal type:
sudo apt-get install network-manager-gnome

Hope this helps!

---

