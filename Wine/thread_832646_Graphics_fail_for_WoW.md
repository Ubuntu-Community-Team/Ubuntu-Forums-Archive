---
title: "Graphics fail for WoW"
date: 2008-06-17
forum: Wine
---

### Post by Crusnik309 on 2008-06-17
I'm a newbie Linux user.  I just got it about a week ago and haven't really done anything intense so far.  I've just customized it a bit and use the programs readily available.
Well, the summer has come and I have spare time and I would like to start playing World of Warcraft again but I have an annoying issue that happens every time I log in.

When I open up WoW, rather than the normal login screen, I have three shades.  Black, red, and a lighter shade of red, but all the buttons and login boxes are fine.  The character selection screen background is black, but there is still the WoW emblem in the top right corner and the character list is visible, along with all the buttons.  Once loading the the character all I see is grey and the background color of the sky, but there are definite objects.  All objects are grey and the only way to see them is to have you screen where the sky is behind them to show you the outline of them.

I'm pretty sure my graphics card is not the issue, I've run WoW on the windows just fine.  Now, on Ubuntu, after installing both WoW and the Burning Crusades, it was just fine, I logged in and went to the character selection screen with the graphics just fine, it's when it wanted me to download the patches, and afterwards that I've encountered this problem.  Anyone have an idea?

If it matters, my graphics card is the regular Mobile Intel(R) 965 Express, I have 2GB of ram, Intel Centrino Duo...

Sorry for the looong post, but this has been frustrating and I've been trying to figure it for days.

Thanks.

---

### Post by Crusnik309 on 2008-06-18
This is what I'm seeing...
[http://img93.imageshack.us/img93/974/loginwo6.png]("http://img93.imageshack.us/img93/974/loginwo6.png")
[http://img140.imageshack.us/img140/6219/characterqy6.png]("http://img140.imageshack.us/img140/6219/characterqy6.png")
[http://img209.imageshack.us/img209/4007/ingamedu4.png]("http://img209.imageshack.us/img209/4007/ingamedu4.png")
In this last one, I actually see the ground!  I don't know why it changed, but sometimes I see a regular sky for the time of day, sometimes it's just a grey clouded sky, and once in a while this happens.  This in-game part is the only thing that changes from time to time.

---

### Post by Cup of Squirrels on 2008-06-18
Have you set your graphics mode in WoW to opengl?

If not, open config.wtf and add the line:

```
SET gxApi "opengl"

```


Good luck!

---

### Post by Crusnik309 on 2008-06-18
Yep I've done that.

---

### Post by Roryking on 2008-06-18
Try this:

1. Open your Config.wtf file
cd ~./wine/Program\ Files/World\ of\ Warcraft/WTF
gedit Config.wtf

2. Add this line:
SET M2UseShaders "0"

3. Save and close, and start WoW.

I added this line to mine, and it fixed a similiar issue to what you had. I have an ATI x1300 card.

---

### Post by thisismalhotra on 2008-06-19
Follow these links please;

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by Crusnik309 on 2008-06-19
Thank you, it's better now, but I still have issues with the action bar icons and water.  I can actually see my character and see most scenery now. :D

Another thing that doesn't work is my map, and when I go invisible, my screen turns a solid cyan color.

EDIT: Ah, the ground in many places is glitched.

---

### Post by cachcoco on 2009-07-11
Hi, I've been a bit successful with getting WoW to run with Ubuntu Jaunty. I installed Wine, Microsoft Core Fonts (so you can push the accept button), and then I used the cd's to start the dl's from the disks. 

Something that i've found interesting was that the battlechest dvd and the wotlk dvd didn't work for me. I had to bust out the old disks from vanilla and bc and then download wrath from account management.  

Playing was no issue as far as graphics go for me. My only real issue was that the graphics were too low. but i'm installing an addon from wowinterface called Applytoforehead ([http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)) and that is supposed to allow me to adjust the graphics in game. 

Another site I found helpful was [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft).

Be well!

---

