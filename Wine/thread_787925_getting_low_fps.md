---
title: "getting low fps"
date: 2008-05-09
forum: Wine
---

### Post by ac1240 on 2008-05-09
why am i getting low fps with games?

---

### Post by zeller on 2008-05-09
What's "low"?

---

### Post by Trance56k on 2008-05-09
We need more info. What game, what version of wine, system specs....etc give more info and you might get an answer.

---

### Post by Catalyst2Death on 2008-05-09
You should also make sure that you have the proprietary drivers installed for your card...
and maybe check for direct rendering and your renderer with: 

```
$glxinfo | grep render
```

if it returns:
direct rendering: yes
OpenGl Render String:<name of card type (nvidia, ati)>

then you should be gold... I doubt that it will though.  If it doesn't then your first step should be ensure that you have your video drivers setup and working properly.

and DON'T use compiz when you play games!!

---

### Post by schtufbox on 2008-05-09
> **Catalyst2Death said:**
> 
and DON'T use compiz when you play games!!

Really depends on your vid card, I only lose around 2 - 5 fps with compiz running, not  worth disabling it for that IMO.

---

### Post by Catalyst2Death on 2008-05-09
Good point.

On my system (or any system with ati drivers)  direct rendering is disabled when compiz is enabled... And so the loss in performance is dramatic.

---

### Post by dtrot55 on 2008-05-10
Im getting LOW FPS in Counter Strike....I turned on the drivers in the Hardware Manager.  I Have a Nvidia 8600 GTXXX 256mb which runs the game perfectly in Windows..i get around 80-100FPS...but in WINE on Ubuntu 8.04 x64 i get 9-20...HUGE DROP!! I have the most recent WINE installed.

Any ideas?

---

### Post by Trance56k on 2008-05-10
I have the same problem with steam games, and I have the same video card.

---

### Post by Ky3r0z on 2008-05-10
Have you tried using envy to install your drivers?

---

### Post by jarrhed on 2008-06-07
Or even better than envy have you tried manually installing them ( I only know how to do this with nvidia)

first go to terminal and type:
sudo apt-get install kernel-package build-essential
now type
sudo passwd root (this is to make it so u can use su) then it will say:
Enter New Unix Password: (Type in here your root password (It can be whatever you want)
Confirm New Unix Password: (Now confirm it)
Now you download the nvidia driver for your architecture
For i386 (The Default one AKA X86 or 32 bit) [http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html)
For AMD64 (or EMT64) (AKA X64 or 64 bit) [http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)


then you push CTRL+ALT+F1 and then  it will say login and you type root then as your password what you put for the root password. After that you type killall gdm. Now you go to where you downloaded the nvidia driver and for me it was the desktop so i typed
cd /home/yourusername/Desktop
then i went to run it by typing
sh *.run
it will come up with a license agreement and just hit enter on I agree
then it will say that theres no pre-compiled interface or something and you just hit ok a bunch
till it builds it
and when it asks about the OpenGL libraries (Only for AMD64 I think) then just hit yes or ok and then as soon as its done you type:
gdm

then login like normal
YOUR DONE!

---

