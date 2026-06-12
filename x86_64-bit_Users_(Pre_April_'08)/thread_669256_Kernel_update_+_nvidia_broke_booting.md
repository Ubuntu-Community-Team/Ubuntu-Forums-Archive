---
title: "Kernel update + nvidia broke booting"
date: 2008-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkzom on 2008-01-16
Hi all!

I am experiencing some problems when booting with ubuntu 7.10; yesterday night upgraded to the latest kernel and rebooted, then went to "recovery mode" in grub and installed nvidia driver (latest one for 8800 GTS 320Mb), and then when rebooted again, with default boot for the new kernel in grub and nothing came up, I can't even ctrl+alt+Fsomething to switch from terminal to terminal, completely dead.

My surprise is that when I start in recovery mode, after arriving to the login screen, I insert "exit" into the terminal and it shows the nvidia welcome screen together with the X login screen....

Please, could you tell me what have I screwed up? Took a look to xorg.conf but everything is ok... I have given a look to several topics in the forum but I think it is not the same problem, as I can enter into recovery mode...

Thx very much in advance!!

---

### Post by darkzom on 2008-01-17
Anybody can help out there?

I reinstalled the nvidia driver (recovery mode, exit, login screen, log in as me, then switched terminal with ctrl+alt+f4 (e.g) and sudo sh NVIDIA-blablabla.run), reconfigured x, rebooted and still the same problem, so the only way to enter into functional ubuntu is to switch to recovery mode and then type exit into the terminal in order to login as me...

Please, some help or hints on what to search for would be very appreciated, I am new to linux and I am really trying to stay within linux except for playing games (even bought ET:Quake Wars due to the ability to play in linux...)

Thank you very much ;)

---

### Post by brett.hamilton@bredband.n on 2008-01-18
HI Same problem here,if I use the normal process screen goes black then nothing,the only way out sems to be to reboot but looking above there may be another way.
The only work around i found was to boot into recovery mode from grub loader, use init 5 (I gleened this from another video problem discussion, thanks to whoever that was),  then you get an NDVIDIA Slpash screen followed by the login screen and business as it should be.
I cant help thinking the obvious and  that there is some sort of clash between unbutu splash screen and the ndvidia one.
Video card is 8800 gt?
Im a noob at linux but im willing to investigate further provided peeps can point me in the right direction, its the only way to learn in my opinion.

---

### Post by brett.hamilton@bredband.n on 2008-01-18
I may try this to disable the splash screen from this thread
[http://ubuntuforums.org/showthread.php?t=670868](http://ubuntuforums.org/showthread.php?t=670868) and see if that works

---

### Post by darkzom on 2008-01-18
It seems we are experiencing the same problem here. I always experiment the bug regarding the splash screen since 7.04 due to my video card, which is by the way a 8800 GTS (the 320 Mb version). I looked in this forum and got it fixed (showing the boot logo and all) for 7.04 but when I upgraded to 7.10 it appeared again, so I had to add nosplash to the menu.lst.

I have to say that even without adding nosplash, the screen went out of signal but after some seconds it came again and poped with my ubuntu desktop, so it was only a problem of the video during the boot screen.

So far, so good, until now, that the screen goes blank (not out of signal) and there is no way to revive ubuntu.

To brett; try typing "exit" once logged into recovery mode, it does the same but I think it is "cleaner" as you log out from root account to log in to your desired account. I am not sure about this as I am also completely noob.

Anyone can point some hints to us please?

---

### Post by darkzom on 2008-01-19
Nobody with more expertise than us can really answer anything? Ç_Ç

---

### Post by darkzom on 2008-01-26
It seems we are the only ones suffering this problem...

---

### Post by PmDematagoda on 2008-01-26
Ok, try this:-

1) Open the modules file using:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nv_new"
```
and save the file.

3) Reinstall the Nvidia driver and reconfigure the X-Server. After that is done, reboot Ubuntu, it should now work properly.

---

### Post by darkzom on 2008-02-02
Thank you very much PmDematagoda !!

I do not know why I did not receive any e-mail when you replyed to my post... well, I investigated today a little bit further and got to post ok again, in fact, I was going to put here my sucess and how I made it, but I have some new problems with it... hehehe.

I was booting with this options on the kernel; 

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f0dc7131-d03b-4f6c-ba2f-97c2242c59c8 ro quiet splash locale=es_ES vga=791

I had to add noapic and nolapic to make it boot.

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f0dc7131-d03b-4f6c-ba2f-97c2242c59c8 ro nosplash noapic nolapic locale=es_ES

Once I made it boot right, I removed the vga option as it was causing my display to not show anything on the boot stage. However, I discovered that I do not have glx anymore... no compiz and when I run glxgears I get the following:

zom@microZom:~$ glxgears 
Error: glXCreateContext failed

I've just added nv and nv_new to the disabled modules, I am going to reinstall the nvidia drivers and reboot to see if I get some glx working again.

Thank you and I'll come to post any news on that.

EDIT: Yay !! Got it working again when reinstalling nvidia drivers!! Now I wonder if I really need the noapic and nolapic options... next boot I'll try without them. Thx a lot!!!

EDIT 2: Ok, no need for noapic and nolapic options, maybe what keep me out was the VGA option? Dunno...

---

