---
title: "Nvidia driver installation"
date: 2009-01-17
forum: x86 64-bit Users
---

### Post by Roaster on 2009-01-17
Hello all, I am running Ubuntu 8.04.1 and I am a fairly new Ubuntu user. I have downloaded the latest Nvidia driver from the Nvidia website(NVIDIA-Linux-x86_64-180.22-pkg2.run). Can some one please guide me thru the installation of this driver? If this has been asked before I apologize, but I really would appreciate your help.Thanks, Frank

---

### Post by EXCiD3 on 2009-01-17
You will need to be in a console to do most of this so press Ctrl-Alt-F1 and login
Disable the xserver by running "sudo /etc/init.d/gdm stop"
cd to where you saved the file
Run "chmod +x NVIDIA-Linux-x86_64-180.22-pkg2.run" to make the file executable
Now run "sudo ./NVIDIA-Linux-x86_64-180.22-pkg2.run" to start installation
Re-enable the xserver by running "sudo /etc/init.d/gdm start" and you should be good to go!

Its still recommended to use System->Administration->Hardware Drivers to install the Nvidia driver (but it might be slightly out of date). You can also use Envyng to install the Nvidia driver for you instead of using the commands above. Good luck!

---

### Post by shrekfx on 2009-01-17
I used the hardware drivers under system and it worked great. so far no crash or bugs or glitches... I tried the manual download from nvidia and try to install it and just couldnt get it to work.

---

