---
title: "nvidia driver on Thinkpad T61"
date: 2007-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by plutino on 2007-09-22
Hi there,

I follow this link ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Audio](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61#Audio))  to install the nvidia driver on my Thinkpad T61.  Everything works find after the installation -- gdm restarts beautifully and the driver selects the optimized resolution automatically.  Problem occurs, however, after I reboot the computer.  The Xorg error report shows that the nvidia kernal module has an incompatible version.

I did find a fix for this:  first do a `sudo rmmod nvidia', the a `sudo modprobe nvidia', and restart gdm, fine.  But the problem is, I have to do this everytime I boot up the computer.  Does anyone have any idea what's going on?

Thanks.

---

### Post by Sockerdrickan on 2007-09-23
I have no idea but you could do one of the following:
Re install the driver
Do a startup script of the commands you use

---

### Post by plutino on 2007-09-26
solved.  I restalled the driver and enable it using the Xubuntu restricted module manager instead of "nvidia-glx-config".  Thanks for the suggestion

---

### Post by John Jason Jordan on 2007-10-22
Yesterday I opened the box on a brand new Thinkpad T61. Before turning it on the first time I inserted a Gutsy amd64 DVD in the drive, then proceeded to wipe out the factory partitions and install Gutsy as the only OS. There were a few glitches with the video during the install, but eventually I got it running at 1680 x 1050. Later I used the Restricted Drivers Manager to install the nVidia drivers, then I enabled compiz and set it to the third (high) setting. 

Everything was working fine for some time, including during reboots, but suddenly the wallpaper (actually I had set it to no wallpaper and a white color) suddenly changed to the default Ubuntu pink-brown. I went back into Appearance, but it refused to take any changes to the color. I decided to reboot. When it came back up again the video was at 640 x 480 and I got the "Ubuntu is using the default video" popup. 

The popup has a Configure button, but most of the stuff didn't work properly. For example, I could select the nVidia driver and set the screen to Generic 1680 x 1050, but when going back to the main window it was still on "Plug and Play." It wouldn't take the changes. 

Here is lspci:
jjj@Devil7:~$ lspci |grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)

At this moment I finally got it back to 1680 x 1050, but I suspect it is still not right. If I reboot sometimes it goes back to VGA and the Configure button on the popup window still doesn't get it working right. I have to let it boot in VGA, reset the nVidia driver with Restricted Drivers Manager and then reboot. Afterwards it comes up correctly, but if I shutdown and restart again, sometimes it will go back to VGA and I have to go through the Restricted Driver Manager routine again. And I still can't change the desktop background color. (And I really need to do that, because the default titty-pink-brown is so not me.)

I tried to edit the xorg.conf file, but decided to leave it until I learn more about what the sections do. For example, there are six sections that leave me confused as to what they are for:

Section "Device"
Section "Monitor"
Section "Screen"
Section "device" #
Section "monitor" #
Section "screen" #

I hope someone here has the same video and has it properly configured on a T61. If so, can you post your xorg.conf file? 

Also, when it boots I do not get the Ubuntu splash screen with the progress bar. And sometimes the boot process just hangs. The end of the boot line in menu.lst (after the UUID number) says "ro quiet splash." I think that means it is supposed to display the splash screen and progress bar, but for some reason it is not doing so. This may be related to the video issues. 

Other than the video issues, everything "just works" - bluetooth, wireless, everything. I love this machine. Any help getting the video issues resolved would be greatly appreciated.

---

### Post by Ehtetur on 2007-10-25
I had to run **nvidia-settings** or **nvidia-config** (forgot which one it was??) from a terminal to set my video, Dapper wouldn't properly set up the video so I used the nvidia program.
I don't have the machine anymore but I think the same applies to Gutsy,

---

### Post by NigelHarrison on 2007-10-27
It's nvidia-settings (not that I understand what most of the options actually do).

Nigel

---

