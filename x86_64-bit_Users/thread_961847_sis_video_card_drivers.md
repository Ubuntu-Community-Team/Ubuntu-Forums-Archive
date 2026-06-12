---
title: "sis video card drivers"
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by Asherr6 on 2008-10-28
Hey guys I've been trying to find the drivers for my video card. When i finally found it (I think anyway), now i cant seem to install it. So far I've tried doing it in terminal but it usually says something to the effect of missing destination file. or permission denied. I've run it in root still same effect. I used the karchiver wizard jazz and it says "cannot find the script configure" any help would be great thanks ASher

---

### Post by Mark_in_Hollywood on 2008-10-28
Ahserr6

Tell me what version of ubuntu you are using ... Breezy, Hardy, Ibex?

The video drivers should be found on installation of the OS. And usually you need the drivers from the manufacturer, for example: ATI or NVidia. If you have an Nvidia card, we have both OSS and proprietary drivers for most if not all video cards. 

Also, open a terminal and post the output of lspci. Let's see if the card is "found" on the pci bus.

---

### Post by Asherr6 on 2008-10-28
I'm using hardy, its a sis card and i know there hard to find i've been using ubuntu for about 4 months. Its been a pain to find the driver.

ok heres the output--
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by Mark_in_Hollywood on 2008-10-28
Start here:

