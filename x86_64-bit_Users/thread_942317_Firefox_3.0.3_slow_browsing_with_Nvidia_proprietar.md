---
title: "Firefox 3.0.3 slow browsing with Nvidia proprietary drivers enabled"
date: 2008-10-09
forum: x86 64-bit Users
---

### Post by bramvanvliet on 2008-10-09
Yesterday I did a fresh installation of my laptop with Ubuntu 8.04. (64-bit), with all the necessary updates installed. After enabling the Nvidia proprietary drivers, browsing suddenly became very slow. It can take up to 30 secs before the Gmail login page is loaded, and before Sxipper shows its pop-ups and I can choose the right account to login. It also takes a while, before Sxipper even noticed that I clicked on it, before it starts logging in. The same happens with hotmail and or Yahoo accounts. Normally this all goes pretty fast and smooth. Also a lot of websites are loading pretty slowly, en switching between the tabs in Firefox are not working the way it was like in Ubuntu 7.10. Sometimes Firefox even hangs for a while when I try to switch between the tabs.

After disabling the Nvidia proprietary drivers, it is all working like a charm again. Is this a known bug/problem, and is there already a solution for it to resolve this issue?

My Hardware config:
Dell inspiron 1720, 
Intel® Core&#8482;2 Duo T7100 Processor (1,80 GHz, 800 MHz, 2 MB L2-cache),  
17,0-inch WXGA+ (1.440 x 900),  
nVidia® GeForce Go 8600M GT 256 MB DDR2,
2.048 MB 667 MHz Dual Channel DDR2 SDRAM [2 x 1.024],
Intel® Pro Wireless 3945 802.11a/b/g

---

### Post by ju2wheels on 2008-10-09
Are you sure its the Nvidia driver and not flash on the page? I know my browser does it because the flash is still not stable (although im running Intrepid 64bit). I have not had any issues of this kind while running on my 8500 GT with compiz enabled.

---

### Post by bramvanvliet on 2008-10-09
I am not sure if the problem is the Nvidia proprietary driver. But when I disable the driver, browsing, switching tabs and the use of Sxipper is going the way it was used in Ubuntu 7.10.

Just removed the flashplugin-nonfree in Synaptic, and enable the Nvidia driver. But the problem still remains.

---

### Post by nasar2k2000 on 2008-10-09
i think its something to do with flash AND the NVIDIA drivers.

---

### Post by Morty007 on 2008-10-09
Ok, I had this exact same problem. We have the same video card. Although I'm using linux mint, I installed the drivers initially through envy. It gave me awful compiz performance so I reinstalled and used the driver through the hardware restricted drivers. Now everything is fine.

Sxipper- It sucks up my cpu and will cause lag with your system. I emailed them and they acknowledged this to me in an email. they told me that they are looking for ways to integrate it into the firefox toolbar...like roboform. That damn overlay just sucks up all my cpu cycles. Unfortunately we don't have much of an option at this point.

---

### Post by geologic on 2008-11-03
I seem to be having this problem since upgrading to 8.10 a couple days ago. Everything seemed to work normal in 8.04.

Running the nvidia 173 drivers (downgraded from the 177 drivers because of issues with logging out).

have whatever flash comes with the system. I'm also noticing some of the graphics in gmail are distorted, such as the google logo and the icons for people's status in chat..havent noticed a problem with other sites

---

### Post by aztechclan on 2008-11-08
Hello,
I was having a similar issue, using 177 of the Nvidia drivers.  I am using i686 (not 64bit), but my firefox 3 was unusably slow especially when scrolling etc.  Following the instructions here fixed it for me: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

Very nice to have FF back, and props to Opera for helping me hold out.

---

### Post by JemW on 2008-11-08
> **aztechclan said:**
> Hello,
I was having a similar issue, using 177 of the Nvidia drivers.  I am using i686 (not 64bit), but my firefox 3 was unusably slow especially when scrolling etc.  Following the instructions here fixed it for me: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

Very nice to have FF back, and props to Opera for helping me hold out.

Except that your / nVidia's instructions appear to be out of date. The instructions *only* apply to Version 177.67. I now have 177.80 in Intrepid (there may have been an update that I didn't notice), so please check your version number in X-Server Settings before doing anything.

---

### Post by aztechclan on 2008-11-11
I take it back, the fix above did NOT work, FF3 is still really sluggish.  Not sure why I thought it was fixed, but the settings did seem to make things speed up a *little. Probablly just me.  

