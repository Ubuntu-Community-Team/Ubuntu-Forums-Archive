---
title: "Ubuntu Amd64 + NVidia drivers"
date: 2005-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by banasw01 on 2005-12-10
So I installed 5.10 and everything looks great. I visited [www.nvidia.com](www.nvidia.com) and downloaded the driver NVIDIA-Linux-x86_64-1.0-8174-pkg2.run I press ctrl+alt F2, log in as root, and type killall gdm. I type sh (driver name) and here is were problems begin. The program wants to compile a driver for my kernel. This use to work "great" before, but not now. First it tells me that I need ld. LD? WTF is ld? Oh ok, that is part of gcc. Oh no problem, lets get gcc installed using synaptic. No problem. So I should use the newest? gcc 4.0? Lets try it. Oh wow, you mean you want to use gcc 4.0, but your kernel was compiled with 3.4??? Forget it!!! You want to uninstall gcc 4.0 and install 3.4? You can't do that, because other programs need 4.0 really bad. Ok, lets see what the program says now. Shoot! I need libc dev, doh I should know that LOL. Lets install that too and try again. Oh, sorry make is not installed you can not compile your driver. Oh come on.... grrrrrr. Lets install make too. What do I need now? Oh sorry again.... you don't have source for your running kernel installed, bummer! Lets install it and see what I need to compile my driver for my NVidia video card. Darn! Are you sure you installed the right kernel source? I can't compile your driver, sorry. You idiot! you can't find and choose the right kernel source, omg you're so stupid.

I originally wanted to play some World of Warcraft using Transgaming Cedega 5.0, but I guess I will just reboot and play some in Windows. Maybe try another day... LOL. User Friendly??? LOL

Now here someone will tell me how to fix, my problem. But I don't really want to know how to fix it. I just want to play WOW, TODAY!

---

### Post by AvixK7 on 2005-12-10
This is a pathetic rant that won't get you anywhere.

you just needed to run Synaptic package manager and it would have installed everything for you automatically.

I"m new with linux too, so I don't know how to fix your problem. but I know that asking a lot of questions with proper descriptions of your problem will get you answers rather than ranting and trolling around the forum.

Good luck.

---

### Post by rplantz on 2005-12-10
[QUOTE=banasw01]I originally wanted to play some World of Warcraft using Transgaming Cedega 5.0, but I guess I will just reboot and play some in Windows. Maybe try another day... LOL. User Friendly??? LOL

Now here someone will tell me how to fix, my problem. But I don't really want to know how to fix it. I just want to play WOW, TODAY![/QUOTE]

I guess "user friendly" depends on what one is looking for.

I've never played World of Warcraft, but the other things you describe sound like great fun to me. :-)

---

### Post by banasw01 on 2005-12-10
Thank you for your reply rplantz. It has been few hours since my failed attempt at linux gaming. I made this post to make a point that some things are getting better, but some things are still the same. I started "playing" with Linux in 2000 and had to learn a lot to make it work for me. Six years have passed, and I still can't get my 3D driver to work right. A task that is trivial in Windows. Oh well, I'll try again in a couple of years.

---

### Post by TripHammer on 2005-12-11
First off, you should have have at lest glanced at the Nvidia readme, you would have known that you need gcc, make, and your kernel headers before your even think about building a kernel module.

As for the gcc issue, simply:```
apt-get install gcc-3.4
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
```All we are doing here is changing the symbolic link 'gcc' from pointing to gcc-4.0 to gcc-3.4, that way the Nvidia installer won't give you any problems relating to compilier version.  You don't need to remove gcc 4.0 or anything like that.

---

### Post by padams on 2005-12-11
Changing the simlink is not advisable by any means.  The simple way to sort out the gcc part of the problem is to to use:

export CC=gcc-3.4

before running the install for the nVidia drivers.  This is actually documented in the driver's README.

---

