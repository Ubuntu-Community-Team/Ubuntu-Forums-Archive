---
title: "Cedega 5.0"
date: 2005-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by jammupatu on 2005-11-11
Hello all!

Has anyone gotten Cedega 5.0 installed properly with 5.10 Ubuntu? I forced the i386 deb of Cedega but when I try to run for example the video tests I get libXxf86vm.so.1 not found errors on console screen. 

Next step was to try [http://www.ubuntuforums.org/showthread.php?p=475023#post475023](http://www.ubuntuforums.org/showthread.php?p=475023#post475023) with bad luck also. I did get the WoW installer fired up. The installer went almost through but crashed in the end. The video tests run from Cedega lock up the whole pc, too.

Any ideas? =)

-j-

---

### Post by theh0g on 2005-11-11
I never had any problems with it, though if 4.4.3 works for you, use it. I've read many WoW users still use it since there is no difference between versions. Oh, my WoW got installed under Windows (months back) and I just copied it to ext3 partition, works (including patches) like a charm. But do check: [http://transgaming.org/forum/viewforum.php?f=51](http://transgaming.org/forum/viewforum.php?f=51)

---

### Post by jammupatu on 2005-11-11
So you've gotten it to work with amd64 version of Ubuntu? Sorry for not mentioning it explicitly.

-j-

---

### Post by fallencan on 2005-11-11
hi
im new to ubuntu and linux. somehow i managed to install vga drivers and i installed cedega 5.0 from .deb file. i'm trying to install some games but nothing happens. i follow all the step that explained in transgamings howto but nothing happens. what i am doing wrong? or am i forget to install something? thanks anyway.

---

### Post by dolny on 2005-11-12
Update after installation. You also need the Cedega 5 engine which is not in the deb by default... you have to download it. Anyway Cedega 5 didn't change anything for me - still Day of Defeat works at 5FPS (on P IV Celeron 2.8, 512 DDR RAM, ATI Radeon 9600 Pro).

---

### Post by fallencan on 2005-11-12
hi
i updated the program while first time setup wizard executed. it downloaded all ms core fonts, mozcontrol, and cedega engine and i haven't seen an error message so i   assume everyting went ok. but still i can't install anything. after clicking install button and continue noting happens. is there some other programs i have to install?

---

### Post by action09 on 2005-11-12
mozcontrol ?

what is it ? can't install it from 'apt'  how did you installed it ?

cf:
---
Installing Add-Ons (Mozilla Control and Microsoft Core Fonts)

For best performance, Cedega requires some additional packages: the Mozilla Control package and the Microsoft Core Fonts package.

The Mozilla Control allows programs that use embedded HTML to be correctly displayed.

---

### Post by monchichi on 2005-11-12
make sure you have all the ia32 and lib32 compatibility files installed, then install cedega on the command line with dpkg -i --force-architecture ./cedega_5.0.1_i386.deb

then everything should run fine. fwiw, the 3d acceleration and alsa sound tests fail... but everything works great in the games. cedega has always has dodgy alsa support, just use oss emulation. and 3d acceleration does work, the test lies. i can play morrowind, guild wars, wc3, and others flawlessly.

---

### Post by action09 on 2005-11-12
Thanks for this answer and for your help ! :)

---

### Post by frodon on 2005-11-13
Same for me, all my games don't works since i update to cedega 5.0, thanks cedega ;)
I don't know why, before i used only command lines to lauch my games and now you have this GUI which make things harder than they would be.
If anyone could tell me how to successfully install a game with cedega 5.0. i  will really appreciate :)
I have cedega 5.0.1 installed and cedega 5.0 engine and the only message i get in terminal when i try to install a game is : wine: Unhandled exception, starting debugger...
And now when i try to use the old versions of cedega, it doen't work so i'm locked now.

---

