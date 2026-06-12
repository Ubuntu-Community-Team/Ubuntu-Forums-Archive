---
title: "USB-Device connection in WINE"
date: 2014-12-20
forum: Wine
---

### Post by yooooy on 2014-12-20
Hi guys!
 

 I just bought a nice USB-oscilloscope but its software runs in Windows only. I tried to run it in WINE but it tells me that no device is connected. There is a forum for this  oscilloscope and some user suggested to run the following commend to map the scope to the WINE-emulator:
ln -s /home/USER/.wine/dosdevices/com1 /dev/ttyUSB0
 
 My scope is attached to ttyUSB3 port.  
 
 When I run this command I get following message (it's in German so I have to translate it but I'm not sure if I'm using proper technical terms):
symbolic conjunction &#8220;/dev/ttyUSB3&#8221; could not have been established: file already exists
Well something like that.  

 I have no skills in Linux at all so I depend on your help to figure it out. Could somebody look in to it? It would be great! I just don't want to go back to Windws, it's not an option!!! :D

My Ubuntu Version is 14.04.1 LTS and WINE version is wine1.6 1:1.6.2-0ubuntu4


 
 Cheers!
 
Robert.
 

 PS:
 Here is the link to the forum:
 [http://dpscope.freeforums.org/dpscope-software-under-linux-using-wine-t62.html](http://dpscope.freeforums.org/dpscope-software-under-linux-using-wine-t62.html)

---

### Post by hojat2 on 2014-12-27
sorry for this , before you buy a device chcek it for your OS
method 1:
You can Install virtualbox and install win Xp and use your scop !
dont forget this code after virtualbox install
```
usermod -a -G vboxusers username 
```
method 2:
and I find a code for USBasp not for your program
with This code program work correctly ! try to use this code with change for your scop
```
 SUBSYSTEM=="usb", ATTR{product}=="USBasp", ATTR{idProduct}=="05dc", ATTRS{idVendor}=="16c0", MODE="0666"
```

---

