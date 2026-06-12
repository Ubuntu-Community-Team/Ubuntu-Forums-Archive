---
title: "Guild Wars on Wine"
date: 2008-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by GiPilot12 on 2008-01-15
I am trying to get Guild Wars to run on this laptop. I am running:

Ubuntu 7.10 - the Gutsy Gibbon
and
Wine 0.9.53


Guild wars is installed, but it won't connect to ArenaNet anymore. And when it did connect, the game worked fine except I had abou 5 frames per second or even less :(
 

Please help, I am completely new to Ubuntu


Also i am running a laptop that has:
Inspiron E1505
with an ATI X1400 mobility Video Card.



Guild wars worked fine when i was using Windows, but now doesn't work

---

### Post by Kilz on 2008-01-15
> **GiPilot12 said:**
> I am trying to get Guild Wars to run on this laptop. I am running:

Ubuntu 7.10 - the Gutsy Gibbon
and
Wine 0.9.53


Guild wars is installed, but it won't connect to ArenaNet anymore. And when it did connect, the game worked fine except I had abou 5 frames per second or even less :(
 

Please help, I am completely new to Ubuntu


Also i am running a laptop that has:
Inspiron E1505
with an ATI X1400 mobility Video Card.



Guild wars worked fine when i was using Windows, but now doesn't work

Do you have the accelerated video drivers installed. These are the drivers from ATI, not the repositories. [This guide should help if you do not.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually")

---

### Post by GiPilot12 on 2008-01-15
thanks, but I have no idea what

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.


means 

Sorry I am so clueless :(


and In addition, I keep getting this message in the terminal

Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)'
in the drive '/cdrom/' and press enter


I am not sure what it means.

---

### Post by Kilz on 2008-01-15
> **GiPilot12 said:**
> thanks, but I have no idea what

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.


means 

Sorry I am so clueless :(


and In addition, I keep getting this message in the terminal

Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)'
in the drive '/cdrom/' and press enter


I am not sure what it means.

The message is asking you to install the install media you installed Gutsy with. Odds are that you have asked for something to be installed and it is on that disk.
[You may also want to look at this site]("http://www.monkeyblog.org/ubuntu/installing/") for information on the repositories. I would recommend adding it to your favorites.

The link I gave you in my previous post is a howto. Follow it, for the commands its possible to copy , then right click on the terminal and paste them into place. This will install the video card driver from ATI. That should solve the frame rate problem from your first post.

---

### Post by GiPilot12 on 2008-01-15
Thanks so much :) so far so good. Everything is looking great :) 

Game is running well around 50fps (I could probably improve it if I turned off the desktop cube and other effects) and I am loving this OS even more


Thanks guys :)

---

