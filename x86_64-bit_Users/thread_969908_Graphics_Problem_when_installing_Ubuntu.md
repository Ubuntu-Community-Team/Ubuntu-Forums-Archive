---
title: "Graphics Problem when installing Ubuntu"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by locsphere on 2008-11-03
Disc Version Came from a The Linux Starter Pack Magazine.

Hello I am a bit new to Ubuntu and am having great difficulty just getting the installation Gui to come up. 

First of all they said information is the best thing to getting accurate help so let me start out woth Computer specs

I have an AMD Phenom Quad core Processor Clocked at 2.3 Ghz
k9a2 Platinum Mother board.
video card is the NVIDIA 8800gt
Ram is 5 gb 
I am Running Vista 64 bit on Primary raptor dive and have a secondary raptor drive of 150 gb free and clear of any OS which is the one I would like to use.
I have a Samsung 24" Monitor or Syncmaster  Model t240
I have a dual monitor setup so My secondary Monitor is and LG unknown model.
Wireless Keyboard and Mouse.
Current Issue. 

Ubunto loads up the screen where I can select to install it. I select the first feature at top of list which reads, Start or install ubuntu. 

A loading screen comes up. 

I then get a low resolution setting screen. I then choose to change the setting for better Resolution. 

I can't find My monitor for one. 

I select NVIDIA 8 Series for my video card. 

I then get a screen that is black and looks like a dos promt it  says at the top. 

*Strting Deferred Execution        [OK]
*Starting Periodic Command         [OK]  
*Checking Battery State            [OK]
*Running Local Boot Script         [OK]

_

After reading what is suppose to be a simple installation instructions from the Ubuntu Magazine I am unable to figure out what to do next? There is No GUI (Graphical User Interface) To start the installation and every time I setup the video settings the screen flashes like it doesn't like the settings. it then just sits on the screen I listed above 

*Strting Deferred Execution        [OK]
*Starting Periodic Command         [OK]  
*Checking Battery State            [OK]
*Running Local Boot Script         [OK]

What am I doing wrong?

---

### Post by bwhite82 on 2008-11-03
Don't worry about configuring video right now, do that after installation (just like on Windows). Right now, you just need a driver that is at least remotely usable for installation purposes. That is where 'vesa' comes in. Select that as your video card driver right now.

After installation, goto System>Administration>Hardware Drivers and enable the Nvidia driver there.

---

### Post by locsphere on 2008-11-04
I could Kiss you.

---

### Post by bwhite82 on 2008-11-04
Thanks, but I'll settle for the thread being marked as solved. Glad I could help. :p

---