### Post by monchichi on 2005-11-14
[QUOTE=frodon]Same for me, all my games don't works since i update to cedega 5.0, thanks cedega ;)
I don't know why, before i used only command lines to lauch my games and now you have this GUI which make things harder than they would be.
If anyone could tell me how to successfully install a game with cedega 5.0. i  will really appreciate :)
I have cedega 5.0.1 installed and cedega 5.0 engine and the only message i get in terminal when i try to install a game is : wine: Unhandled exception, starting debugger...
And now when i try to use the old versions of cedega, it doen't work so i'm locked now.[/QUOTE]


You can still run Cedega from the command line (sort of). Read this thread: [http://transgaming.org/forum/viewtopic.php?t=4461](http://transgaming.org/forum/viewtopic.php?t=4461)

as far as getting your games to work... it could be a million things. don't use alsa; use oss. make sure you have 32-bit compatability libraries installed. does dmesg or running cedega with "-debugmessage+all" anything give you anything useful?

---

### Post by frodon on 2005-11-14
Great !

I will try that this evening. Thanks for the answer monchichi.

---

### Post by jammupatu on 2005-11-15
I tried to install Cedega 5.0.1 full and small with no luck. 5.0.1 supports the old fashioned commandline (cedega WoW.exe for example). When I try that, Cedega just exits out without saying anything.

I haven't done 32bit chroot but I do have all ia32 libraries installed. 

If someone has gotten this thing to work without a chroot, please say how and / or post the dpkg -l of all packages...

BR,

-j-

---

### Post by beerwolf on 2005-11-23
here is the step i did :
1- install ia32
2- install lib32
3- sudo dpkg -i --force-architecture cedega-small_5.0.1_i386.deb

Cedega works the only problem left is the alsa test fails and the 3d  test also fails but the 3d works so i'm able to play!

---

### Post by jammupatu on 2005-11-24
[QUOTE=beerwolf]here is the step i did :
1- install ia32
2- install lib32
3- sudo dpkg -i --force-architecture cedega-small_5.0.1_i386.deb

Cedega works the only problem left is the alsa test fails and the 3d  test also fails but the 3d works so i'm able to play![/QUOTE]

I will definitely try this today. Stay tuned.

---

### Post by Snipersnest on 2005-11-25
I installed Steam games without a problem... I also got Guild Wars going without a problem too.. 

I honestly don't see how using a GUI is harder than editing lines of text. The GUI does all the work for you mostly.

My 3D Accell fails....3D works yes, but its a Mesa version... which renders slower. So some 3D games are more laggy than they should be. i.e. Guild Wars.

I should be pulling about 15,000 fps in glxgears but I'm only getting 14,000... I can't figure out how to change the Mesa version to the correct one so I can have full 3D support.

---

### Post by beerwolf on 2005-11-25
[QUOTE=Snipersnest]I installed Steam games without a problem... I also got Guild Wars going without a problem too.. 

I honestly don't see how using a GUI is harder than editing lines of text. The GUI does all the work for you mostly.

My 3D Accell fails....3D works yes, but its a Mesa version... which renders slower. So some 3D games are more laggy than they should be. i.e. Guild Wars.

I should be pulling about 15,000 fps in glxgears but I'm only getting 14,000... I can't figure out how to change the Mesa version to the correct one so I can have full 3D support.[/QUOTE]
I guess you have an NVIDIA card. 
I extract these step from the ubunyu starter guide:
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

this is ONLY for NVIDIA card:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

Save the edited file
LOGOFF, and CTRL+ALT+BACKSPACE or Reboot you computer. 

to access Nidia setting : Applications -> System Tools -> NVIDIA Settings

---

### Post by Snipersnest on 2005-11-25
Thanks for that tutorial...however that doesn't fix the 3D accell problem for me.. my 3D is using "Mesa" and I can't figure out how to change it to use the nvidia libs.. 

Your correct, NORMALLY nvidia-glx will do it for you.. however with PCIX and my 64bit it didn't change it.  That tutorial is how I installed my drivers...many people are having this problem with Cedega 5.0 not sure why.

---

