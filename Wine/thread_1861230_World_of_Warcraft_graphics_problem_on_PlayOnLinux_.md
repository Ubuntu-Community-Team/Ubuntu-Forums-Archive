---
title: "World of Warcraft graphics problem on PlayOnLinux - Oneiric 11.10"
date: 2011-10-15
forum: Wine
---

### Post by Davh on 2011-10-15
Hello!
I have an HP 430 and ```
lshw -c video
``` command line said:

 ```
*-display               
   description: VGA compatible controller
   product: 2nd Generation Core Processor Family Integrated Graphics Controller
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 09
   width: 64 bits
   clock: 33MHz
   capabilities: vga_controller bus_master cap_list rom
   configuration: driver=i915 latency=0
   resources: irq:42 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

I'm running this at Ubuntu Oneiric Ocelot 11.10 and PlayOnLinux 4.0.12.

-[When I'm logging in the graphic
s are perfect]

There's an image that could be helper.

[IMG]http://i55.tinypic.com/2ur2zk0.png[/IMG]

---

### Post by Langney on 2011-10-15
I havent had that problem myself but mines been the Framerates :/ Think It might be a Wine update or something. I really don't have any answer. Sorry mate. Just hope both our problems get sorted. I feel really dirty having to log into Windows :(

---

### Post by cwwilson721 on 2011-10-15
Having an Intel chip is...'problematic' at least.

Either it won't work at all, or you can try this post.

Sorry, but Intel + wine + Opengl = Bad Juju.

Good luck.
[http://ubuntuforums.org/showthread.php?t=1799781]("http://ubuntuforums.org/showthread.php?t=1799781")

---

### Post by Davh on 2011-10-15
I've solved this!

*First*. Install **mesa-utils** if no installed: ```
sudo apt-get install mesa-utils
```to test fot OpenGL support.

*Second*. Run a check to see if you have OpenGL support: ```
glxinfo|grep 'direct rendering'
``` or ```
/usr/lib/unix/unity_support_test -p
```.

*Third*. Run ```
glxgears
``` to see how your video card renders and its FPS for the render.

If it appears you have OpenGL support and all is good then add to the WoW launcher the **-opengl** parameter. For example ```
'.wine/drive_c/Program Files/World of Warcraft/Wow.exe' -openGL
```

Good luck!

IMPORTANT: If you get pixelated trees, you have to restart and Log In with Ubuntu-2d session. 

After doing all these instructions my problem is solved :P!

Greetings.

---

### Post by cwwilson721 on 2011-10-15
ALWAYS go with:
[LIST]
[*]2D (if using Unity), or No Effects (For Gnome)
[*]Use the -opengl switch
[/LIST]
No matter WHAT videocard/chip you use.

---

### Post by Langney on 2011-10-15
> **Davh said:**
> I've solved this!

*First*. Install **mesa-utils** if no installed: ```
sudo apt-get install mesa-utils
```to test fot OpenGL support.

*Second*. Run a check to see if you have OpenGL support: ```
glxinfo|grep 'direct rendering'
``` or ```
/usr/lib/unix/unity_support_test -p
```.

*Third*. Run ```
glxgears
``` to see how your video card renders and its FPS for the render.

If it appears you have OpenGL support and all is good then add to the WoW launcher the **-opengl** parameter. For example ```
'.wine/drive_c/Program Files/World of Warcraft/Wow.exe' -openGL
```

Good luck!

IMPORTANT: If you get pixelated trees, you have to restart and Log In with Ubuntu-2d session. 

After doing all these instructions my problem is solved :P!

Greetings.

My problem Is the openGL never saves into config.ini thus causing the Framerate Issue, everything I have tried however has broken the game so to speak. I'm on the 4th time downloading. Near on 100G downloaded so far :confused:

---

### Post by cwwilson721 on 2011-10-15
> **Langney said:**
> My problem Is the [COLOR="Red"]openGL[/COLOR] never saves into config.ini thus causing the Framerate Issue, everything I have tried however has broken the game so to speak. I'm on the 4th time downloading. Near on 100G downloaded so far :confused:

It is NOT 'openGL', it is '-opengl'

Ex:
```
env WINEPREFIX="/home/<USER>/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```

NOTE: <USER> is your username. This is assuming you installed WoW in the default wine location. The '-opengl' tag will run WoW in this mode, and WoW will insert the correct 'set gxAPI' option in World of Warcraft/WTF/Config.wtf (NOT config.ini). Also, I run 'Wow.exe' and not 'Launcher.exe' at this time, due to issues with Launcher.exe exiting and really launching WoW.

And there is NO need to delete the entire WoW install. I, for example, have the actual WoW install folder elsewhere, and just have a link to the actual folder in ~/.wine/drive_c/Program Files.

Ex:
```
/home/<USER>/.wine/drive_c/Program Files/<LINK TO REAL WOW FOLDER>
```

 That way, I can delete the .wine folder, and STILL have the HUGE WoW install intact. Then, I can just run 'winecfg', and make a new link to the WoW folder.

---

### Post by christopher.wortman on 2011-10-15
Edit the following file:
{wow directory}/wtf/config.wtf

add the line:
SET gxApi "opengl"

to the very top with gedit. save, exit, play game. I also play wow especially on Linux

Game on my friend!

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

also google before posting.

---

