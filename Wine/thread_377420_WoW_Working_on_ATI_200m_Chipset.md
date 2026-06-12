---
title: "WoW Working on ATI 200m Chipset"
date: 2007-03-06
forum: Wine
---

### Post by jamieplucinski on 2007-03-06
Well finally, after many attempts, I have WoW working through Wine on 6.10, which is nice. I am getting 20 to 50 fps inside buildings, 5 to 20 fps outside (in stormwind when empty of all players), and 4-9 fps in areas with large mobs and gadgets.

Not the most ideal fps I'll admit, but, at least it's not hanging my system.

The key to getting it working was, simply, loads of hard reboots and swearing, I kid you not. A lot of (excellent) posts detail how to install the FGLRX drivers from ATI, but they then go on to detail the installation of XGL, which may look pretty, but is completely evil when it comes to gaming, at least on the 200m.

Follow [this]("http://ubuntuforums.org/showthread.php?t=321766&highlight=200m") guide and follow it until you get to this part:
> And that should work!

Now, let's get XGL and Beryl working:

But we want to game, so don't touch XGL or Beryl, once you've reset you should install Wine, and WoW as per [this](https://help.ubuntu.com/community/WorldofWarcraft) guide.

Once that's done run winecfg again and click the Graphics tab, then select the box "Emulate a virtual desktop" and in the desktop size box enter the resolution you want to run WoW at, mine is set to 800x600 for now. Then in the Direct3D box set Vertex Shader Support to None, and deselect the Allow Pixel Shader box. Then click Ok.

You can always put some of the options above back to normal once everything is running, but these are the only options I could get decent performance out of on the 200M with WoW TBC and 1.12+

Next follow Toxicity999's tip (you can find [here](http://ubuntuforums.org/showthread.php?t=156841))
```
** SNIP **
try adding:
tmpfs /dev/shm tmpfs defaults 0 0
to /etc/fstab
** SNIP **
```

Now before you reboot, open your /etc/X11/xorg.conf by doing
```
sudo gedit /etc/X11/xorg.conf
``` from a terminal and add the following lines:
```
Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"
```
To the section that starts like this:
```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
```

Once that's done, reboot your computer, or if you rebooted after adding the entry to /etc/fstab just restart X by pressing CTRL+ALT+BACKSPACE at the same time.

Welcome back to Ubuntu :) Now drop into a terminal and copy and paste the following command:
```
aoss wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -d3d
```

Now if you're not sure what the above line does, here's a quick explanation. aoss lets the OSS sound system you selected back in the Wine Setup guide share your sound card with other applications, so you can use team speak, or play music in whilst playing WoW. Anything that uses OSS should be started with the aoss command in front of it to allow all OSS applications to share the soundcard.

Now a lot of guides will tell you to use -opengl at the end of WoW.exe for better frame rates, but with the 200m running with -opengl just ends up with slow frame rates, corrupted graphics, and hangs. At least on the 200m chipset on the Compaq R4225 or similar models, of which there are many. Instead use -d3d it lets you set options without extra addons and makes the game much more playable.

Once that's done you should start WoW and login to your character, then logout again. Once you've done this a file called Config.wtf will be created in the WTF subdirectory of where you installed WoW, if it hasn't happened already. This is when you add the following lines:
```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
```

And yes, I realize I said to use d3d, but the code above has OpenGL in it, you can change it if you want, but the command-line switch of -d3d overrides it anyway.

Then start the game again and go into the graphics options and set everything to low, or whatever floats your boat. Mine is set to low, and looks fine, plus with the relatively low frame rates in populated areas, the extra quality if just going to slow you down a lot.

Remember to start WoW every time with the following command:
```
aoss wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -d3d
```

You may get better results with the instructions contained in the plethora of posts on this topic, but these are the only instructions I have found that actually work on the Compaq 4xxx laptop models that use the 200m chipset.

A mini-spec is below for reference:
ATI Athlon 3500+ (2.2GHz), 1GB RAM, 100GB HDD, 200M chipset (128MB Sideport).

---

### Post by jamieplucinski on 2007-03-06
Before editing any of your files you may want to make a backup of them by dropping in a terminal and doing the following command:
```
mv /path/to/my/file.ext /path/to/my/file.ext_backup
```

---

### Post by jbaerbock on 2007-11-17
Well this is the best post I have seen yet. I did what you said and the FPS is brilliant indoors or inside shops. However I was in Booty Bay and anytime i was outside it was terrible FPS. Any other posts you have found regarding this?

---

### Post by jbaerbock on 2007-11-17
Ok like it says above got it working except bad FPS in busy areas, not wonderful FPS in empty areas either but playable. 

Question 1: How do I get it to show the FPS ingame so as to figure out that it is?

Question 2: In the terminal it spits out the following code during game play over and over:
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198

Question 3: After about 5 minutes of play it simply freezes, any ideas?

---

### Post by jbaerbock on 2007-11-17
After it crashed now the FPS has gone to hell again too, down to maybe 2fps

---

