---
title: "[SOLVED] World of Warcraft and Wine.... Doesn't Work Well"
date: 2008-06-20
forum: Wine
---

### Post by JustinAlf on 2008-06-20
I have not Windows in more then 2 1/2 years.  I had to install it yesterday , Vista of all things, in order to play World of Warcraft.  Everything runs ok, but I have no ground.  The ground appears like a sea through area, and then it freezes when loading and ending the game.  

I know it's not a graphics card because it works in Vista.  I'm running OPenGL and followed a guide, but WINE says that this game runs perfectly under Ubuntu with some configuration.  IF anyone could help me, I would really appreciate it, cause I hate Windows, but this game is fun.

---

### Post by myromance123 on 2008-06-20
I feel your pain man :) 
   Hopefully someone with experience will help you out soon enough, stay tuned and dont give up~  :D

---

### Post by DoktorSeven on 2008-06-21
Regardless of whether it works in Windows, many video cards aren't as well supported in Linux to play the more complex games.  Generally, you need an nvidia card (ideally) or a good ATi 3d card, though the ATis have reported various problems here and there due to its drivers.

So what video card do you use, since yes, it might be the problem?  I use an older nvidia card and have zero issues with running WoW.

---

### Post by dur on 2008-06-21
Try running in DirectX mode. Remove the opengl line from your config.wtf and restart wow. That was the same problem I was having.

---

### Post by JustinAlf on 2008-06-23
I'm running a Dell 1525 Laptop, with a Intel Graphics Media Accelerator X3100.  WOW on Windows is amazing, but on linux. it sucks.  I don't have any problem with other OPengl games on linux like Glest and Wesnoth and Nevernall, But it does not like WOW.  Logging in is fine, and it's fine up to when i actually get into the world.  Sometimes it goes in and I have no ground, other times it freezes and I have to restart.  Any suggestions?  I hate windows!

---

### Post by Takatalvi on 2008-06-23
The problem is with the new Graphic Drivers. I'm still trying to find out exactly what the problem is.

It works(at least for me) in OpenGL mode _IF_ nvidia-settings don't force AA/AF

If you use AA or AF it doesn't get past the Launcher.exe, OR it freezes when you log in.

Any help would be great, I've tried every nVidia Driver I could find. They all fail as of the recent Kernal/Graphic Driver update.

---

### Post by hikaricore on 2008-06-23
Intel drivers and hardware are crap without DirectX.

Known issue.

Had you searched the forums you'd likely have found hundreds of posts just like yours dealing with using crappy intel chipsets on Linux.

---

### Post by thisismalhotra on 2008-06-24
I know there are issues with intel drivers and wow but I would start with this page and the troubleshooting part in the end

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by JustinAlf on 2008-06-25
I"m going to re-install tonight and try it without Open-GL and run with Direct X.  I"ll post if I can get it to work like this.

---

### Post by JustinAlf on 2008-06-27
Well, that didnt' work.  I'm wondering if anyone tries this game through VMware, and if it's dreadfully slow.  Anyone?

---

### Post by Takatalvi on 2008-07-10
I kinda feel stupid. But I did a 'winecfg', and under the graphic tab I checked "Allow Pixel Shader(if supported by hardware)", and WoW works as it did b4. Simply Flawless.

Apparently the new version of wine unchecked the box by default. I don't know why.

Hope this is the same fix for everyone else here.

---

### Post by Shaythong on 2008-07-10
That's unusal. Last time I checked my winecfg (WINE 1.1.0) on a new install of Ubuntu Hardy it said it *was* checked.

---

### Post by thisismalhotra on 2008-07-10
VMware does not have a 3d graphics support yet, or Stable support yet, it is experimental.

---

### Post by JustinAlf on 2008-07-11
OK I have WOW running smoothly on OPENGL, but I still have a problem.  When in the playing field, it looks like this:

Elywin Forest : [IMG]http://lh5.ggpht.com/Justinalf/SHfCCdzkrWI/AAAAAAAAABA/s3nV6I8oEJs/ElwinForest.png?imgmax=576[/IMG]

But When I"m in a city, it looks like this:

Stormwind City: [IMG]http://lh5.ggpht.com/Justinalf/SHfCCjrzCZI/AAAAAAAAABI/RMrxhNaIVlQ/Stormwind.png?imgmax=576[/IMG]

Why does a city look differnt?  Is there any way to hack OPenGL to get this working!   

Thanks.

---

### Post by JustinAlf on 2008-07-14
Bump

---

### Post by thisismalhotra on 2008-07-15
This definitely is drivers, look up on wine website and see if anyone else has this issue.

---

### Post by JustinAlf on 2008-07-16
Finally have it working!!!

I did everything off of the offical Ubuntu guide to WOW found: [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

It only worked slightly this way, without following the guide, the game was blackend.  I then got fed up and changed this line:

SET gxApi "opengl"

to 

SET gxApi "direct3d"

To my amazement, it worked!  I removed a lot of code from the config file, but it now works, not graphics problems at all.  Thank you all for all of your help!

---

### Post by Takatalvi on 2008-07-17
In my opinion thats not a good fix. Natively OpenGL runs smoother in Linux. Make sure you do the registry tweak though. I usually get about 20-60 MORE fps with OpenGL.

---

### Post by JustinAlf on 2008-07-28
It simply won't work with Open GL.  This does cause a slight probelem with the FPS.

---

