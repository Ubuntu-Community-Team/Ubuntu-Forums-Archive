---
title: "X Server error after install"
date: 2006-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by jiub on 2006-03-23
I've new to Linux and new to the forums, I hope someone can help me with this:

I have been trying to setup Ubuntu 5.10 in a dual boot setup. I have 3 hard drives, an 80GB on Master, an 80GB on Slave, and 250 on SATA. The Master has a 60GB (NTFS) for Windows, 20GB for Ubuntu (~18GB / (root?) and 
~2.5GB Swap). The slave is /home as XFS (This will eventually be used with MythTV and that is the recommended file system). 250GB will stay NTFS for use with windows.

Setup runs fine until it tries to setup X Server. I receive an error "Failed to start the x server (yoru graphical interface). It is likely that it is not set up correctly." Then asks if I would like to view two log files. Looked through them but I don't understand any of it. I have tried installing 3 times and it always dies here.

System specs:
AMD Athalon 64 3200+
ATI Radeon x800 (PCI-E x16)
ATI TV Wonder VE capture card
1GB (2x512MB PC3200 RAM)
DVD ROM + DVD RW
Hard drives as above
Motherboard is nVidea nForce 4 chipset

Any help much appreciated. Ask for anymore information you need, hopefully I covered most of it. Also, hope I got the terminology right. Thank you.

---

### Post by Sutekh on 2006-03-23
Try running this from the command line
```
sudo dpkg-reconfigure xserver-xorg
```
When prompted for a password, use your user's login password.

You will be led through a number of questions regarding your keyboard, mouse and monitor.  When unsure about how to answer, just accept the default/suggested values.

That should get you back and running.

---

### Post by jiub on 2006-03-23
Thanks for your help. 

I ran that and went through all of the configuration screens. However, when I get done it goes back to the command line and I don't know how to try and restart xserver. Trying to reboot goes back to the same screen

---

### Post by Sutekh on 2006-03-23
Well I don't know if it will help but try
```
sudo /etc/init.d/gdm stop
```
Then```
apt-get -f install
apt-get install ubuntu-desktop
```
(to see if any packages are not installed properly/missing)

Then
```
sudo dpkg-reconfigure xserver-xorg
```
Then```
sudo /etc/init.d/gdm start
```
To restart X

Otherwise have a look through the error logs for lines with (EE) in them.

---

### Post by jiub on 2006-03-23
I tried that but it gave me the same error after I tried restarting. Going through the server output I found:

skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:mdebug_xform.o":No Symbols found
EE No devices detected

Just a quick side question: I've seen it 3 times now, what does "sudo" mean/refer to?

---

### Post by Sutekh on 2006-03-23
[QUOTE=jiub]I tried that but it gave me the same error after I tried restarting. Going through the server output I found:

skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:mdebug_xform.o":No Symbols found
EE No devices detected[/QUOTE]

I meant to post this last time, sorry.  When you get to this step
> For the X Window System graphical user interface to operate correctly, it is necessary to select a video card driver for the X server.
Drivers are typically named for the video card or chipset manufacturer, or for a specific model or family of chipsets.
Select the desired x server driver:
apm, ark, ati, chips, cirrus, cirrus_alpine, cirrus_laguna, cryix, fbdev, glide, glint, i128, i740, imstt, mga, neomagic, newport, nsc, nv, rendition, riva128, s3, s3virage, savage, siliconmotion, sis, tdfx, tga, trident, tseng, vesa, vga, via, vmware.
What options did you choose?  Try vesa.  Actually I think it must be the ATI card, I'll have to look into that.

So try the dpkg-reconfigure command and choose 'vesa', then the gdm start command when you are finished, then you'll need to get the ATI drivers.

[QUOTE=jiub]
Just a quick side question: I've seen it 3 times now, what does "sudo" mean/refer to?[/QUOTE]
**sudo** means super-user do.  I don't expect that to mean anything to you yet though.  

In Ubuntu the normal user is not allows to perform tasks that could potentially mess up your system.  To perform system wide changes the command sudo is appended to the beginning of a command. 

That was a pretty weak explanation, but I can link you to a much better one.

[Ubuntu Wiki -  RootSudo](wiki.ubuntu.com/RootSudo)

---

### Post by Sutekh on 2006-03-23
Okay, after some reading a quick fix would be to run the ```
sudo dpkg-reconfigure xserver-xorg
```
command and choose **vesa** for the driver. 

OR

Edit the xorg configuration file manually and change the driver to "vesa".

These commands will copy the Xorg configuration file to a backup file and then edit it using the very simple editor **nano**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

Find the part of the file with (it won't look exactly like this though)
```
Section "Device"
Identifier "ATI x800"
**Driver "ati"**
BusID "PCI:1:0:0"
```Change the **Driver** line so that it reads
```
Driver "vesa"
```
Save the file (Ctrl+O) and exit (Ctrl+X)

Then start the graphical interface
```
sudo /etc/init.d/gdm restart
```



If you get into GNOME, then you are halfway there.  Those "vesa" drivers are just the quick fix.  You should look into installing the ATI drivers.

You can try either this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)

---

### Post by jiub on 2006-03-23
Thanks a lot for all of your help. I need to call it a night right now (early class in the morning) but I'll try that as soon as I get back tomorrow and post back the results.

---

### Post by jiub on 2006-03-23
Well, not quite sure what happened. I didn't have time to try the next step last night so I booted back to windows to make the last post. When I went to shutdown I must have hit restart by mistake, and when I woke up this morning it was sitting at the login screen and is working flawlessly. Restarted a few times and always comes up fine.

Thanks a lot.

---

### Post by Sutekh on 2006-03-23
Okay thats good to know.

What was the last thing you tried before it worked?

---

### Post by jiub on 2006-03-24
The last thing I did was the x-server configure thing while selecting vesa drivers. Restarting the computer and restarting the interface didn't work that night but for some reason it worked that one time and has been running great since.

Thanks a lot!

---

### Post by Adler on 2006-03-25
Sutekh,

Thanks for your responses here. I just had the same problems as the original poster. You saved the install. Thanks!

I have just gotten a new COMPAQ 64-Bit Workstation and I was trying out SuSE 10, KBUNTU and settled on UBUNTU because it is native 64-Biy, SuSE isn't.

Adler

---

