---
title: "Ubuntu and 9600 GT"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by Roaster on 2008-06-25
Hello everyone, I just installed a new 9600GT video card in this computer and when I boot into 8.04 it goes as far as a screen with the Nvidia logo and stops! I'm sure I need a new driver but at this point I do not know what to do. I am dual booting with Vista 64bit(using Wubi).  Any help greatly appreciated. Thanks

---

### Post by blastus on 2008-06-25
Download the 64 bit driver from [http://www.nvidia.com/object/linux_display_amd64_173.14.09.html](http://www.nvidia.com/object/linux_display_amd64_173.14.09.html)

[CTRL-ALT-F1]
[login]
sudo /etc/init.d/gdm stop
sudo apt-get install build-essential
sudo sh NVIDIA-Linux-*.run (the NVIDIA package)
sudo nano /etc/default/linux-restricted-modules-common
  [Change DISABLED_MODULES="" to DISABLED_MODULES="nv"]
sudo reboot

---

### Post by screaminj3sus on 2008-06-25
thanks installing ubuntu on my 9600gt pc now, hopefully all goes well :)

---