I also installed Intrepid on my desktop with NVIDIA GeForce 7800GT and have none of these problems!  It must be related to the NVIDIA chipset in my MacbookPro (SantaRosa) + buggy drivers or something like that.  I've noticed that other applications than FF3 have similar issues, even things like gvim.

---

### Post by aztechclan on 2008-11-11
Oh! Somewhere along the line I was fooled into using the 173.xx driver for NVIDIA!?  (You can see the version in nvidia-settings).  I know for sure I selected 177 for install originally but when I just checked the running version it was 173.  Upgrading to 177.80 has indeed fixed the FF3 scrolling problem I had in 32bit mode.  Sorry to clutter up the thread, since the 64 bit flash thing sounds like a slightly diff problem.

---

### Post by Spoom on 2008-12-10
If anyone's still experiencing this slow tab switching behaviour, I was able to fix it on my laptop after manually specifying the VideoRam in my /etc/X11/xorg.conf and enabling a few tweaks (not sure which of these actually fixed it):

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "true"
    VideoRam       524288
    Option         "AddARGBGLXVisuals" "true"
    Option         "UseEvents" "true"
EndSection
```

Obviously, set the VideoRam to match your card (so if you had a 256MB card, you'd use 256 * 1024 = 262144).

---

### Post by Gias Kay on 2009-01-28
An easy fix:

[FONT="Courier New"]sudo apt-get install nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180[/FONT]

Go to "System > Administration > Hardware Drivers" to enable the version 180 driver, reboot and all problems gone!


Source: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/289964]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/289964")

---

### Post by Morty007 on 2009-01-28
Wait a minute. This thread [http://www.nvnews.net/vbulletin/showthread.php?t=115916&page=46](http://www.nvnews.net/vbulletin/showthread.php?t=115916&page=46)
 
is now at 50 pages and some are saying the 173 driver is better!

---

### Post by Gias Kay on 2009-01-29
Version 180 fixed the bug, period. Try it and you'll see it as I've already done. It's also the first stable version with [VDPAU]("http://en.wikipedia.org/wiki/VDPAU"). I am posting this because many people including me didn't realize that version 180 can already be found and installed through Synaptic despite "Hardware Drivers" not showing it.

---

### Post by Morty007 on 2009-01-29
Ok, which one do I download in synaptic? I see two of them- 180 kernel source and nvidia-glx-180-dev?

Or can you post the terminal command? Thanks!

---

### Post by Gias Kay on 2009-01-29
> **Morty007 said:**
> Ok, which one do I download in synaptic? I see two of them- 180 kernel source and nvidia-glx-180-dev?

Or can you post the terminal command? Thanks!

It's in my first reply.

---

### Post by Morty007 on 2009-01-30
Thanks Gias Kay. Overall there is an improvement, especially in scrolling some websites. However, my burn animation in compiz is still laggy, but not as much. Not sure if there is a cure for that. Maybe you can share you nvidia settings. :p

---

### Post by Morty007 on 2009-02-01
Just wanted to add that 180 did not work out for me. I got total graphical corruption. Maybe the next one will be better.

---

### Post by gammadragon on 2009-02-06
> **Gias Kay said:**
> An easy fix:

[FONT="Courier New"]sudo apt-get install nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180[/FONT]

Go to "System > Administration > Hardware Drivers" to enable the version 180 driver, reboot and all problems gone!


Source: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/289964]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/289964")

This worked great for me. I've been searching for two days for a solution, trying all kinds of things (none of which worked) and it ended up being annoyingly simple.

---

### Post by bicyclebarron on 2009-02-07
I had a similar theme with ATI driver. Adjusted the driver settings and it is better.

---

### Post by lajevardi on 2009-10-23
Having the version 180 mentioned above & the problem with Firefox still persists!

---

### Post by drdos2006 on 2009-10-24
Look for this in your /var/log/syslog file

agpgart-intel 0000:00:00.0: Intel G33 Chipset
agpgart-intel 0000:00:00.0: detected 7164K stolen memory
agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000

If not look for 'No AGP bridge found'
If AGP is not found then reboot into BIOS and turn on secondary video (if on the motherboard ).
You will have to reinstall though otherwise Ubunutu does not bridge the onboard video and your AGP video card.

Check out this thread
Ubuntu 9.04 64bit and Web Browser problems

regards

---

### Post by lajevardi on 2009-10-24
[http://ubuntuforums.org/showthread.php?t=1299253](http://ubuntuforums.org/showthread.php?t=1299253)

---

