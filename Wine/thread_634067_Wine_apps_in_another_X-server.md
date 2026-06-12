---
title: "Wine apps in another X-server"
date: 2007-12-07
forum: Wine
---

### Post by KhaaL on 2007-12-07
I'm trying to get better performance by graphic intense games by running them in another Xserver, but I don't know how. Usually I run games in Xserver :1.0  by typing:
sudo xinit /usr/bin/dolphin $* -- :1.0  

According to [linuX-gamers]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+extra+XServer") you need to regedit and insert this value
[HKEY_CURRENT_USERSoftwareWineAppDefaultstest.exeX11 Driver]
"Display"=":1.0"

in order to run apps in other Xserver, but that dosen't work.  Yes, I obviously changed text.exe to the name of the app I wanted to run :P


If anyone can shed light on this I'd be grateful.

---

### Post by cogadh on 2007-12-07
Just use a launch script to launch the game in a seperate X server, instead of the Wine registry hack:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "~/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"
```
However, in order for this to work, you will need to modify the /etc/X11/Xwrapper.config file to allow non-root users to launch the X server. Change the line &#8220;allowed_users=console&#8221; to &#8220;allowed_users=anybody&#8221;.

---

### Post by KhaaL on 2007-12-07
Ah, this worked very well, thanks! 

While we're on the topic, do you know how I can do the same thing, but from the menu?

I have this command:
kdesu "xinit /home/khaal/no-backup/apps/etqw/etqw.x86 :1.0"

But I guess I put the quotation marks wrong, because i get the error:

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

---

### Post by cogadh on 2007-12-07
Well, I honestly don't know why that didn't work, I only use scripts similar to the one I posted for any app that I launch in a separate X server (native or Wine), I just change the launch line to reflect the correct binary. If you use a script and want to use the menu to launch it, just modify the menu shortcut to point to the script instead of the normal binary.

---

### Post by Enverex on 2007-12-07
I highly doubt you will gain any performance from this, the only reason it's normally done is to avoid messing up your current X server in the case of testing. You'll likely get worse performance (if anything) due to more RAM being used on a second X server.

---

### Post by cogadh on 2007-12-07
Actually, the performance improvement can be enormous, especially with games run through Wine. Since the normal desktop is not being rendered or used, most of the resources that are dedicated to that get freed up (not all of course, some are stil retained to maintain it for when you go back to it). You can get an even bigger performance increase if you use a script to launch the game from a console session with the normal X session disabled.

---

### Post by KhaaL on 2007-12-07
I have also noticed a enormous performance increase with having another Xserver. Since I have 2 Gb RAM, I'm not worried about RAM usage. Those extra FPS can be worth it :D

Once I find a more proper method of benchmark that's better than running glxgears, I'll make a performace test.

---

### Post by phoogkamer on 2008-07-30
I am running Grand Prix Legends on an Ubuntu 8.04 desktop with wine 0.9.59. I am trying to run wine with the script mentioned in the begining of this post, but get an error regarding nvidia-settings. The errors states:

Error: The control display is undefined

Could somebody help me?

---

### Post by phoogkamer on 2008-08-04
I have figured this out. It had something to do with the value of the $DISPLAY variable. I can start Grand Prix Legends in a different X server.

Peter

---

### Post by serialbox on 2008-08-07
> **cogadh said:**
> Just use a launch script to launch the game in a seperate X server, instead of the Wine registry hack:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "~/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"
```
However, in order for this to work, you will need to modify the /etc/X11/Xwrapper.config file to allow non-root users to launch the X server. Change the line “allowed_users=console” to “allowed_users=anybody”.

Hey.. first thanks for all the help and tips.  this was a mission to get wow to even run and display graphics properly in wine.  

I am trying to use this script in order to play world of warcraft using wine.  Just playing it with wine by itself has a framerate of 2.  I have successfully installed WOW and made the necessary regedits and changes to Config.wtf .

The game loads fine using just wine and the graphics look alright as does the resolution but my FPS is only 2 so the game is at a crawling speed.

When I try to use this script.. my screen goes black for a minute then switches to this weird looking screen with lines all over it and just hangs there.  I have to CTRL-ALT-BKSPC to get back to my terminal and this is the error I get:

```

(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found

(II) Module "ddc" already built-in
(II) Module "i2c" already built-in


(II) Module "ramdac" already built-in
(EE) [drm] Could not set DRM device bus ID.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.


expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc

Atom 4, CARD32 4, unsigned long 4


Synaptics Touchpad no synaptics event device found (checked 19 nodes)

Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.

(EE) PreInit failed for input device "Synaptics Touchpad"


expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc


FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
dan@dan-laptop:~/Desktop$ 


```

Im using the latest version of wine installed from the repos and Ubuntu 8.04 .  Its running on my laptop which is an intel core2 duo 1G of ram and onboard video card.

any help would be appreciated.  when I formatted my laptop to get rid of windows and install linux I completely forgot about wow!

---

### Post by DaVince21 on 2008-11-09
The topic is a bit old, sorry for that, but I still have a question about this. How can I get above script to run any app I feed it? For example, if I name the script "xwine" and put it in /usr/bin, how do I have to modify it to run applications like Wine does?

Example:
```
xwine local-app-name.exe
```

---

### Post by magcius on 2008-11-09
```

#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "$*"

```

Launch like so:

```

$ xwine ~/.wine/drive_c/Program Files/path to/game.exe

```

EDIT: I'm having trouble getting sound to work now. I'm not sure how to start PulseAudio and have it redirected to both terminals.

---

### Post by DaVince21 on 2008-11-09
Thanks man, this will come in really handy!

By the way, the WineHQ forums have some information on [Wine and PulseAudio](http://forum.winehq.org/viewtopic.php?t=1457). Might want to check it out.

---

### Post by Ferrat on 2008-11-18
I'm having a problem, I have to use sudo to create the new X and that makes the new X root based and locks my home folder from being used (since I'm not owner then?)

I can launch programs once the X is started if I do it from a session ruled by me and export it but making a script for that isn't easy, specially if I want to kill everything else, anyone know what I must change to have the rights to create a new X?

Edit, Also now and again I get 
```

X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  637
  Current serial number in output stream:  637
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf79557c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf795596e]
#2 /usr/lib32/libX11.so.6 [0xf7b6b619]
#3 /usr/lib32/libGL.so.1 [0xf7a98345]
#4 [0xf6ba9b48]
#5 [0xf6ba9b48]
#6 [0xf6ba9b48]
#7 [0xf6ba9b48]
#8 [0xf6ba9b48]
#9 [0xf6ba9b48]
#10 [0xf6ba9b48]
#11 [0xf6ba9b48]
#12 [0xf6ba9b48]
#13 [0xf6ba9b48]
#14 [0xf6ba9b48]
#15 [0xf6ba9b48]
#16 [0xf6ba9b48]
#17 [0xf6ba9b48]
#18 [0xf6ba9b48]
#19 [0xf6ba9b48]

```

just sometimes, not always and I have been able to play on a new X server for hours so I can't really figure it out, tried purging all GL libs and reinstalling them but same thing happens

EDIT2:

when I do 
DISPLAY=:1 glxinfo 

I get no errors just the same old attack of GLX stuff as I should get,

---

### Post by cogadh on 2008-11-19
To give yourself permission to launch the new X session, you need to modify the /etc/X11/Xwrapper.config file. Change the line &#8220;allowed_users=console&#8221; to &#8220;allowed_users=anybody&#8221; and you won't have that problem anymore.

I'm not sure about those GLX errors you are getting, I'll leave that question for someone else.

---

