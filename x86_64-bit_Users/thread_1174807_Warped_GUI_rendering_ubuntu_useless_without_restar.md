---
title: "Warped GUI rendering ubuntu useless without restart"
date: 2009-05-31
forum: x86 64-bit Users
---

### Post by vapblack on 2009-05-31
So I'm running ubuntu x64 on my dell vostro. 
Vostro 220
Intel® Core&#33922; 2 Duo E7400 (2.8GHz, 3M, L2Cache, 1066FSB)
3GB DDR2 SDRAM 800MHZ
Integrated Video, Intel® GMA X4500HD
512 nvidia graphic card

Every once and a while the graphics get all crazy on my and I can't do anything. If I don't catch it on time and restart the computer(or log out then back in) the computer will freeze up and I will have to force a restart through the front power button. It only seems to happen on this computer and not my mom's hp in the other room. She's running x64 as well. 

I've formatted many times and every time I bring x64 back this happens. Here's a screenshot


[IMG]http://farm4.static.flickr.com/3392/3581305811_7eced37336_b.jpg[/IMG]
what should I do?:(

---

### Post by ptn107 on 2009-05-31
If you have desktop effects enabled you should disable them for now.  System -> Preferences -> Appearance -> Visual Effects = none

---

### Post by vapblack on 2009-05-31
I usually have that off. I guess I forgot to turn it off this time. Is that what was causing the warping?
Here's a couple more screenshots from what I just got.[IMG]http://farm3.static.flickr.com/2464/3582296634_c831229996_b.jpg[/IMG]
[IMG]http://farm3.static.flickr.com/2464/3581483489_475aed676c_b.jpg[/IMG]

---

### Post by ptn107 on 2009-06-18
Most likely Ubuntu is using the wrong drivers for your video hardware.

---

### Post by bwallum on 2009-06-18
You may have a 64 bit operating system and find that the driver for your graphics card is 32bit, or that the repos 64bit driver does not work for you. I have had similar problems and now use the latest nvidia 64bit driver from nvidia.

Go to nVidia's web site [HTML]http://www.nvidia.com/object/unix.html[/HTML] research and download the appropriate driver to your Desktop. Do not try to open it.

Right click on the file, select Properties, then the Permissions tab and check the box that allows the file to run as an executable.

Go to System>Administration>Hardware Drivers and make sure that there are no graphics drivers loaded. If green lights show then disable the appropriate driver. 

Here, I am using the file NVIDIA-Linux-x86_64-185.18.14-pkg2.run

Take note of the following instructions because after the next step you will lose the Desktop and all open windows from view.

Open a full screen console. Hold down the ctrl and alt keys, then press the F1 key. When the console appears log in with your normal login name and password.

First remove the lock on the X server with:-
```
sudo rm /tmp/.X0-lock
```
The X server puts a lock on the screen currently in use, in this example screen 0. If you have more than one screen you may need to close these down too. Don't miss the dot before X0-lock and 0 is the numeric zero.

Close down the X server with the following command:-
```
sudo /etc/init.d/gdm stop
``` 
Then change directory to Desktop
```
cd Desktop
```
Then run the nVidia file that you have selected. In this example we will run the NVIDIA-Linux-x86_64-185.18.14-pkg2.run file.
```
sudo sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run 
```
Follow the prompts when the file runs. It can take some time so be patient between steps even if nothing appears to be happening.

When the installer requests permission to compile an nVidia kernel interface choose YES
When the installer requests permission to re-write the xorg.conf file choose YES

When the installer has completed you will be returned to the console prompt. You must wait for this to happen. Then at the prompt reboot the system with:-
```
sudo reboot
```
The nVidia 64bit driver should now be loaded. Note that it will NOT appear in System>Administration>Hardware Drivers. To access the driver controls go to 

System>Preferences>NVIDIA X Server Settings

One last thing, the above procedure is dependant upon the current kernel and compiles a kernel interface for the driver. When the kernel changes you need to re-run this procedure. When the 185 driver gets into the Ubuntu repos then use that instead.

Hope that helps, good luck, Bob.

---

### Post by bwallum on 2009-06-18
PS

If you find that resolutions set with the NVIDIA X Server Settings do not persist after rebooting then go to 

System>Preferences>Display

select no and set the resolution in the Display Preferences window. I don't know why you have to do this but presume it is an oversight in the nvidia settings utility.

---

