---
title: "[SOLVED] nvidia hardware drivers"
date: 2008-06-05
forum: x86 64-bit Users
---

### Post by woelf on 2008-06-05
[ATTACH]73006[/ATTACH]
If I Enable this driver and restart a get black screen.

Asus Barebone T3-M3N8200 MCP78S, SATA2, VGA nVidia Geforce 8
AMD Athlon 64 X2 4800+ 2.5GHz AM2 65W
Asus DVD-/+/RAM 2014S1 20x/20x/14x
Corsair 2x1GB DDR2 SDRAM PC5300 CL4.0 TwinX
Samsung 500GB SATA300 16MB, HD502IJ

(When I install Ubuntu 8.04 LTS desktop 64bit AMD I have to do this, go to install Ubuntu press f6 en type  in all_generic_ide then enter)

---

### Post by Sef on 2008-06-05
> VGA nVidia Geforce 8

Which card exactly?  I have an 8600 and it works just great.

---

### Post by woelf on 2008-06-05
VGA onboard: Integrated GeForce 8 GPU
Chipset: nVidia MCP78S

Resolution is now maximal 1280 x 1050 without the driver I need 1680 x 1050

---

### Post by Sef on 2008-06-05
You could download the drivers from [NVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us").  Not sure how easy or hard it is.

---

### Post by woelf on 2008-06-05
hard try that same problem.

---

### Post by philinux on 2008-06-05
i would try envyng then from synatic.

---

### Post by woelf on 2008-06-05
Envying does not recognize your card.
manual get only low-graphics mode.

---

### Post by woelf on 2008-06-06
If I download de driver from nvidia I get
no precompiled kernel interface was found

---

### Post by tenmoi on 2008-06-06
woelf,

sudo apt-get install build-essential libxft-dev

then 
Alt + Ctrl + F1

sudo /etc/init.d/gdm stop

sudo sh your Nvidia driver.run

follow instructions on screen. no precompiled kernel interface will be found, so you just hit "accept" and the installer will compile one for you. just hit OK or accept all the way from now on and you're good to go.

then 
sudo /etc/init.d/gdm restart.

good luck.

I am running X86_64_173.08.

---

### Post by woelf on 2008-06-06
[ATTACH]73122[/ATTACH]
try it resolution is now 800 x 600.
[ATTACH]73123[/ATTACH]
looks like no video card ?

---

### Post by razvi on 2008-06-06
Try
sudo apt-get install nvidia-glx-new
in a console. It should work.

---

### Post by tenmoi on 2008-06-06
> **woelf said:**
> [ATTACH]73122[/ATTACH]
try it resolution is now 800 x 600.
[ATTACH]73123[/ATTACH]
looks like no video card ?


Woelf,

My xorg.conf is exactly the same as yours.

You must purge-remove all the linux-restricted-modules* for the Nvidia driver to be functional. Open synaptics. Search for the modules. Remove them and if things don't improve, you should sudo NVidia.run --uninstall and then reinstall the driver.

bie.

---

### Post by woelf on 2008-06-08
Resolution is now maximal 1024 x 768 still need 1680 x 1050

---

### Post by tenmoi on 2008-06-09
First back up your xorg.conf and modify it to look like this:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes		[COLOR="Red"]"1680 x 1050"[/COLOR] "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

Save and reboot.

bie.

---

### Post by woelf on 2008-06-10
solved

it works thanks Tenmoi


get the driver NVIDIA-Linux-x86_64-173.14.05-pkg2.run form  Nvidia website .
Move the file to home directory.
Open terminal 
sudo apt-get install build-essential libxft-dev
Open synaptic Search nvidia remove all linux-restricted-modules
Alt+Ctrl+F1
sudo /etc/init.d/gdm stop
sudo chmod a+x NVIDIA-Linux-x86_64-173.14.05-pkg2.run
sudo sh  NVIDIA-Linux-x86_64-173.14.05-pkg2.run
sudo /etc/init.d/gdm restart
open terminal 
sudo /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf 
insert the color line

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
[COLOR="Red"]Modes "1680 x 1050" "1280x1024" "1024x768" "800x600" "720x400" "640x480"[/COLOR]
EndSubSection

save and reboot

---

### Post by woelf on 2008-06-10
did a new install of ubuntu and this works

choose languages go to install ubuntu press f6
type all_generic_ide enter
update
(sudo apt-get install ubuntu-restricted-extras)

get the driver NVIDIA-Linux-x86_64-173.14.05-pkg2.run form Nvidia website 
Move the file to home directory.
Alt+Ctrl+F1
sudo apt-get install build-essential libxft-dev
sudo /etc/init.d/gdm stop
sudo chmod a+x NVIDIA-Linux-x86_64-173.14.05-pkg2.run
sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run
sudo /etc/init.d/gdm restart
Go to Systeem-->Preferences-->Appearance-->Visual effects--> mark none

---

### Post by caladeira on 2008-06-10
Hello woelf,

I'm glad you've solved your problem.

I have the intention to get one of these boxes, however as a result of previous experiences with asus barebones, I'd like to ask you three questions first:

Do you notice any problem with USB devices? External USB disks being too slow or usb keyboards not working properly.

Can you go to standby on ubuntu and then return with everithing working?

I noticed that you use the resolution "1680 x 1050", can you tell me if the "1360 x 768" is available?

Appreciate if you can answer.

Best regards.

---

### Post by woelf on 2008-06-11
caladeira,

problem with usb,

It takes 6 minutes to pass the asus screen after the start up the usb ports are not working properly.
Get message : usb 3_5 : device descriptor read/64,error-110
After finish the Ubuntu install the problem seems to be gone

standby seems no problem

resolution "1360 x 768" don't see it on my resolution list 

I test the sound and I have sound but there is a disturbance.
so next problem.

I say don't buy.
(my old computer install Ubuntu 8.04 everything works have to do nothing extra, resolution 1680 x 1050 no problem )

---

### Post by caladeira on 2008-06-11
Well, thanks for your quick answer.

I was asking this because I'm «stuck» with a Asus T3-M2NC51PV that have lots of problems with USB and I'd like to upgrade.

I've read that other T3 models for intel have the same problem.
How can they continue repeating the same errors.

And then if you go to the asus support forums, well, I don't know if you have tried to post anything but I can't find a forum for "barebones"!!!

This make us ask, how can a company like asus produce this peace of *****.

Again, thanks for your answer.

---

### Post by woelf on 2008-06-12
well still not working properly sound is disturbance.

---

### Post by netpro25 on 2008-07-02
I am having the same problem with distorted/static audio. I have the MCP78S (Geforce 8200) chipset also. I am not sure what to do.

---

### Post by TheTrlak on 2008-07-02
Hi, I installed Hardy and seems I have a black screen as well after I let it auto install drivers for my Geforce 9500. I wasnt sure if it was because its not hte right driver for my 64-bit version of my WUBI install... Ps.. wouldnt happen to know how to repair these installs once they are in this state would you?

---

### Post by TheTrlak on 2008-07-03
Well I actually just reinstalled and got a stable build going. Now the steps you guys laid out for me after I actually did research elsewhere like a dolt... now work. Well except for one problem.

When I am installing the nvida driver it goes to build my kernel and seems it stops saying error, check your logs. Something about not matching yadda yadda and has the words NVIDIA.KO for some reason. Anyone experiance this before per chance and have a possible work around?

---

### Post by woelf on 2008-07-16
ever time I have a update off the kernel.
I have to install the nvidia driver again.
As today.

sudo /etc/init.d/gdm stop
sudo sh  NVIDIA-Linux-x86_64-173.14.09-pkg2.run
sudo /etc/init.d/gdm restart

---

### Post by philinux on 2008-07-16
Yep.

Thats the reason I've just done a reinstall. Can't be bothered with that hassle every kernel update. And I didn't notice any improvement on my machine with the latest driver.

Home is on it's own partition so I was back to normal in half an hour.

Also in Intrepid they've split the driver up as well so I'm definitely sticking with the repo's.

---

### Post by LibertyShadow on 2008-07-16
There is a way to automatically update your *manually* installed nvidia driver.  See [http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573").

I have tested it out, and it seems to work well.  You will still need to reinstall the driver when you update anything related to mesa, though.

---