### Post by jon_gunnar on 2005-12-11
[QUOTE=banasw01]Thank you for your reply rplantz. It has been few hours since my failed attempt at linux gaming. I made this post to make a point that some things are getting better, but some things are still the same. I started "playing" with Linux in 2000 and had to learn a lot to make it work for me. Six years have passed, and I still can't get my 3D driver to work right. A task that is trivial in Windows. Oh well, I'll try again in a couple of years.[/QUOTE]

Did you bother to read the first ansver you got at all. A few click in Synaptic would have done the job. Should be simple enought, no?

---

### Post by gpw797 on 2005-12-11
[QUOTE=banasw01]Oh well, I'll try again in a couple of years.[/QUOTE]

Isn't WOW a windows only game? Is there a linux version of game? Games written for linux like quake, doom etc.. work great. You shouldn't get all excited because you can't run a windows game in linux, try running some linux software in windows and let me know how that works for you.

---

### Post by banasw01 on 2005-12-11
[QUOTE=jon_gunnar]Did you bother to read the first ansver you got at all. A few click in Synaptic would have done the job. Should be simple enought, no?[/QUOTE]

Have you ever had to read a README to install a driver in windows? I don't remember last time I had to do that.

---

### Post by banasw01 on 2005-12-11
[QUOTE=gpw797]Isn't WOW a windows only game? Is there a linux version of game? Games written for linux like quake, doom etc.. work great. You shouldn't get all excited because you can't run a windows game in linux, try running some linux software in windows and let me know how that works for you.[/QUOTE]

