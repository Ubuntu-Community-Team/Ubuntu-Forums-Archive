---
title: "Wine Virtual Desktop Issue"
date: 2007-12-22
forum: Wine
---

### Post by tj111 on 2007-12-22
I have a 1680 x 1050 moniter, but because of my graphics card I usually run games at 1440x900 in wine.  I tried to set up a virtual desktop today so I could run CS:Source in a virtual desktop.  Steam loads up fine in a 1450x910 virtual desktop, but when counter strike loads, the virtual desktop resizes to what seems less then 800x600.  Anyone know what could cause this? (See the screenshots at these links)

[http://i16.tinypic.com/8dwppb4.png](http://i16.tinypic.com/8dwppb4.png)
[http://i5.tinypic.com/6krqxxt.png](http://i5.tinypic.com/6krqxxt.png)
[http://i12.tinypic.com/6wzbrkm.png](http://i12.tinypic.com/6wzbrkm.png)

---

### Post by cogadh on 2007-12-23
There are only two ways I can think of that would make that happen:[list=1]
[*]You have the game set to a lower resolution in the game settings.
[*]You have turned of the shader support in Wine, which will make the game default to DX 6 mode, which will drop the resolution down.
[/list]

---

### Post by tj111 on 2007-12-26
> **cogadh said:**
> There are only two ways I can think of that would make that happen:[list=1]
[*]You have the game set to a lower resolution in the game settings.
[*]You have turned of the shader support in Wine, which will make the game default to DX 6 mode, which will drop the resolution down.
[/list]

Hmm.  I know the games are set to 1440x900 in the settings, because when I turn off the virtual desktop they run at that resolution.  I'll have to double check and make sure shader support is enabled.

---

### Post by markharding557 on 2007-12-27
i

---

### Post by hikaricore on 2007-12-27
> **markharding557 said:**
> i would advise not using the virtual desktop it's more bother than it's worth

If used properly virtual wine desktops are the only way some games/programs will run in a usable fashion.  Please keep the broad and opinionated advice to a minimum.

---

### Post by markharding557 on 2007-12-28
i just quit giving advice in the wine section since you obviously have vastly superior knowledge to me.
i will therefore leave all that to you

---

### Post by ChiaGod on 2008-01-11
Seems we had a shared issue.  I'm running a triple head display (two nVidia GeForce 8600's) and this is what I did to get Steam games (HL2, Portal) to run at full resolution (3840x1024):

1.  Set the wine desktop at the appropriate resolution
a) Launch winecfg from a console or wherever
b) Under virtual desktop set it to the desired size:  (3840x1024 in my case)

2.  Configure the game to launch fullscreen with the exact same resolution
a)  Launch the steam game with the following command (this is the example for HL2):  wine "C:\Program Files\Steam\steam.exe" -applaunch 220  -novid -dxlevel 80 -width 3840 height 1024

3. Success!


I can also run World of Warcraft (requires setting the resolution manually in the Config.wtf file found in your WoW directory under the WTF folder).   One caveat, if the game tries to launch full screen in a virtual desktop a different size than the fullscreen setting it has it will go to 800x600 in my experience.  Hope this helps!

Now if I can launch vent and WoW and not have WoW cover vent the whole time (have WoW in a virtual desktop, Vent launched normally) I'd be set!

---

### Post by tj111 on 2008-01-11
Awsome advice.  I will try this out when I get home.  thanks

---

