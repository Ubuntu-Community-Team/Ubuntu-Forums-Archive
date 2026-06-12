---
title: "WoW wine problem."
date: 2008-06-20
forum: Wine
---

### Post by Razzlesnaff on 2008-06-20
I'm having problems with the World of Warcraft graphics. As in that they aren't they're. I run WoW, and all I get is some lighting detail and names. I can click on quest givers and see those graphics, but sadly no characters or environmental detail. Also while World of Warcraft was running it kept flickering back and forth between the desktop and WoW.

It looks like this.

[http://img.photobucket.com/albums/v719/ssjdaisuke/Screenshot.png](http://img.photobucket.com/albums/v719/ssjdaisuke/Screenshot.png)


Anyone have any insight to this problem?

---

### Post by werries on 2008-06-20
follow [this guide]("https://help.ubuntu.com/community/WorldofWarcraft") and make sure you add all the options it says. you can skip past the installation bit since im assuming you installed it. go right to configuration
edit: also you could have it not allow the window manager to control WoW, in winecfg. and allow directx apps to stop the mouse leaving their window.

and your graphics settings may be too high. if you can get into WoW, hit esc for the main menu, then go to video settigns and turn em down.

---

### Post by Razzlesnaff on 2008-06-20
Thank you so much! That solved all of my problem except for the flickering.

---

### Post by werries on 2008-06-20
what kind of flickering? like the desktop is showing up?

what background programs are you running?

---

### Post by Razzlesnaff on 2008-06-21
Exactly what you described. I have nothing else running in the backround. 

Not only that but WoW crashed after I was playing with the video settings and I can't seem to get it to work again.

---

### Post by werries on 2008-06-21
to reset the settings for the video, delete the wtf folder in the WoW folder, and then start up wow and logon, and then you will have to do the guide changes to the config.wtf file again.

edit: just to clarify, WoW makes the wtf folder again at login, its a configuration settings place.
edit2: wtf stands for Warcraft Text File, by the way.

---

