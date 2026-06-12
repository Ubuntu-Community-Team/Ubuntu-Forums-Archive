---
title: "Installing and running DWA-130"
date: 2008-08-17
forum: x86 64-bit Users
---

### Post by Cokemonkey on 2008-08-17
Hello there, I'm attempting to install a D-Link Wireless N USB Adapter on my x64 ubuntu 8.04 machine.

I have searched the web extensively but i've been unable to find a list of directions that make sense.

I understand I need ndiswrapper/ndisgtk in order to properly use the windows .sys files located on the driver installation CD that came with the adapter. I cannot figure out how to install and run either one, although I understand ndisgtk is just a GUI of ndiswrapper.

Thanks in advanced,

---

### Post by cariboo on 2008-08-17
The ndiswrapper files you need are located on the Cd you used to install Ubuntu.

Go to System-->Administartion-->Synaptic Package Manager, once the program has opened, make sure your CD is in the drive, click the seach button and enter ndiswrapper in the seach box, it should list the three programs you need, just right click and choose mark for installation for each one, then click apply, click apply again on the window that pops. This will install the programs you need. Once they are installed, go to Syatem-->Administration and ndisgtk should be in the list, it may say something about wireless drivers. I nowhere near my laptop so I can't check exactly what it says.

Jim

---

### Post by Cokemonkey on 2008-08-17
when i put the cd in and search for the 3 things, it tells me i'm reinstalling them, which tells me I already have them. However I'm continuing with your instructions and "reinstalling".

"successfully applied all changes"

now I see "windows wireless drivers" which is what I think you were talking about (in administration menu)

installed the .inf, thank you very much it seems to be working!

Now the importnat part. Following the tutorial here:
[http://www.linuxquestions.org/questions/linux-hardware-18/wireless-usb-device-dwa-130-on-ubuntu-583189/](http://www.linuxquestions.org/questions/linux-hardware-18/wireless-usb-device-dwa-130-on-ubuntu-583189/)
When I click on configure network, I don't see wireless connection.

I get this:

[img]http://filesmelt.com/Imagehosting/pics/bfe317a8d586fa1e96f7c53c2d65ada8.png[/img]

---

### Post by Cokemonkey on 2008-08-18
*bump*

---

### Post by Cokemonkey on 2008-08-20
*bump*

---

### Post by Cokemonkey on 2008-08-21
*bump*

---

### Post by Yellow Pasque on 2008-08-21
I'm not used to using a GUI for this, but I think I know where you're at.
First, verify the .inf installed
```
ndiswrapper -l
```
Make sure the kernel module can load:
```
sudo depmod -a
sudo modprobe ndiswrapper
```
If the following command returns driver=ndiswrapper for your wireless card, then the driver is installed:
```
sudo lshw -C network
```
Now, we need to create the interface and tell Ubuntu to load the kernel module:
```
sudo ndiswrapper -m
sudo echo ndiswrapper >> /etc/modules
```
Reboot.

---

