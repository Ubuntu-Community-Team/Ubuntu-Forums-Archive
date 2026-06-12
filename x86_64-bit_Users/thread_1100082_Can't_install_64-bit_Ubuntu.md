---
title: "Can't install 64-bit Ubuntu"
date: 2009-03-18
forum: x86 64-bit Users
---

### Post by Ian222 on 2009-03-18
I have an AMD 64 Cisnet CA-8003B. I did a clean install of Vista on the entire hard drive with no partitions, got all of the updates, defragmented the hard drive, and tried to install the 64-bit 8.10.

I checked that the CD had the right MD5 sum and checked that there were no errors on the CD with at the live cd menu. I also checked that the hard drive had no errors (it's new). 

When I try to install or run the Live CD, the Ubuntu progress bar gets near the end and I get a message that says "[.004000] Aperture beyond 4 GB. Ignoring. 
Loading, please wait..." then get a warranty message and "ubuntu@ubuntu:"$"

The attached photo gives the entire message.

I bought this computer with the intent of using Ubuntu primarily, I'm not that keen on going back to Windows. Any help would be greatly appreciated.

Thanks,

Ian

---

### Post by pytheas22 on 2009-03-18
It looks like the system is booting correctly, but X (the graphical display) is not starting for some reason.  What kind of video card do you have in the machine (if you know the exact model, that would be helpful)?

Also, what happens if you type the command:
```

startx
```

at the command prompt that you see?  This should either start X, or give you some feedback about why it doesn't want to start.

I don't think the line about 'Aperture beyond 4 GB. Ignoring' is relevant to the situation; you're only seeing it because you're in text-only mode.

---

### Post by Yellow Pasque on 2009-03-18
> Aperture beyond 4 GB. Ignoring
As pytheas22 said, don't worry about this one at the moment. It won't stop you from installing.
I'd recommend pressing F4 at the LiveCD menu and using "Safe Graphics Mode" before booting into the LiveCD environment and/or running the installer. If that doesn't work, please state your video card model.

---

### Post by nikgare on 2009-03-19
Did you install using the server CD or the desktop CD?
The Server CD doesn't install X, maybe this is the problem?

---

### Post by wfp on 2009-03-19
Yes it looks like you might have downloaded the server edition from looking at your screen shot it says the kernel that is loading is  2.6.27.7 if you downloaded the desktop edition in the last month are so it should read 2.6.27.11

---

### Post by Ian222 on 2009-03-19
I'm using the Desktop CD.

I can run the LiveCD using safe mode.

I tried to run the LiveCD and typed "startx" at the prompt. The error is shown in the attached photo, but seems to be that the computer didn't detect a monitor. I called the manufacturer; the video card is an ATI Radeon X300 based 2d by 3d. 

It seems reasonable that this is the problem. What can I do to fix it? Thanks,

Ian

---

### Post by Slim Odds on 2009-03-19
> **Ian222 said:**
> 
It seems reasonable that this is the problem. What can I do to fix it?

You might want to look at the Xorg.0.log file (refer to the screen shot for locations)

---

### Post by Ian222 on 2009-03-19
How am I supposed to look at that? I can't get Ubuntu installed.

---

### Post by Yellow Pasque on 2009-03-19
Someone suggested the monitor disconnecting from the video card right before you boot Ubuntu, so that X.org won't get confused by a monitor that gives bad info.

Another thing to try would be "Safe graphics mode" under the F4 menu.

---

### Post by pytheas22 on 2009-03-19
You can try Temüjin's recommendations above for getting Ubuntu installed using 'Safe Graphics Mode'.  If that won't work, you could burn the [Ubuntu alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), which uses a text-based installer that should work for you, and use it to install Ubuntu.  Once Ubuntu is installed, we can deal with fixing the graphics issue permanently (if it's not fixed on its own).

---

### Post by Slim Odds on 2009-03-19
> **Ian222 said:**
> How am I supposed to look at that? I can't get Ubuntu installed.

Your picture shows a command prompt.

```
less /var/log/Xorg.0.log
```

---

### Post by Ian222 on 2009-03-19
I tried running the Live CD in safe mode and got the /var/log/Xorg.0.log file, which is attached. It doesn't mean anything to me. I saved it as a .txt and had to split it so I could attach it. Does anyone see anything in it that suggests what the problem is? Should I try installing Ubuntu in safe mode next? Thanks,

Ian

---

### Post by pytheas22 on 2009-03-19
The log that you posted was created when your system was in failsafe graphics mode, so it's unfortunately not representative of what happens when you try to run Ubuntu normally.  There's not an easy way to get a non-failsafe log while running just the live CD.

I would go ahead and install Ubuntu in safe graphics mode.  From there, it will be easier to figure out how to solve the problem permanently.

Once you get Ubuntu installed, it would be useful if you posted your xorg.conf file, which you can view by typing:
```

gedit /etc/X11/xorg.conf
```

---

### Post by can8dnSix on 2009-03-20
Ian222 have you tried just turning off the splash when you do the install? 
I had an issue similar to yours sometime back and I turned off the splash and it works. Was odd; but anyway just my $0.02

 ```
kernel /boot/vmlinuz-2.6.22-14-generic root=UU--BLAH BLAH--2203 ro quiet spash
```

L

---

### Post by Ian222 on 2009-03-22
I installed using the graphical safe mode. It works fine, except the resolution is set to 640 x 480 and can't be changed as the computer isn't detecting the type of monitor I'm using. I have another computer that will be replaced connected to the same monitor and it detects it. I assume this means there is a problem with the video card. Is there a way to get it to work, or should I look to get another? Thanks for your help,

Ian

---

### Post by pytheas22 on 2009-03-22
If you go to System>Administration>Hardware Drivers, do you see an option for enabling a driver for your video card?  If so, checking the box to enable that driver may solve the problem, because it would download the closed-source video driver, which may work better.

If there's no option in Hardware Drivers, please open a terminal (Applications>Accessories>Terminal), run these commands and post the output:
```

lspci -nn
cat /etc/X11/xorg.conf
```

Although I can't say with certainty until I know exactly which type of video card you have (the output of the 'lspci -nn' command will tell me), I doubt that you need to get a new video card to get higher resolution.  It's probably just a matter of straightening out some issues with the driver.

---

### Post by Ian222 on 2009-03-24
I activated the proprietary driver; it let me change the resolution, but the monitor is still not identified and I can't change the refresh rate or the rotation, not a big deal now, but I may want to in the future. I ran the commands suggested and got the following:

ian@ian-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
00:19.0 PCI bridge [0604]: ALi Corporation M5249 HTT to PCI Bridge [10b9:5249]
00:1b.0 Ethernet controller [0200]: ALi Corporation ULi 1689,1573 integrated ethernet. [10b9:5263] (rev 50)
00:1c.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:1c.1 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:1c.2 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:1c.3 USB Controller [0c03]: ALi Corporation USB 2.0 Controller [10b9:5239] (rev 01)
00:1d.0 Audio device [0403]: ALi Corporation High Definition Audio/AC'97 Host Controller [10b9:5461]
00:1e.0 ISA bridge [0601]: ALi Corporation PCI to LPC Controller [10b9:1573] (rev 31)
00:1e.1 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:1f.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c7)
00:1f.1 RAID bus controller [0104]: ALi Corporation ULi 5287 SATA [10b9:5287] (rev 02)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200] [1002:5974]
02:11.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]
ian@ian-desktop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Any suggestions on what should be done to get the driver to work perfectly? Thanks,

Ian

---

### Post by pytheas22 on 2009-03-24
It's strange that it's not giving you more refresh-rate options (assuming your monitor definitely supports them), but unfortunately I don't know how to fix that--the flgrx driver is closed-source and as such there's not much that can be done if it doesn't support something (not that the open-source driver worked any better).

It might be possible to specify refresh rate and screen rotation in your xorg.conf file, but you'd have to look up the syntax, and you'd have to be careful not to write in a value that's not supported, or it could potentially damage your monitor.  But assuming the current settings are tolerable for you, your best bet would probably be to stick with them rather than risk mucking something else up.

But if rotation and refresh rate are really important to you, let me know and I'll see if there's anything else that might be done.

---

### Post by Ian222 on 2009-03-25
No, it's not very important to me. Thanks to everyone for their help.

---

