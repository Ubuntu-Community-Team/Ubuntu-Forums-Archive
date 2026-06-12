---
title: "Xorg.conf for Ubuntu 7.10 amd64"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by tsairox on 2007-10-18
Hi all,

Like many Linux users, I downloaded Ubuntu 7.10 amd64 this morning.  I can't get past the xorg.conf issues.  I can't even ctrl-alt-f1 to fix anything.  The screen just blinks at me.  I have a Viewsonic E90f monitor and do no know the proper adjustments to make in xorg.conf to fix it.

Can anyone tell me how to get into the xorg.conf file and what the settings would be for this monitor.  Oh, I also have a Geforce 7600 Nvidia graphics card.  Re: I can't ctrl-alt-f1 or ctrl-alt-backspace into terminal.

Thanks for any help,

trox

---

### Post by Silent Ninja on 2007-10-18
I've the same thing that you, I'm on a Sempron 3500+ and i've an nVidia go 6100, and ubuntu gutsy, just starts, but never shows anything past the grub loader. You can start in recovery mode (switching the kernel on the grub load) and change stuff.. but i've don't know yet which thing to modify.

---

### Post by John.Michael.Kane on 2007-10-18
I can't reproduce this error, and I'm on a machine with a geforce6100. I installed gutsy 7.10 using the alternate cd iso.

You can see if the info in the thread below offers any help.
[http://ubuntuforums.org/showthread.php?t=574124](http://ubuntuforums.org/showthread.php?t=574124)

---

### Post by Silent Ninja on 2007-10-18
I'll tell you step by step:

I'm on a notebook (or laptop if you preffer), with a Sempron 3500+ 64bits processor, nVidia GeForce Go 6100, a widescreen (1280x800) monitor... and, some other stuff that comes built in that don't handle video.. so...

I've managed to clean install from the ubuntu gutsy 7.10 live cd (not the alternate), but i've to set the vga video to 1024x768 because if i didn't it hang up and the screen goes black.. afther beginning it automatically sets the 1280x800 resolution.

So, afther the install.. it never EVER, showed me something on the screen afther the grub loader, it shows only a black screen. So, i went to text (recovery) mode. It worked.. i was able to startx from there, and it worked to.. but with some limitations. 

And so.. i've tried to install the nvidia-glx-new with apt-get or the restricted drivers engine but i could't do it, keeps telling me that it doesn't exists anymore. So, i've downloaded the new driver from nvidia, but it says it's no good to install it on recovery mode.. so, i'm not able to do it.

Any ideas?

---

### Post by Nick Payne on 2007-10-18
Try the alternate install CD instead. I haven't downloaded the release version yet, but I had no problems with either the beta or the RC CD when installing on a machine with a Geforce 7600 dual head video card.

---

### Post by LoneWolfJack on 2007-10-19
not sure if this will help you, but it solved my little startup problems:

when in recovery mode, find your xorg.conf file and use vi to find where you have the screen resolutions listed... looks something like this (even though this might be ATI-specific):

"1152x768" "1024x768" "800x600" "640x480"

add your desired screen resolution to that list and make sure it is the first value in line. you can also specify a frequency setting like "1152x768@80".

there is probably another conf file somewhere where you have to specify the screen resolution again as my monitor still shows a blinking "invalid frequency" text before it gets to the login screen. I didn't get there yet... too many other problems. ;-)

---

### Post by oodledoodle on 2007-10-19
ok, this is how to hopefully boot into a default xorg if that is what is needed. 

when your pc is loading and the grub loader message appears, press escape. boot into ubuntu recovery mode. 

enter this command at the command prompt

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will reset your xorg to a default setting. 

if you simply want to edit your xorg then type 

```
nano /etc/X11/xorg.conf 
```

at the command prompt. this will allow you to make changes to it but i am unable to give you any help with regards to your monitor, sorry.

---

