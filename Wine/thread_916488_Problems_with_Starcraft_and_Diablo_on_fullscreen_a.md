---
title: "Problems with Starcraft and Diablo on fullscreen and nvidia"
date: 2008-09-10
forum: Wine
---

### Post by hellfire_bg on 2008-09-10
I am trying to run Diablo 2 Lord of Destruction and Starcraft Brood War and both have the same problem - if i start the game in Fullscreen the game does not stretch on the whole screen but rather sits on the top left corner of the screen. I`ve tried this with both cedega and wine. In wine the game keeps its original aspect ratio and stays in the left top corner of the screen, in cedega it changes the aspect ration but again stays on the top left corner of the screen. All of this is happening on a Thinkpad T61 14,1 (1440x900) laptop with NVidia Quadro NVS 140M and the nvidia 173.14.09 drivers installed (on x86_64 system). Here are some screenshots to see how it looks. The first one is with cedega, the second with wine. 
[[IMG]http://img258.imageshack.us/img258/605/17532774zk7.th.png[/IMG]](http://img258.imageshack.us/my.php?image=17532774zk7.png)
[[IMG]http://img205.imageshack.us/img205/8499/36382579tr0.th.png[/IMG]](http://img205.imageshack.us/my.php?image=36382579tr0.png)
I also have a second laptop - Acer Travelmate 2492NWLMi with Intel GMA 950 - there the both games just stretch on the entire screen (thus changing their aspect ratio) - this is fine by me and i would like to achieve the same effect on the Thinkpad. I guess it is something with the drivers because if i try the nv driver it goes fullscreen but does not stretch - the games retain their original aspect ratio and there are black bars to the left and to the right. This is not an option for me first because i need the 3d and second because it is still not the way i want it - i want the game to stretch on the entire screen.

---

### Post by Zeike on 2008-10-13
I have the exact same issue, also with a Thinkpad T61 w/nvidia.

Shameless bump.

---

### Post by alkamid on 2008-11-23
The same issue here. Bump

(ThinkPad T61 user)

---

### Post by jorj82 on 2008-11-23
I had this problem, too.  The only way around this was changing my desktop resolution to 640x480 (the native res for starcraft) before playing.  Not really a fix, but it worked.

---

### Post by hellfire_bg on 2009-02-02
Well my laptop screen does not appear to support this resolution.
> hellfire@debian:~/&#1048;&#1075;&#1088;&#1080;/Starcraft$ xrandr
Screen 0: minimum 512 x 384, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0     52.0     53.0     61.0  
   1280x800       54.0  
   1280x768       55.0  
   1024x768       56.0  
   720x450        57.0  
   640x400        58.0  
   640x384        59.0  
   512x384        60.0  

I tried the soltion mentioned here:
[http://ubuntuforums.org/showthread.php?t=822888&highlight=starcraft+widescreen]("http://ubuntuforums.org/showthread.php?t=822888&highlight=starcraft+widescreen")
However instead of 640x480 it changes my resolution to 640x384 and i miss the bottom part of the screen.

---

### Post by BDNiner on 2009-02-18
Is there a solution to this issue? I don't mind playing in a window if i can change the resolution to anything higher than the default.

---

### Post by Kareeser on 2009-02-19
I don't believe so, since the games are too old to go any higher than 1024x768.

Try telling wine to emulate a desktop, so you can at least play in a window.

---

### Post by BDNiner on 2009-02-20
That is the way i have it now. I really like playing in a window since i can use other apps like pidgin. I was just hoping that the window could be made larger.

---

### Post by havok1977 on 2009-02-21
Im having the exact same issue on a Sony Vaio with an ATI Readeon 9200; and the weird thing is: it was stretching fine until today!!! And I didnt make any changes to my configs to cause it, only updated to the latest kernel version and installed some additional software that is related to wine: playonlinux... 

I will remove that app and reboot on the older kernel version; but can anyone confirm what could cause this?

---

### Post by sensei240 on 2009-06-13
Hey everyone, I found a solution to Nvidia-carded Thinkpads with NO BIOS OPTION for display:

Right-click your desktop and click on NVIDIA Control Panel (or go to it elsewhere if it's not in your menu)
Create a custom resolution (640x480)
You can now use Fn+f7 to make a custom profile - I even made mine launch StarCraft automatically when I enable it!

Good luck!

- sensei240

---

### Post by thaimin on 2009-06-20
An even easier method is if you set up the custom resolution with 640x480 and 8 bit color. 16 and 32 bit color will not work and the resolution must be 640x480. With this custom resolution in place, at least in a purely Windows environment, Starcraft is able to take up the whole screen ON ITS OWN. No need for special shortcuts or whatever. No other bit depth works to have Starcraft do it by itself.

It is probably because Starcraft requests a 640x480x8 screen when it starts up and the graphics card says it supports it only if the bit depth matches the custom.

I have never used Wine so I'm not sure if it will work or not, but I don't have Linux running when playing games on my laptop.

---

