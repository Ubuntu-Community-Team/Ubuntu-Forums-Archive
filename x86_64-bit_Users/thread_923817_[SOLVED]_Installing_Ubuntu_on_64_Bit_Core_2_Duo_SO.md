---
title: "[SOLVED] Installing Ubuntu on 64 Bit Core 2 Duo SONY FW series"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by pravlm on 2008-09-18
I have installed the KUbuntu 8.04 successfully. 

But when I boot that I get a blank screen. I have no clue what the problem is.

Am I missing any drivers ? Please help

The configuration of my SONY laptop

Software

Operating System : Genuine Microsoft® Windows Vista® 64bit Home Premium with SP1

Display
Resolution : 1600 x 900
Screen Size : 16.4"6
XBRITE-ECO™ Technology : Yes

Hard Drive
Capacity : 320GB2
Interface : Serial ATA
Speed : 5400rpm

Memory
Installed : 4GB15 PC2-6400 (2GBx2)
Maximum : 4GB15
Speed : 800MHz
Type : DDR2 SDRAM

Networking/Modem
Bluetooth® Technology : Integrated Stereo A2DP Bluetooth® Technology16
Ethernet Protocol : 10Base-T/100Base-TX/1000Base-T
Ethernet Speed : Fast Ethernet (RJ-45)
Modem Type : Integrated V.92/V.90 Modem (RJ-11)
Wireless LAN : Intel® WiFi Link 5100AGN (802.11a/b/g/n)3

Optical Drive #1
Blue ray Read, DVD and CD


-Regards
Mak

---

