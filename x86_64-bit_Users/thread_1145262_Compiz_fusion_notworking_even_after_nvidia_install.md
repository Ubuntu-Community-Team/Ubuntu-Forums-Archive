---
title: "Compiz fusion notworking even after nvidia install"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by akshay.sulakhe on 2009-05-01
Hello friends...Just installed Ubuntu 9.04 which is an AMD quad core 9950(BE),mother board Asus M3A78-Em....and graphics card is nvidia 9600 GT...512 mb...
After installing Ubuntu i tried hardware drivers,but it said that no hardware found...so i downloaded the driver and installed it manually..after reboot nvidia x server settings never appeared,and when i checked hardware drivers it told me to install the driver...so i did...some 180 ver...but still the desktop effects could not be enabled...plz help..

---

### Post by jbrown96 on 2009-05-01
Try to open nvidia-settings. You may need to install it first. ```
sudo apt-get install nvidia-settings
``` Look around and try to find your driver version.


```
glxgears
``` It should open a window that has three spinning gears. If you can see them, then the driver is working. Just toggling the proprietary drivers in System--->Admin--->hardware drivers. It sould eventually wise up. 

When you installed the drivers manually, did you let Nvidia automatically create a xorg.conf for you?

---

### Post by akshay.sulakhe on 2009-05-02
yes..i let it update my xorg file...here is log of ur commands...
akshay@Akshay-desktop:~$ sudo apt-get install nvidia-settings
[sudo] password for akshay: 
Sorry, try again.
[sudo] password for akshay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
The following packages were automatically installed and are no longer required:
  python-mutagen python-qt3 python-kde3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
akshay@Akshay-desktop:~$ glxgears
Error: couldn't get an RGB, Double-buffered visual
akshay@Akshay-desktop:~$ 

whats that...Thanks...do reply....

---

