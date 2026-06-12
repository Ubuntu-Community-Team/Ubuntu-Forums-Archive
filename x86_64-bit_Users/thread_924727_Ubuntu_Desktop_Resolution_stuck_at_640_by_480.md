---
title: "Ubuntu Desktop Resolution stuck at 640 by 480"
date: 2008-09-19
forum: x86 64-bit Users
---

### Post by kewlpics on 2008-09-19
I just purchased a new PC and installed Ubuntu Server 8.0.4 64 bit.  However, the video resolution stuck at 640 by 480.  I am using HDMI connection.

Could someone please help me find the right driver for my video card?  

**Specifications**
AMD Phenom™ 9100e Processor, 64-bit Quad Core Processor
ATI® Radeon™ HD 3200 Graphics
4GB DDR2 Dual-Channel Memory, 640GB SATA II (7200RPM, 16MB Cache) Hard Drive
802.11g Dual Band Wireless LAN
18x DVD?R/RW SuperMulti Drive featuring Labelflash™ Technology

Thanks for all your help!

---

### Post by IanW on 2008-09-20
Try installing Envy & selecting ATI driver 8.6 (the only one it offers for ATI).
```
sudo aptitude install envy-gtk
```

---

### Post by kewlpics on 2008-09-28
I've tried everything I could.  Looked over many threads.  Even followed all the instructions on this link - [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I get good resolution on the log in screen, but once I log in the screen turns all white, and it changes from 1080i to 480i.

---

### Post by Yellow Pasque on 2008-09-28
I have not had good luck with using the Radeon 3200 and the Hardy-included Catalyst driver. I too have had the "white screen of death". With the latest driver from the ATI site, I get a usable picture, but I cannot get the kernel driver to build no matter what I do, so I end up with the "Mesa" problem (software acceleration).

So, I use the open-source radeonhd driver, which doesn't yet have acceleration code for the Radeon HD cards (should come soon), but at least has proper mode-setting.

---

### Post by peakshysteria on 2008-09-28
In terminal:

```
sudo displayconfig-gtk
```
And adjust the resolution.

Or alt: System --> Preferences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others

---

### Post by seatbelt67 on 2008-09-28
There is an issue with the 4gb of ram. I had the same issue. There is a work around with the 173.. driver upgrade but just do a clean install with either the 64-bit version of 8.04 or get the beta of 8.10. I have 8.10 now and the resolution is back to normal and I can adjust it. Now I have to figure out the sound issue or lack thereof. 
PM me if you have any other questions.

---

### Post by kewlpics on 2008-10-03
> **Temüjin said:**
> I have not had good luck with using the Radeon 3200 and the Hardy-included Catalyst driver. I too have had the "white screen of death". With the latest driver from the ATI site, I get a usable picture, but I cannot get the kernel driver to build no matter what I do, so I end up with the "Mesa" problem (software acceleration).

So, I use the open-source radeonhd driver, which doesn't yet have acceleration code for the Radeon HD cards (should come soon), but at least has proper mode-setting.

I installed the Open-source RadeonHD driver.  Now, I got black screen, no signal is getting through after it is boot up.  

I am trying to get my HDMI working on the Radeon HD 3200 Video Card under Ubuntu 8.0.4.  

I have not tried 8.1.0 because I read it may kill your intel network card.

---

### Post by Yellow Pasque on 2008-10-03
How did you install the radeonhd driver? The package available in Hardy (and Intrepid) is outdated. You have to build from the git source. (I'm actually in the process of writing documentation on how to do that right now).

> I have not tried 8.10 because I read it may kill your intel network card.
Only if it's an e1000e.

---

### Post by kewlpics on 2008-10-03
> **Temüjin said:**
> How did you install the radeonhd driver? The package available in Hardy (and Intrepid) is outdated. You have to build from the git source. (I'm actually in the process of writing documentation on how to do that right now).


I installed the driver using the instruction under this link.

[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

The following is part of my Xorg.0.log, not sure if this is helpful.  Thank you!

(--) RADEONHD(0): Detected an RS780 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xfe8f0000 to 0x7fec61ce4000 (size 0x00010000)
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom:
        SubsystemVendorID: 0x1002 SubsystemID: 0x1002
        IOBaseAddress: 0xc000
        Filename: B_HDMI_T1.bi
        BIOS Bootup Message: ^M
                                                                            ^M

(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 16
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0xfffc000
(II) RADEONHD(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0xfffc000
(II) RADEONHD(0): Default Engine Clock: 500000
(II) RADEONHD(0): Default Memory Clock: 333000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 14320
(WW) RADEONHD(0): DRI support has been disabled at compile time
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 14320
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1fda
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1fda
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x1
(II) RADEONHD(0): I2C bus "RHD I2C line 4" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.

---

### Post by Yellow Pasque on 2008-10-03
Those directions are really out of date. You were probably missing some dependencies. I just did a fresh install of Ubuntu Intrepid on my spare disk and I got the build dependencies with apt-get build-dep. I've adapted the list for Hardy and put it into an easy command:

```
sudo apt-get install x11proto-xf86dri-dev x11proto-core-dev libxau-dev x11proto-fonts-dev x11proto-input-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev xutils-dev m4 autoconf autotools-dev automake patch dpkg-dev html2text gettext intltool-debian po-debconf debhelper diffstat libdigest-sha1-perl libdigest-hmac-perl libfile-remove-perl libio-stringy-perl libltdl3-dev libmime-types-perl libobject-realize-later-perl libuser-identity-perl libmail-box-perl libsys-hostname-long-perl libmail-sendmail-perl zlib1g-dev libpci-dev libpixman-1-dev libtool quilt libpciaccess-dev xserver-xorg-dev libstdc++6-4.2-dev g++ build-essential libdrm-dev
```

Remake the driver.
cd /usr/src/xf86-video-radeonhd/
sudo ./autogen.sh
sudo make
sudo make install

Use cvt to get a modeline and put it in the Monitor section of /etc/X11/xorg.conf
Example
```
cvt 1680 1050 60.0Hz
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

---

### Post by kewlpics on 2008-10-06
Thanks.  I will give this a try.  I think I broke my TV's HDMI port.  Now, I got complete black screen.  Even on restart I don't see the BIOS, logo or anything.  I got a new HDMI cable, no help.

I borrowed a VGA monitor.  I do get signal and resolution for the VGA.  My next step is to get a friend's laptop with HDMI port to see if it is really the HDMI port broken for the TV.

If it is, I guess I need to get a new TV.  If not, it is probably my video card's HDMI function is broken.

---

