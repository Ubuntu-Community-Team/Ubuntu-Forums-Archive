---
title: "Wireless Woes..."
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by joey-elijah on 2008-06-04
Using Ubuntu Hardy 64bit if that makes any differences, anyway. I have a USB Wifi stick thing that my desktop uses to connect to the wireless hub. It's a "ez connect N SMCWUSBS-N2" affair.

I installed ndiswrapper and installed windows xp drivers like so: -

```
ndiswrapper -i xpdrivercode.inf

ndiswrapper -m

ndiswrapper -l
```

which happily told me:

```
xpdrivercode : driver installed
        device (XXXX:XXXX) present
```

Awesome.

```
sudo modprobe ndiswrapper

sudo ndiswrapper -m
```

Somewhere along the lines i got an error that said 

> module configuration already contains alias directive

And going into system>admin>network - everything was greyed out.

Help?

---

### Post by sam_delta on 2008-06-04
i dont know what your problem is, but i MIGHT be able to help 
can you post the output of the following commands please```
cat /etc/modprobe.d/ndiswrapper
iwconfig
lshw -C network
```
sam

---

### Post by joey-elijah on 2008-06-05
okay... 

> joey@joey-desktop:~$ cat /etc/modprobe.d/ndiswrapper
alias usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp8B5Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp8B5Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v083ApB522d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v083ApB522d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip* ndiswrapper
joey@joey-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

joey@joey-desktop:~$ sudo lshw -C network
joey@joey-desktop:~$    

hmm.

ndiswrapper says the driver is installed and 
> joey@joey-desktop:~$ ndiswrapper -l
rt2870 : driver installed
	device (083A:B522) present


---

### Post by sam_delta on 2008-06-05
i duno whats wrong, in order to know your exact wireless card model, can you post the ouput of ```
lsusb
``` with the wireless model , ill try to to find out whats happening by doing some research, ill do my best

also, about the system>admin>network being grayed out, its always like that, for security reasons, you have yo unlock it before making any changes, to unluck it ,simply press the unlock button at the buttom of the network window, it will prompt you with your password and everything will be unlocked  (not grayed out)

sam

---

### Post by wdaniels on 2008-06-22
> **joey-elijah said:**
> Using Ubuntu Hardy 64bit if that makes any differences

Yes it does, you will need to use specifically the 64-bit XP drivers (which do seem to be available at least from what I can see in the download from the [OEM site]("http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_GBR&knowsPartNumber=false&productCategory=5&modelNumber=1653&partNumber=4193&downloadType=1&os=8")). Probably if you do something like:

```
dmesg | grep ndiswrapper
```

(or otherwise look though the system logs manually) I expect you will find a message telling you this, I just don't remember the exact wording.

I don't have this card myself and can't find any information to say whether or not these drivers will work with ndiswrapper anyway though...perhaps you can report one way or the other?

---

### Post by joey-elijah on 2008-06-25
the disc does have the xp64 driver, so i'll try

---

### Post by joey-elijah on 2008-06-26
> **sam_delta said:**
> i duno whats wrong, in order to know your exact wireless card model, can you post the ouput of ```
lsusb
``` with the wireless model , ill try to to find out whats happening by doing some research, ill do my best

also, about the system>admin>network being grayed out, its always like that, for security reasons, you have yo unlock it before making any changes, to unluck it ,simply press the unlock button at the buttom of the network window, it will prompt you with your password and everything will be unlocked  (not grayed out)

sam


Bus 002 Device 006: ID 083a:b522 Accton Technology Corp. 
Bus 002 Device 004: ID 0d49:7310 Maxtor 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 003: ID 06a3:8020 Saitek PLC 
Bus 001 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 0000:0000

---

