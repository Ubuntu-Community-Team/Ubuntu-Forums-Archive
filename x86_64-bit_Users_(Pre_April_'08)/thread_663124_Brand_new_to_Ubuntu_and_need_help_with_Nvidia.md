---
title: "Brand new to Ubuntu and need help with Nvidia"
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by SmasherBasher on 2008-01-09
First of all, hello to everyone and thanks for looking at my post!
I have been using Ubunto 7.10 AMD 64 bit for all of 10 minutes and already have a problem. 
I have an EVGA (NVIDIA) Geforce 7300GT 512 MB graphics card and I have downloaded the driver that the Nvidia website said to download based on my card and that i am running 64 bit. Downloaded it fine and in the instructions, it says to
** sh NVIDIA-Linux-x86_64-169.07-pkg2.run**, given that **NVIDIA-Linux-x86_64-169.07-pkg2.run** is the name of the file I downloaded. 
So I opened up a terminal and did exactly that and got the following error:
[B][COLOR="Red"]sh: Can't open NVIDIA-Linux-x86_64-169.07-pkg2.run
[/COLOR][/B]
What am I doing wrong? Help would be greatly appreciated! And sorry if I put this post in the wrong place, feel free to move it. 
Thanks!

---

### Post by crjackson on 2008-01-09
Have you tired the drive in the restricted driver manager?  If not, I would give that one a try first and see what you think.  It works great for me personally.

Right click on the file and go to the properties menu.  From there find and enable the check box that says "Make Executible"

---

### Post by SmasherBasher on 2008-01-09
Thanks for the quick response!
I had not run it as an executable. As said, I am brand new to ubuntu and was going off of what the Nvidia website said to do. 
I got the program to launch, however it threw me an error stating it must be run as root. 
How do I run a program as root? Do I have to put it in the root directory? Sorry for the dumb questions, just goes to show how new I am.

---

### Post by jhetrick62 on 2008-01-09
To run as root

sudo program_name_here.run

---

### Post by SmasherBasher on 2008-01-09
OK. Thanks. I managed to get that far, then within the Nvidia installation program is where I got the error that it has to be run as root.

---

### Post by jhetrick62 on 2008-01-09
Do you have yourself setup as an administrator?  I also made one error in the syntax.

sudo ./your_program_name_here.run

Jeff

---

### Post by SmasherBasher on 2008-01-10
Okay, I did manage to (I think) get the driver installed. I used the restricted drivers manager to get it to work as suggested above. 
Now, why can't I adjust the screen resolution? I want to go from 800x600 to at least 1024x768 or more. I go into the screen resolution from the system menu, adjust it to what I want hit apply, keep resolution, and it doesnt change anything......

---

### Post by Colin The Grey on 2008-01-10
Fairly new to Ubuntu myself, ran into the same problem with installing NVidia drivers.

Found 2 methods that have helped me get the driver installed:

First one is prob the easiest - download and install ENVY - automatic installer for NVidia drivers.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Just download the .deb to your desktop and double click it to run the installer.

If Envy doesn't work try the instructions on this page:

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)


As for adjusting res etc: both the above methods should auto config it for you - but if not try this (assuming you have the latest driver installed).

Open terminal and enter gksudo /usr/bin/nvidia-settings - this will open the Nvidia Settings program which will allow you to adjust screen res and add to the xserver config file. I use gksudo to launch it as if I just launch it manually from the menu it can't save the updates to the xserver config file due to lack of permissions. the settings you want are under the heading X Server Display configuration. When you have the screen res set to what you want just click Save to X configuration file., and hopefully all should be fine on next reboot.


Hope this helps.

---