WOW works under Linux using the Transgaming Cedega software. It is officially supported by Transgaming, see: [http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by predaeus on 2005-12-11
[QUOTE=gpw797]Isn't WOW a windows only game? Is there a linux version of game? Games written for linux like quake, doom etc.. work great. You shouldn't get all excited because you can't run a windows game in linux, try running some linux software in windows and let me know how that works for you.[/QUOTE]

As far as I know Cedega is a tool that alows you to run directx games on linux systems.

[QUOTE=banasw01]Have you ever had to read a README to install a driver in windows? I don't remember last time I had to do that.[/QUOTE]
That is neither Ubuntu's nor GNU/Linux's fault. The problem lies with NVIDIA and open source politics in general. I know it is frustrating but the Ubuntu community is quite nice and can help you out if you know what to ask for.

---

### Post by banasw01 on 2005-12-11
Thank you for your reply predaeus. I have a question. Is there a good reason why the Ubuntu 5.10 cd does not install gcc, libc-dev, make and linux-source by default? I know this would make installing NVidia drivers a lot easier for people with NVidia video cards (and I think those are pretty popular).

---

### Post by RAOF on 2005-12-11
[QUOTE=banasw01]Thank you for your reply predaeus. I have a question. Is there a good reason why the Ubuntu 5.10 cd does not install gcc, libc-dev, make and linux-source by default? I know this would make installing NVidia drivers a lot easier for people with NVidia video cards (and I think those are pretty popular).[/QUOTE]
Because, in general, people don't need gcc & all the dev packages.  For those who do need the dev packages, it's simple enough to apt-get/synaptic them.  People should never **need** to build from source.

You've actually made it harder for yourself at the beginning.  The **easy** way to install the nvidia drivers is to get the nvidia-glx package through apt-get/synaptic.  This installs the drivers and puts the 32bit compatibility libraries in the right place.  Then running nvidia-glx-config enable tells X to use the new nvidia drivers.  This will get the version 76.67 drivers, which should work fine, unless you know otherwise (ie: you have a 7800GTX or you have an SLI setup).

---

### Post by banasw01 on 2005-12-12
Thank you RAOF. That sounds like something a newbie like me could do.

I messed around with it a little yesterday and the NVidia driver told me that my kernel was compiled with gcc 3.4 and my current gcc was 4.0. So I tried to uninstall gcc 4.0 and synaptic uninstalled everything that depended on gcc 4.0 That broke my system lol. I will reinstall and try your method.

I'll be back.

---

### Post by LordDante on 2005-12-12
[QUOTE=banasw01]Have you ever had to read a README to install a driver in windows? I don't remember last time I had to do that.[/QUOTE]

that is your problem.. since readmes actually do contain some usefull information.. If you dont read readmes why do you upgrade drivers??? newer=better? :rolleyes: do you know that 90% of the win people upgrade their drivers without removing the old ones.. and later on they complain about "driver issues" gues what the readme says about that? oh, right, you dont read them do you #-o 

by the way... it is common sense to ask synaptic "hey i have Nvidia, does anyone else have nvidia? do you have it in the repository"

---

### Post by banasw01 on 2005-12-12
[QUOTE=LordDante]that is your problem.. since readmes actually do contain some usefull information.. If you dont read readmes why do you upgrade drivers??? newer=better? :rolleyes: do you know that 90% of the win people upgrade their drivers without removing the old ones.. and later on they complain about "driver issues" gues what the readme says about that? oh, right, you dont read them do you #-o [/QUOTE]

I always remove my old video drivers before installing new ones in Windows, because that is common sense. Most of the time there are only generic Windows drivers installed because I install NVidia display drivers right after restoring from a backup image.

[QUOTE=LordDante]
by the way... it is common sense to ask synaptic "hey i have Nvidia, does anyone else have nvidia? do you have it in the repository"[/QUOTE]

Ok, I will add that to my common sense repository.

---

### Post by banasw01 on 2005-12-12
[QUOTE=RAOF]Because, in general, people don't need gcc & all the dev packages.  For those who do need the dev packages, it's simple enough to apt-get/synaptic them.  People should never **need** to build from source.

You've actually made it harder for yourself at the beginning.  The **easy** way to install the nvidia drivers is to get the nvidia-glx package through apt-get/synaptic.  This installs the drivers and puts the 32bit compatibility libraries in the right place.  Then running nvidia-glx-config enable tells X to use the new nvidia drivers.  This will get the version 76.67 drivers, which should work fine, unless you know otherwise (ie: you have a 7800GTX or you have an SLI setup).[/QUOTE]

RAOF you are a genius. That worked and it was very easy. Thank you!!! :D

---

### Post by RAOF on 2005-12-12
Apt-get/synaptic is the solution to all the world's problems ;)

---

### Post by darkpark on 2005-12-14
[QUOTE=RAOF]Apt-get/synaptic is the solution to all the world's problems ;)[/QUOTE]

Almost!   If I (or anyone else) could order a pizza and a case of Mountain Dew via apt-get/synaptic than we'd be in business!  :D 

say, did the GUI seem to get a little sluggish for anyone after installing the nvidia-glx driver and running "nvidia-glx-config enable"?  

running an AMD64 3500+ w/ nvidia 6800GT and the nvidia drivers that come with ubuntu 5.10 version 1.7667?

---

### Post by tburns on 2005-12-14
[QUOTE=banasw01]Thank you for your reply predaeus. I have a question. Is there a good reason why the Ubuntu 5.10 cd does not install gcc, libc-dev, make and linux-source by default? I know this would make installing NVidia drivers a lot easier for people with NVidia video cards (and I think those are pretty popular).[/QUOTE]

I imagine space is the primary concern with excluding those packages. I personally like the fact that Ubuntu installs with a single CD. And synaptic or apt-get can get just about everything else.

---

### Post by RAOF on 2005-12-14
[QUOTE=darkpark]Almost!   If I (or anyone else) could order a pizza and a case of Mountain Dew via apt-get/synaptic than we'd be in business!  :D 

say, did the GUI seem to get a little sluggish for anyone after installing the nvidia-glx driver and running "nvidia-glx-config enable"?  

running an AMD64 3500+ w/ nvidia 6800GT and the nvidia drivers that come with ubuntu 5.10 version 1.7667?[/QUOTE]
Sluggish?  No!  If anything, the opposite.  Maybe you should check that the option "renderaccel" is enabled in xorg.conf?

---

