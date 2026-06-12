---
title: "[SOLVED] Cannot run Ubuntu Feisty 64 with Ati x700, blackscreen results 64bit thread"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ramza001 on 2007-09-20
I posted this in the absolute beginner talk section.

[http://ubuntuforums.org/showthread.php?t=555752](http://ubuntuforums.org/showthread.php?t=555752)

"""Please forgive my ignorance, this is my first attempt to use any kind of Linux OS.

My system is a Emachine T6212 Amd 64bit 3200 and i am using a Ati x700 pcie video card.

"the x700 works in windows on my system"

First off I could not use the live 64bit Feisty cd to install Linux because i kept getting a blackscreen and my monitor went off, so I used the alternate version installation cd instead and I successfully installed Linux.

Then when i tried to enter the installed system, I still got a blackscreen and the monitor went off.

So i figured it had something to do with my video, so i took out my video card and the system worked using my integrated x200 video.

I looked up on google if I could disable my integrated video but from what i have read the bios I am using will not allow it.

I tried a number of things the last few days with the help of google and I have found no solution so that I can still use my x700 video card with linux.

If I cannot get this fixed I will have to wait on using this wonderful OS which i have been wanting to use for a long time."""




I was wondering if part of the problem is that im using the 64bit version of feisty.

Hope you can help because this is a big headache.

---

### Post by John.Michael.Kane on 2007-09-20
From the info I found on your machine, and the fact that you say the Ubuntu install when off with out any issue until you rebooted. I'm inclined to say that the gpu is not faulty, 

What seems to be happening is that when you plug in the pci-e card you have the bios disable the on board gpu automatically.


Heres what you can try doing. 

Restart your machine with the Ubuntu cd in the drive, and at the boot/install menu ( Press F6 first). , and add the command below, and proceed to install Ubuntu.
```
nosplash noapic nolapic
```
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

### Post by Ramza001 on 2007-09-20
> **SD-Plissken said:**
> From the info I found on your machine, and the fact that you say the Ubuntu install when off with out any issue until you rebooted. I'm inclined to say that the gpu is not faulty, 

What seems to be happening is that when you plug in the pci-e card you have the bios disable the on board gpu automatically.


Heres what you can try doing. 

Restart your machine with the Ubuntu cd in the drive, and at the boot/install menu ( Press F6 first). , and add the command below, and proceed to install Ubuntu.
```
nosplash noapic nolapic
```
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

I pressed f6 on the text installation on the alternate install cd and typed this in, I reinstalled and im still getting the black screen.

Did i do something wrong or something else i can do?

---

### Post by John.Michael.Kane on 2007-09-20
> **Ramza001 said:**
> I pressed f6 on the text installation on the alternate install cd and typed this in, I reinstalled and im still getting the black screen.

Did i do something wrong or something else i can do?

Not sure if you did something wrong or not. All you needed to do was add that line of code to the code already in the  boot line, and press enter, however.If you typed over the info in the boot line then yes you did it wrong.

As for other options

1) Install Ubuntu using the on board gpu, Then install the ati drivers, and  retry the new card after properly installing Ubuntu, and the ati driver.

2) See if theres a bios update for your board.

---

### Post by mobad on 2007-09-20
Heh you have the same video card I have... and the same problem I had.

Should be an easy fix. 

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "sudo nano /etc/X11/xorg.conf" (without quotes) You will need to type your password.
Step 4: Look through the file and find a line like " Driver "ati" "
Step 5: Change the "ati" to "radeon"
Step 6: Hit Ctrl + X then "Y" then enter.
Step 7: Type "sudo /etc/init.d/gdm restart" (without quotes) You may need to type your password. 

That should do it!  If not post back.

---

### Post by Ramza001 on 2007-09-20
> **mobad said:**
> Heh you have the same video card I have... and the same problem I had.

Should be an easy fix. 

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "sudo nano /etc/X11/xorg.conf" (without quotes) You will need to type your password.
Step 4: Look through the file and find a line like " Driver "ati" "
Step 5: Change the "ati" to "radeon"
Step 6: Hit Ctrl + X then "Y" then enter.
Step 7: Type "sudo /etc/init.d/gdm restart" (without quotes) You may need to type your password. 

That should do it!  If not post back.

Thank the lord! It finally worked.

Lets hope i do not run into any more troubles.

Thank you SD-Plissken,mobad, Hopefully this thread will help other who have similar problems.

---

### Post by mobad on 2007-09-20
Heh, no problem.

I would recommend installing the ATI restricted driver.  (Its really easy there should be a pop up for it when you log in, if not go to System > Administration > Restricted Drivers Manager and check the ATI one.)  You may have some problems after installing it though... if you do just post again and I'll help.

---

### Post by Ramza001 on 2007-09-20
> **mobad said:**
> Heh, no problem.

I would recommend installing the ATI restricted driver.  (Its really easy there should be a pop up for it when you log in, if not go to System > Administration > Restricted Drivers Manager and check the ATI one.)  You may have some problems after installing it though... if you do just post again and I'll help.

Actually yes I do have a problem with this, I activated the driver then rebooted and got blackscreen so I followed your directions again and im back on Ubuntu.