### Post by pravlm on 2008-09-18
Does anyone has SONY FW series and tried installing Ubuntu Or I am just alone :(

---

### Post by volekvolek on 2008-09-19
:(

Sorry to say, I have the same problem with my new Sony Vaio Fw140, ubuntu 8 64bit. 

I tried using different boot option such as vga=792 with no luck.  
Still investigating... as more people buy this laptop , I am sure we will see more usseful postings than mine .

---

### Post by pravlm on 2008-09-19
Thank god I am not alone :) , Oct 30 there will be new release of Intrepid hopefully it will have fixes for the new laptops like Sony FW. We have to just wait.

---

### Post by cprofitt on 2008-09-20
To clarify... blank screen before or after your get to the initial splash screen on the liveCD?

Have you tried the alternate install?

Does your SONY use the Intel Graphics Media Accelerator 4500MHD?

---

### Post by pravlm on 2008-09-20
Yes exactly, I tried alternate install its the same results.

Some one in the IRC chat mentioned to use CTRL-ALT-F1 key , and I did to get a login prompt.

I was able to login, but how do I proceed I dont know.

Yes exactly SONY has Intel Graphics Media Accelerator however the display adapter is called as Mobile Inter (4) series chipset family.

I am sure Sony does not have any drivers for Linux as such.

---

### Post by pravlm on 2008-09-20
Sorry I didnt answer one question,

Blank screen is after I get the Kubuntu/Ubuntu Splash screen.

---

### Post by IntuitiveNipple on 2008-09-20
It might be helpful if you can post the results of these commands. You can redirect them into a file and copy that file to another PC, or a memory-stick, in order to open it and copy its contents here:
```

lspci -nn > /tmp/Vaio-FW.txt

lsusb >> /tmp/Vaio-FW.txt

```

---

### Post by cprofitt on 2008-09-21
Yes the output of lspci would be good. I am glad I found this though as I was considering buying a VGN-FW170J/W.

From what I am looking at there is no open source graphics driver for this chipset yet.-- though this might be it...

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2991&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2991&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

---

### Post by cprofitt on 2008-09-21
I found some more information:

[http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=1cfe769c74d1a3a392bf1aaaf5c2dcc8273daf66](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=1cfe769c74d1a3a392bf1aaaf5c2dcc8273daf66)

This indicates that the driver is committed to the xorg/driver/xf68-video-intel on June 17th.

Anyone know when this will make it in to Ubuntu?

From what I can tell support is in the 2.4.2 package for xf86-video-intel

---

### Post by pravlm on 2008-09-21
Hi IntuitiveNipple and PrivateVoid,

I am unable to copy the output to my USB drive, I cant mount the usb drive.

$sudo fdisk -l 

Shows the disk but the USB is not mounted, I checked the /media

While mounting I get an error saying me to run modprobe fuse.

But running that causes a FATAL error, could not load the modules.dep. Iwent through many threads in the forum not much help.

Is there a easy way to get the lsusb and lspci output to some media ??

---

### Post by pravlm on 2008-09-21
Hi IntuitiveNipple and PrivateVoid,

I am unable to copy the output to my USB drive, I cant mount the usb drive.

$sudo fdisk -l 

Shows the disk but the USB is not mounted, I checked the /media

While mounting I get an error saying me to run modprobe fuse.

But running that causes a FATAL error, could not load the modules.dep. Iwent through many threads in the forum not much help.

Is there a easy way to get the lsusb and lspci output to some media ??

---

### Post by pravlm on 2008-09-22
> **IntuitiveNipple said:**
> It might be helpful if you can post the results of these commands. You can redirect them into a file and copy that file to another PC, or a memory-stick, in order to open it and copy its contents here:
```

lspci -nn > /tmp/Vaio-FW.txt

lsusb >> /tmp/Vaio-FW.txt

```


----------

Atlast I was able to get the output of these here is the output

```

$lspci

00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)

00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)

00:02.1 Display controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

05:00.0 Network controller: Intel Corporation Device 4232

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)

09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)


$lsusb

Bus 008 Device 005: ID 054c:0377 Sony Corp. 

Bus 008 Device 003: ID 0781:a7c1 SanDisk Corp. 

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 002: ID 05ca:183d Ricoh Co., Ltd 

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 003: ID 044e:3017 Alps Electric Co., Ltd 

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by pravlm on 2008-09-23
Hi Folks,

I just read this in another website. Hope its helpful for someone who is struggling like me to install in Sony FW.

Let me tell you I installed Kubuntu so this didnt work for me, I hope for others who installed Ubuntu + Gnome it might work try it and let me know.

> 

If you got a white screen (or just brown background color) and no gui after you login into Ubuntu, you propably have Compiz enabled while using video driver no capable to process Compiz.

Here is workaround. You need to go into console using Ctrl+Alt+F1, then login and type DISPLAY=:0 metacity --replace (double dash here, who knows how to fix it in wordpress?). Then go back into gnome using Ctrl+Alt+F7 and you should get your gui back. Then you can install other drivers or disable Compiz in System->Preferences->Appearance on Visual Effects tab.

WARN: If you have external monitor connected and you see gui there, this is propably not your soultion. I&#8217;m going to check external monitor connection on my laptop soon.



---

### Post by JagerQ on 2008-09-23
I had a similar problem on my new laptop which went away when I boot with mem=4096m but now I can't seem to see all my RAM, only 2.5 Gb despite the 64 bit OS.

---

### Post by cprofitt on 2008-09-23
I am strongly leaning towards the problem being the new video chipset from Intel not being supported in the current (8.04) version of Ubuntu.

---

### Post by pravlm on 2008-09-26
Yes as "PrivateVoid" is doubting the problem is that either 8.04 nor the "Interpid" versions are not supporting the new Intel Mobile (4) chipset.

Can any one respond to us to let us know when will the new intel chipset be supported??

God Bless!

---

### Post by shadyzay on 2008-10-02
I have the VGN-FW170J. Trying to install Kubuntu 8.04 amd64. I installed the intrepid driver ( 2.4.1 ) and the problem is not solved.
Now when I run the system, I get a very corrupted display. The display is tiled with a little section of the kubuntu login screen. First it's the wait cursor ( the white spinner ) repeated all over, and by moving the mouse, I can see different parts of the screen ( like some letters of the "username" label )

This is where I downloaded the backported drivers from:
[http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/](http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/)
(the links are in the blog post )

---

### Post by pravlm on 2008-10-02
Hi Shady,

Yes I have the same problem , I believe there are bugs yet to be fixed for Intel GMA4500HD. 

We just have to wait.

---

### Post by alexinchains on 2008-10-09
I have the sony vaio FW with the ATI card and installing linux works. But it has a hard time with the resolution, it only gives me 1280 x 800.

your problem is probably the intel graphics.

---

### Post by pravlm on 2008-10-09
Hi Alex,

Yes you are correct, the problem is with INTEL graphics. Do you know how to compile the intel graphics driver? , by the way which linux flavor you installed?

---

### Post by pgar23 on 2008-10-13
Hey guys..I have been following your thread..and I am also having the same problem. I was referred to a site where I got this driver..it is for linux, I have not tried install it yet but if anyone knows how, try it and reply back to us..

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2991&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2991&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

---

### Post by pravlm on 2008-10-14
Hi Pgar32

Do you think that Oct 30 release of Intrepid will have the fix for this problem?

Any idea?

---

### Post by pgar23 on 2008-10-14
> **pravlm said:**
> Hi Pgar32

Do you think that Oct 30 release of Intrepid will have the fix for this problem?

Any idea?

I don't know to be honest, but I doubt it. because the chipset is new and I bet not enough people have reported the bug yet..So it is best to find a workaround ourselves first and then hope that a new release will come with the fix. :)

---

### Post by goharanwar3 on 2008-10-16
Hi Guys, I am facing the same problem on my FW170J. I tried installing Ubuntu 8.04 on my friends note book i.e FW190E. It worked perfectly. But still havent got the solution for FW170J.
We should report this bug to the developers of the UBUNTU so that they may fix the problem in the upcoming release of UBUNTU.

Gohar

---

### Post by ponar on 2008-10-20
I have a Sony VGN-FW140E with the exact same issue. I've install the latest 8.10 Beta, compiled the latest intel drivers (2.4.2), updated the kernel, all to no avail.

It works great when I connect an external monitor to the VGA output of the laptop, but the built-in display refuses to work with anything other than vesa mode.

Anyone come up with anything yet?

---

### Post by igknighted on 2008-10-26
Just a confirmation of everyone else... I've got an FW140E and no matter what distro I boot (Ubuntu 8.10 RC, Suse 11.1 Beta3, Fedora 10 beta, etc.) I get a white screen when X loads.  I can go to the terminal and change to vesa and get the desktop, but nothing fixes the display with the intel driver.  Still no luck anyone?

---

### Post by suncoolsu on 2008-10-27
I have the same problem on my Dell Studio 1535 laptop. Following is the configuration:

Processor - Intel Core 2 Duo T8100
Video Card - Intergrated Intel(R) Graphics Media Accelerator X3100
BIOS Version - A04.

I got the White Screen of Death as well but changing drivers to "vesa" in the xorg.conf atleast fixed the problem. But the ubuntu graphics are pretty primitive - My laptop was able to handle vista so i think I should be able to enjoy ubuntu with full visual pleasure. 

I am pretty sure that ubuntu is not even able to recognize my Video Card :(. I have searched and searched - but none of the method worked .. 

if anyone has solved this problem - please help !

---

### Post by shadyzay on 2008-10-31
any progress on this .. anyone?

---

### Post by villordo on 2008-11-04
Hi igknighted. I have same problems than you on my fw170j =/
if had any progress please tell me

---

### Post by pravlm on 2008-11-07
Has anyone tried installing the oct 30 release of ubuntu in sony Vaio ??

How do we come out of this problem, initially I thought I was the only one now we have some many people reporting this problem.

How do I write the bug report?

---

### Post by volekvolek on 2008-11-08
I just installed the latest release Oct 30.  And the same problem. I do see a message at boot time about Intel Video via KDM ,  I am trying to track it down and post it here.  Sony Viao wide screen is one of the mostly sold laptops, Its amazing this problem has not been resolved after 4 months.

---

### Post by suncoolsu on 2008-11-09
The same is case for Dell laptops :) Its amazing that it hasnt been fixed yet. Alas, i am not smart enough to figure it out. This post might help if u have the knowledge and experience in linux

[http://ubuntuforums.org/showthread.php?t=890843&highlight=Mesa+drm](http://ubuntuforums.org/showthread.php?t=890843&highlight=Mesa+drm)

---

### Post by shadyzay on 2008-11-17
apparently the cause of the white screen issue has been found, [this comment]("http://bugs.freedesktop.org/show_bug.cgi?id=17292#c122") was just posted to the bug report on freedesktop.org. I didn’t have the chance to test the patch myself, but apparently the bug is resolved.

---

### Post by shadyzay on 2008-11-19
I just want to confirm that this fix worked for me on my Sony Vaio VGN-FW170J with kubuntu-8.10-amd64 installed
I used the source package for xserver-xorg-video-intel from ubuntu repositories ( 2:2.4.1-1ubuntu10 ) and applied the patch. The display is on now.

The login screen has two vertical strips with "noise" at the sides, but the display is ok once kde starts.

As for the backlight, the control buttons doesn't work, it's always set to it's maximum value.

The following lines are written to Xorg.0.log almost every 10 seconds:
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.

Although direct rendering is on, glxgears outputs: 3610 frames in 5.0 seconds = 721.848 FPS, which is way lower than what I expects from this card.

X crashed when I tried to change the resolution from systemsettings.

---

### Post by pravlm on 2008-12-31
Hi Everybody,

I was able to get the Kubuntu graphics up and running and what can I say its out of the world excellent graphics. 

Just followed these steps,

1. Downloaded the Kubuntu DVD interpid Ibex 8.10 you can get it from

   [KUbuntu DVDImage]("http://cdimage.ubuntu.com/kubuntu/releases/8.10/release/") 

2. Follow this link to download the latest driver - thanks to someone who made it a debian package. You can follow this link to solve it as well.

 [ How to get the graphics working in Sony FW ]("http://www.uluga.ubuntuforums.org/showthread.php?t=1023801") 
 Download the 32 bit or 64 bit which ever is applicable to you.
 Download it to an USB drive.

3. After installing the Live DVD Kubuntu.
   Login to Command line Kubuntu by pressing "alt-f1"

4. Now remove the current version of the driver.
   ```

   sudo apt-get remove --purge xserver-xorg-video-intel
   
```

5. Plug in the USB drive which has the debian packge of the driver.
   Mount the USB drive by doing this
```

   sudo mkdir /media/usb
   sudo mount -t ntfs-3g /dev/sdb1 /media/usb -o   uid=1000,gid=1000,utf8,dmask=027,fmask=137 -o force
 
```

6. Now install the package by 
   ```

     cd /media/usb
     sudo dpkg -i <Name of the package>.deb
   
```

7. Thats all now reboot the Kubuntu 
   and enjoy!!!!!!!!!!!!

---

