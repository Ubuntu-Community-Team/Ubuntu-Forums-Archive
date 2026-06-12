---
title: "Flying Model Simulator (FMS) in Wine"
date: 2008-07-27
forum: Wine
---

### Post by Gyrotwister on 2008-07-27
FMS is a popular simulator for practising flying model aircraft.  It's written for Windows and is free  to download and use.  
After reading about a way of getting the recommended Version running in vista I decided to try and apply that same solution in Wine.  

After installing FMS Version 2.0 Beta 7 and dumping d3drm.dll in the same directory I found that it almost worked.  My el cheapo Esky USB controller was recognised and calibrated OK.  The plane took off and flew but only the top 20% of the screen was was being animated.  The bottom 80% stayed frozen.  

What else can I try to get the video working properly?  

I'm using Wine 1.1.2  Ubuntu Hardy 8.04

---

### Post by LinuxRocks713 on 2008-07-28
> **Gyrotwister said:**
> FMS is a popular simulator for practicing flying model aircraft.  It's written for Windows and is free  to download and use.  
After reading about a way of getting the recommended Version running in vista I decided to try and apply that same solution in Wine.  

After installing FMS Version 2.0 Beta 7 and dumping d3drm.dll in the same directory I found that it almost worked.  My el cheapo Esky USB controller was recognized and calibrated OK.  The plane took off and flew but only the top 20% of the screen was was being animated.  The bottom 80% stayed frozen.  

What else can I try to get the video working properly?  

I'm using Wine 1.1.2  Ubuntu Hardy 8.04

You have 3 choices:

1. Get Windows. Now.

2. Run Windows XP in a VM with your FMS app.

3. Recompile FMS (if opensource) with winelib and wineg++. You will most likely need extra libraries and headers.

---

### Post by Gyrotwister on 2008-08-03
I have this program installed on my xp partition so I'm really not desperate to have it working under WINE but it would be nice to have one less reason to boot to the other OS.  

I'm no expert but it seemed to me this program is running OK except for 80% of the graphics.  The sound works.  The behind the scenes number crunching seems to work OK too because the altimeter and airspeed readings indicate the model actually flies.  If I do loops in Chase view mode I can see the top 20% of the screen alternate between sky-ground-sky-ground etc.    

LinuxRocks713, you seem quite adamant that it can't be done but you haven't stated how you formed your conclusion.  

Can any one else suggest anything?  Perhaps some more dll files?

---

### Post by pabloab777 on 2011-02-14
Don't forget to tell us your experience with FMS on Ubuntu on Wine AppDB, [this is the article for FMS]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2907").

---

### Post by mark bower on 2012-12-09
Has anyone had success installing FMS simulator in Wine and Ubuntu 12.04?  I am using Linux native driver for an ATI Radeon 9200 PRO card.

I followed the lead in this thread and copied the d3drm.dll file into the FMS location.  Function:

1)the program boots with a black screen
2)pull down menus are visible & functional except black screen means no model
3)the controller is not interpreted correctly. i played with installing via syn-pkg-mgr "xserver-xorg-input-joystick" and joystick, the controller seems to function o.k. as seen in FMS Calibrate, but it messes with the logitech trackball(i do not like mice).

I have seen some solutions regarding 3) above having to due with changing xorg files, but none seem to be fully functional, ie, mouse, keyboard and controller all acting as they should.  And, the changes seem to get a little complicated.

So, has anyone discovered partial or complete suggestions to deal with 1),3) above?

[edit 13 Dec 12]  o.k., please see following link, posts #26 and #34 and #36, for a solution that works to eliminate joystick interference with the mouse:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470)


mark

---

### Post by mark bower on 2012-12-13
bump.  again, how does open FMS simulator in WINE and not get a black screen?

---