There is also a error at the start of my system about "hal".

---

### Post by mobad on 2007-09-20
OK it's a pretty easy fix. (BTW the hal error should not be a problem)

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "sudo nano /etc/X11/xorg.conf" (without quotes) You will need to type your password.
Step 4: Look through the file and you should notice doubles of the "Screen", "Driver" and "Monitor".
Step 5: You are going to want to remove the places that look like the red ones below:

NOTE: the red ones may not look exactly like that but you can get the general idea of what to remove.

[COLOR="Red"]
Section "Monitor"
	Identifier   "monitor"
	HorizSync    30.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection
[/COLOR]
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection
[COLOR="Red"]
Section "Device"
	Identifier  "ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Driver      "fglrx"
	VideoRam    512000
	BusID       "PCI:1:0:0"
EndSection
[/COLOR]
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
[COLOR="Red"]
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Monitor    "DPro930SB"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
[/COLOR]
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Step 6: Hit Ctrl + X then "Y" then enter.
Step 7: Run "sudo depmod -a"
Step 8: Type "sudo /etc/init.d/gdm restart" (without quotes) You may need to type your password. 

That should do it! If not post back.

---

### Post by Ramza001 on 2007-09-21
> **mobad said:**
> OK it's a pretty easy fix. (BTW the hal error should not be a problem)

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "sudo nano /etc/X11/xorg.conf" (without quotes) You will need to type your password.
Step 4: Look through the file and you should notice doubles of the "Screen", "Driver" and "Monitor".
Step 5: You are going to want to remove the places that look like the red ones below:

NOTE: the red ones may not look exactly like that but you can get the general idea of what to remove.

[COLOR="Red"]
Section "Monitor"
	Identifier   "monitor"
	HorizSync    30.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection
[/COLOR]
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection
[COLOR="Red"]
Section "Device"
	Identifier  "ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Driver      "fglrx"
	VideoRam    512000
	BusID       "PCI:1:0:0"
EndSection
[/COLOR]
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
[COLOR="Red"]
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Monitor    "DPro930SB"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
[/COLOR]
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Step 6: Hit Ctrl + X then "Y" then enter.
Step 7: Run "sudo depmod -a"
Step 8: Type "sudo /etc/init.d/gdm restart" (without quotes) You may need to type your password. 

That should do it! If not post back.



Ok all hell broke lose after doing this, i got a xorg error i think and would not let me get back into ubuntu so i rebooted and got blackscreen again.

---

### Post by mobad on 2007-09-21
Heh then you must of done something wrong...

In any case I'll post a xorg.conf that will replace your old one.

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "wget http://anapnea.net/~mobad/xorg.conf"
Step 4: Type "sudo cp xorg.conf /etc/X11/xorg.conf"
Step 5: Type "sudo depmod -a"
Step 6: Type "sudo /etc/init.d/gdm restart"

Now THAT should do it... If not, just post again!

---

### Post by Ramza001 on 2007-09-21
> **mobad said:**
> Heh then you must of done something wrong...

In any case I'll post a xorg.conf that will replace your old one.

Step 1: Ctrl + Alt + F2 and you should get something that asks for you user name.
Step 2: Type in your username and password.
Step 3: Type "wget http://anapnea.net/~mobad/xorg.conf"
Step 4: Type "sudo cp xorg.conf /etc/X11/xorg.conf"
Step 5: Type "sudo depmod -a"
Step 6: Type "sudo /etc/init.d/gdm restart"

Now THAT should do it... If not, just post again!


Ok that fixed it thankfully, still getting that hal error though. haha

---

### Post by mobad on 2007-09-21
What does is exactly do?  Is it just an error with no other side effects?  Or is it stopping your computer from booting, logging in or so on?

---

### Post by Ramza001 on 2007-09-22
> **mobad said:**
> What does is exactly do?  Is it just an error with no other side effects?  Or is it stopping your computer from booting, logging in or so on?

Well i dont know if there are any side effects or not, do you know what it means?

---

### Post by mobad on 2007-09-22
I don't really know what it means but if you don't notice anything wrong then it shouldn't be a problem.

---

### Post by Ramza001 on 2007-09-22
> **mobad said:**
> I don't really know what it means but if you don't notice anything wrong then it shouldn't be a problem.

Well I guess im good to go for the moment then.

Thanks mobad, Im grateful for the help

---

### Post by Ramza001 on 2007-09-26
It looks like the system will only startup when i type the lines you gave me for that custom xorg file, every time i reboot i have to do it again or i get the blackscreen.

---

### Post by Vich on 2007-10-04
blackscreen at startup?
I had that problem and am still having all manner of problems getting my radeon x800 to work with ubuntu 64bit.

Anyhow, you can add mobad's lines direct into your grub boot config (/etc/boot/grub/menu.lst)
find the line you boot with and add the options on the end.

I got mine to work by appending vga =791 (hopefully in blue if I got the tag right)
e.g

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e1e0c336-1249-4536-5241-c3e80fs9gc13 ro quiet splash [color=blue]vga=791[/color]
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

---