Enabling direct rendering in my [SiS] 661/741/760 PCI/AGP card
[http://ubuntuforums.org/archive/index.php/t-488185.html](http://ubuntuforums.org/archive/index.php/t-488185.html)

If I'm understanding you, you have a video card from SiS and have a hard time installing the driver.

What commands are you issuing?

The link below seems to have info about your card, too:

[http://hardware4linux.info/component/25909/](http://hardware4linux.info/component/25909/)

---

### Post by dennis1200 on 2008-10-28
I used to have a computer with the same video chipset. At the moment, which is the same ever since the cards came out quite a while ago, you can't enable DRI (3D support), but generic video should be no problem. 
As to installing a video driver, it should be already installed in ubuntu. The package is xserver-xorg-video-sis. To make sure it's installed, type: ```
sudo aptitude install xserver-xorg-video-sis
```.

For info on your card in X and DRI support, check out the following (which makes it sound pretty hopeless, though):
[http://www.winischhofer.net/sisdri.shtml](http://www.winischhofer.net/sisdri.shtml)

And this subsection specifically talks about the SiS 760 chipset.
[http://www.winischhofer.eu/linuxsispart1.shtml#13]("http://www.winischhofer.eu/linuxsispart1.shtml#13")



> [COLOR="Red"]Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number.[/COLOR]

---

### Post by Asherr6 on 2008-10-28
this is the name of the driver i downloaded-- sis_drv.o_4.3.0_gcc3_290906-1.tar.gz
i just drag and drop it into terminal, it says permission denied.  then i tried code:
 sudo install apt-get sis_drv.o_4.3.0_gcc3_290906-1.tar.gz   no file or directory

---

### Post by cariboo on 2008-10-28
Double click on the file and let fileroller extract it for you. Extract it somewhere in your home directory. install build-essential, and you should be able to compile the driver.

You might want to have a look here:

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

before starting.

Jim

---

### Post by Mark_in_Hollywood on 2008-10-29
A little more sleuthing shows

[http://www.sis.com](http://www.sis.com)

surf there. Select DOWNLOAD.

Click "agree"

Go to

STEP BY STEP

Pull down to Linux
Select your product -- I tried:

IGP Graphics Drivers

select

Sis 650 & 740 series.

Download the driver:

SiS650 Graphic Driver(Redhat 7.2) 

Save any other pertinent info from Sis.com ([http://www.sis.com/support/support_faqs_4.htm](http://www.sis.com/support/support_faqs_4.htm))

Using either Synaptic Pkg. Mgr. or sudo aptitude install alien,
install alien; that will convert the Redhat package (your graphic driver) into debian-ubuntu.

You will have to run **alien** against the Redhat driver to change it into the Ubuntu-speak.


Here is the Debian page with command structure for the conversion:

Install .rpm Files in Debian and Ubuntu
[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

After the conversion to ubuntu-speak, you have to untar the .tar.gz. Maybe right clicking on the file will offer "open with archive manager", in which case, select that option. 

After the Archive Manager opens, you can untar the file in /tmp

Now as I can't know what kind of file will be opened, you need to look at the permissions and I can't give you help with that. Maybe the driver should be owned by '/' spoked as: root. Or maybe the user has the permissions.

This is as far as I can take you, the untar commands are found at:

[http://www.pendrivelinux.com/2007/10/12/how-to-open-a-tar-file-in-unix-or-linux/](http://www.pendrivelinux.com/2007/10/12/how-to-open-a-tar-file-in-unix-or-linux/)



sudo dpkg -i sis_drv.o_4.3.0_gcc3_290906-1

---

### Post by Kangarooo on 2009-07-10
Ok from i downloaded  SiS650 Graphic Driver(Redhat 7.2)
Filename of that driver is sis_drv.o-410
Then i sudo apt-get install alien
then i tryd
sudo alien -d sis_drv.o-410
sudo alien -i sis_drv.o-410
sudo alien -k sis_drv.o-410
sudo alien sis_drv.o-410
each time i got response
Unknown type of package, sis_drv.o-410.
with dot in the end. Stange.
So how can i get alien working? Maybe some other way to use alien? And/Or to get this driver working?

In alien help in examples are *.rpm files [http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)
There is wwritten that from *.rpm ill get *.deb file and it will be installing not with double click on it to open but with command sudo dpkg -i *.deb

So im very confused.. What to do? I got either on wrong type of file or on alien bug? Maybe without alien i can extract deb from the file i downloded with is ment for RedHat..? HELP

---

### Post by Mark_in_Hollywood on 2009-07-11
> **Kangarooo said:**
> Ok from i downloaded  SiS650 Graphic Driver(Redhat 7.2)
Filename of that driver is sis_drv.o-410
Then i sudo apt-get install alien
then i tryd
sudo alien -d sis_drv.o-410
sudo alien -i sis_drv.o-410
sudo alien -k sis_drv.o-410
sudo alien sis_drv.o-410
each time i got response
Unknown type of package, sis_drv.o-410.
with dot in the end. Stange.
So how can i get alien working? Maybe some other way to use alien? And/Or to get this driver working?

In alien help in examples are *.rpm files [http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)
There is wwritten that from *.rpm ill get *.deb file and it will be installing not with double click on it to open but with command sudo dpkg -i *.deb

So im very confused.. What to do? I got either on wrong type of file or on alien bug? Maybe without alien i can extract deb from the file i downloded with is ment for RedHat..? HELP


Sorry for the delay in getting back to you. I believe you need to give the 

alien argumment-1 argument-2

see:

Installing using an RPM file
[http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/]("http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/")

That's about all the help I can give. I'm outta here.

---

### Post by Kangarooo on 2009-07-12
Try yourself.. not working.. i tryd already all variations.. -k -i and without them also.
That alien converts from .rpm to .deb
and file witch i downloaded from sis download page redhat 7,2 version and also try 7.0 version are not .rpm files..
you suggested to to convert with alien a file witch is not .rpm file.. So what to do then? Go check that [http://www.sis.com/download/](http://www.sis.com/download/) there is not .rpm package..

---

### Post by Kangarooo on 2009-11-15
In [http://www.sis.com/download/index.php](http://www.sis.com/download/index.php) theres link For Linux users, please check out this page [http://www.sis.com/support/support_faqs_16.htm](http://www.sis.com/support/support_faqs_16.htm) and from there info Other available linux drivers Graphics Driver Details goes to [http://www.sis.com/support/linux_old.htm#650](http://www.sis.com/support/linux_old.htm#650)

Hope to see this driver working is still living :)

---

