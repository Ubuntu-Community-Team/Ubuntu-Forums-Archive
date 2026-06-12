---
title: "Obviously, ATI blew it again, Wine+TF2 seem to proof that"
date: 2008-09-07
forum: Wine
---

### Post by perixx on 2008-09-07
Hello and welcome to the ATI-hell...


I've been trying to run Steam/Team Fortress 2 under Wine for about 2 days now. Tried various tutorials and tips from the Wine forum and whatnot to get it working. Also, I installed Playonlinux and gave it a shot with different Wine-versions (9.56 / 1.0 / 1.1.3). I played around with many different registry settings-variations and TF2-starting options as well, of course (rendering, dxlevel, shaders, windowed mode...). 
I dared to skip the intro video, which played, but didn't turn out to be relevant to further functionality.

The outcome was interesting: using newer ATI Catalyst drivers [8-6 and 8-8] would ALWAYS result in a totally distorted desktop upon launching TF2 on the Steam 'Games' panel - regardless of any other settings. So it's very obvious, that ATI broke something a little more from the driver version 8-3 on...

The 'best' results I managed to get, were with Catalyst 8-3 + dxlevel 70 + pixelshader + window-mode enabled:

the TF2-startup-screen picture (showing the Doc and characters) would show up for a second (in a Window) - then crash with the message 'hardware must at least support pixelshader 1.1'.

With dxlevel 81 or 90 + pixelshader enabled, I would even be able to get into the startup menu - hidden, on a black screen. Disabling pixelshader wouldn't show anything at all and result in an immediate crash when launching TF2. 

I dunno, if ATI or Steam is to blame - supposedly, the latter - but I do get 'no permission to run tf' as well. From what I remember, on the higher Catalyst versions (where you barely can make out the message due to crippled graphics) and also on 8-3 on some occasions. Perhaps Steam is involved in the dysfunction of TF2, too. 

Somebody in the forums wrote, that Wine uses OpenGL 2.0 calls on several occasions, thus the graphics driver needs to implement those. On ATI's wiki page, I've learded, that they're using some OpenGL-'slang'(?) called ARB and that they don't implement the standard OpenGL 2.0 language and not even all of the ARB-standard... 

Heck, I guess I'm beginning to understand why my ATI card (X1950GT) fails upon nearly everything related to sophisticated OpenGL functionality 

@_0¬

Not only that they apparently lack of having the manpower and resources to improve their drivers in terms of functionality and performance in a decent manner of time - they don't even seem to be able to provide reliable functionality... even the bug of an OS-crash on shutting down Ubuntu after playing UT2004 was re-introduced with Catalyst 8-8, from what I see.

:P   

I'm starting to get tired of this crap...


perixx

---

### Post by AceOnline on 2008-09-08
After intensive installation and re-installation of Linux & different versions of ATi drivers. I have concluded that the Issue is probably lying with the graphics drivers and it's compatibility with Wine. 
I do not have a Nvidia card or I would have loved to give the card a test and see how would have things gone with Wine+Nvidia!

Right now I'm on the latest ATi Drivers dated as of 20th August 2008 with Wine 1.1.3 which apparently has a gold rating from most users since it is running the game(Team Fortress 2 in Steam) well for them.

Everytime I run the game up, the screen gets messy, It's like some of the game is on the left side of the screen and some of it on the right side, and I can make out the desktop compressed to an inch wide size right smack in the middle of the monitor and the two game parts on different sides. The whole screen is awfully pixelated! I'll Try to take a picture with my bro's mobile and Attach it here soon, hopefully!

I'm with you on this one mate! ATi has messed up or It's Wine that's not up for the job!

---

### Post by perixx on 2008-09-08
Hi AceOnline!

"I do not have a Nvidia card or I would have loved to give the card a test and see how would have things gone with Wine+Nvidia!"

I replaced my card with an old gto6800(?) - can't quite remember - back when using Gutsy, for testing purposes... the result was, I messed up the OS so badly due to broken Symlinks and xserver-xorg(?) and whatnot packages, that it took me over 2 whole days, to get the Ati driver back working again! 

And it wasn't even worth the effort, the game (UT2004) ran even worse. Granted, my x1950gt is quite a bit better, and so are the amdcccle - tools, I'd favour them instead of Nvidia's settings tool. 
To be honest, UT2004 works really good now (didn't check Fraps yet), as did Doom3 (bought it just for testing my card :]) back when I still used Feisty - haven't installed it since. Sometimes I'm not quite sure whether Ati's to blame for the inferior performance, most especially when online-gaming - or UT's or Ubuntu's networking modules.

But still - the OpenGL implementation of Ati keeps returning frustrating results. Not to speak of the overall performance: 50-75% of XP-drivers at best - on low quality settings, with native Linux games! 
Can't tell of any newer games as well.


"It's like some of the game is on the left side of the screen and some of it on the right side, and I can make out the desktop compressed to an inch wide size right smack in the middle of the monitor and the two game parts on different sides. The whole screen is awfully pixelated! I'll"

ROFL - exactly what I've experienced! What's your card's type?
Really, you should take the trouble and go over to Ati's Linux driver feedback page and post your results there (already did it). And on the Wine homepage. If everybody would place his moans on the right place, that could make the difference :)

perixx

---

### Post by bpl07 on 2008-09-08
Try 8-5, supposedly it was the best one before the recent changes that first occurred in 8-6.  Wine doesn't like anything above 8-5 right now.

---

### Post by AceOnline on 2008-09-08
> **bpl07 said:**
> Try 8-5, supposedly it was the best one before the recent changes that first occurred in 8-6.  Wine doesn't like anything above 8-5 right now.

Already gave that a shot! It blew up in my face!


And I own a X1950XT card. I miss XP and my gaming! I don't want to have windows Installed as well as Linux on my pc! I want to stick with one OS!

I'll head on over to ATi's website and let them have it! =S

---

### Post by blaise69 on 2008-09-09
I also get the split screen problem, it's like a checkerboard with 50% of the squares on the left half of my screen and the other 50% on the right, I haven't actually managed to get TF 2 downloaded yet, but this happens without fail everytime I open the pop up for a game in Steam to install it, so we're still talking about being in the Steam app.

Frustrating as I used to have TF 2 up and running (and Steam) on earlier drivers.

I also have an ATi card with the latest drivers.

---

### Post by perixx on 2008-09-09
Blaise69, what card do you own exactly? 
And with which Wine, respectively Catalyst version did you get it to work?
It's very likely that only certain Wine versions will work (at least: had worked) with TF2; I've read about version 1.01 or so and 9.56 doing a good job, but that was quite some time ago - Valve has changed since then, too.

I'll try to talk a friend into lending me his 8800 from Nvidia...
Though I'm bound to run into trouble, I really want to know it now..! When I had time and some results at hand, I'll report back.

perixx

---

### Post by ObiWan2001 on 2008-09-10
There is the trick to replace the libGL.so.* from the ATI drivers with the ones from mesa.
That resolves most of the bugs with ATI and wine on drivers >=8.6.

Don't ask me for an Howto as im running gentoo on my desktop pc, wich has an special command for switching the opengl drivers.


PS:
Even with the mesa libGL, hardware acceleration is active, but AIGLX doesn't work anymore.

---

### Post by perixx on 2008-09-10
> **ObiWan2001 said:**
> There is the trick to replace the libGL.so.* from the ATI drivers with the ones from mesa.
That resolves most of the bugs with ATI and wine on drivers >=8.6.

PS:
Even with the mesa libGL, hardware acceleration is active, but AIGLX doesn't work anymore.

Are you sure about that? Isn't libGL main part of the 3D-rendering functionality? I can't believe that direct rendering wouldn't suffer from such a measure, even if it worked... 

perixx

---

### Post by ObiWan2001 on 2008-09-13
No as long as the fglrx_dri.so exists direct rendering is activ, only a few ati-specific things wont work.

If you used the ATI-binary installer:
```

sudo mv /usr/lib/xorg/libGL.so.1.2 /usr/lib/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib/FGL.renamed.libGL.so.1.2 /usr/lib/xorg/libGL.so.1.2

```

with 64bit:
```

sudo mv /usr/lib64/xorg/libGL.so.1.2 /usr/lib64/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib64/FGL.renamed.libGL.so.1.2 /usr/lib64/xorg/libGL.so.1.2
sudo mv /usr/lib32/xorg/libGL.so.1.2 /usr/lib32/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib32/FGL.renamed.libGL.so.1.2 /usr/lib32/xorg/libGL.so.1.2

```

As alternative you can use the libGL.so from the 8.5 driver:
Download the 8.5 driver from AMD
```

sh ati-driver-installer-8-5-x86.x86_64.run --extract tmp
```
32bit:
```

sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib/xorg/libGL.so.1.2

```
64bit:
```

sudo cp tmp/arch/x86_64/usr/X11R6/lib64/libGL.so.1.2 /usr/lib64/xorg/libGL.so.1.2
sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib32/xorg/libGL.so.1.2

```

---

### Post by perixx on 2008-09-13
Oh, wow... I've got to try this!

Thanks,

perixx

---

### Post by perixx on 2008-09-13
Hi again!


Before doing anything, I backed up the files in question, as suggested in option 1:

> sudo mv /usr/lib64/xorg/libGL.so.1.2 /usr/lib64/xorg/fglrx_org_libGL.so.1.2
sudo mv /usr/lib32/xorg/libGL.so.1.2 /usr/lib32/xorg/fglrx_org_libGL.so.1.2


Additionally, I replaced "/usr/lib32/xorg/libGL.so.1.2": 

> sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib/xorg/libGL.so.1.2


As the suggested file "/usr/lib32/FGL.renamed.libGL.so.1.2" for some reason didn't contain anything, I chose to follow your second proposal, extracting from the driver version 8.5:

> sudo cp tmp/arch/x86_64/usr/X11R6/lib64/libGL.so.1.2 /usr/lib64/xorg/libGL.so.1.2
sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib32/xorg/libGL.so.1.2

Content of "/usr/lib32/xorg/libGL.so.1.2" should - since I'm using an 64-bit version of Xubuntu - be identical to the file at location "/usr/lib64/xorg/libGL.so.1.2", from what I see. I replaced that one accordingly...


Now, for some unknown reason, I can't connect to Steam anymore. Can't remember having messed around with my network settings, though :(
Either Steam has denied permission for me to log in (due to high count of logins) or something blew during Ati driver un-/installations...


perixx

---

### Post by aoanla on 2008-09-13
> 
Now, for some unknown reason, I can't connect to Steam anymore. Can't remember having messed around with my network settings, though :(
Either Steam has denied permission for me to log in (due to high count of logins) or something blew during Ati driver un-/installations...


perixx

Neither happened - this is unrelated to your messing around.
Delete the ClientRegistry.blob in the Steam installation directory, and things should work again.

---

### Post by perixx on 2008-09-13
Thanks for the hint, aoanla!

Steam starts again, but when trying to start TF2 from the menu, Wine insta-crashes now. Either the disengaging the libGL_12.so files has broken the direct rendering or something must've gone awry during the last re-installation of Catalyst 8.8...

I removed it with Envy first, then tried to make installer-packets with the v.8-8 Ati driver but I got error messages about some files not being in the right place - should have made a note on that. Then I just installed via the Ati installer, which maybe was not a good idea...

arr...

perixx

---

### Post by perixx on 2008-09-13
No luck.

I've installed Catalyst 8.8 again (successfully), but though I've replaced the libGL.1.2.so files with those from package v.8.5, I get the messed-up graphics again, when trying to launch TF2 via the Steam menu - which loads perfectly first :(

perixx

---

### Post by ObiWan2001 on 2008-09-13
> **perixx said:**
> 
As the suggested file "/usr/lib32/FGL.renamed.libGL.so.1.2" for some reason didn't contain anything, I chose to follow your second proposal, extracting from the driver version 8.5:

FGL.renamed.libGL.so.1.2 should be the original libGL.so.1.2 from the libgl1-mesa-glx package reinstall it and the libGL.so.1.2 should be the one from mesa again.

/usr/lib32/libGL.so.1.2 is part of the ia32-libs package.

---

### Post by nwlinkvxd on 2008-09-14
I highly recommend using the fglrx 8.5 drivers, without doing all the libGL swapping. The reason steam was crashing is probably due to one of your registry keys in Wine.

First, uninstall your existing fglrx drivers completely, and restart your computer.

Follow this guide ([http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29")) replacing 8-8 with 8-5.

Restart the computer, and once you're back, do ```
wine regedit
``` and follow [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys") to create the HKEY_CURRENT_USER\\Software\\Wine\\Direct3D string values OffscreenRenderingMode = "fbo", and UseGLSL = "enabled". Using those settings gets Portal to work on my machine, so I can't imagine TF2 would play any worse. Unfortunately, when I want to play Spore, I have to switch OffscreenRenderingMode back to "backbuffer".


By the way, I have an X1900XT, so we're running virtually the same hardware.

---

### Post by perixx on 2008-09-14
> **nwlinkvxd said:**
> I highly recommend using the fglrx 8.5 drivers, without doing all the libGL swapping. The reason steam was crashing is probably due to one of your registry keys in Wine.
Hmm... maybe I'll give it another shot, though I'm pretty sure I've tried it before - well, at least 8.3 and 8.6...
As for the registry keys:
> OffscreenRenderingMode = "fbo" / "backbuffer", and UseGLSL = "enabled" I tried nearly every possible combination of keys with those drivers above, so I'm not quite conviced that will work out.

I guess trying an Nvidia 8800 GTO is more promising than this crappy piece of hardware I have here - well, perhaps it's more the crappy piece of (driver) software - it just won't work.

Besides, the X1950GT is based on a modified chip (r570 or so?), different from the full-featured card of yours. Also, it was a problem from the beginning on, to get new drivers for my card: Ati needed about 3 months to provide new drivers from the date of purchase on and Palit (vendor) even longer! Interesting: they had drivers for Vista from day 0 on, but none for XP - yet forget about Linux :P

Well ObiWan2001, since I've replaced the (missing) files you named with those from package 8.5, things should work now, but they ain't. Supposedly, Mesa-drivers won't change anything about it...

perixx

---

### Post by perixx on 2008-11-23
At first: positive news!


I've managed to get TF2 to work, finally! It seems, that either Wine or ATI-fglrx has improved (or bugfixed), I'm using Wine 1.19 and Fglrx binary driver 8.10, currently.

There's no sound, but that's likely due to a messed-up alsa configuration, no other sound is played in any Program und Wine either.

The registry setup so far:

-fbo
-opengl
-1280x124
-glsl

Starter string is:

```
env WINEPREFIX="/home/xxxxx/.wine" WINEDEBUG=-all wine "C:\Programme\Steam\steam.exe" -applaunch 440 -dxlevel 81 -w 1280 -h 1024 -sw -noborder -heapsize 512000 -novid
```

That said, the performance sucks like a vacuum cleaner. Maybe 1/3 of the Windows performance in easy scenes at best, dropping to 3fps in intense battle situations, so it feels. Without any eyecandy like AA or AF turned on. Tearing is horrible. Edges look really blocky and textures are really crappy. *yuck*

I'd rate this 'bronze', not 'gold', that's for sure.
Maybe not fair, but comparing to XP is never - for either OS: all runs fluidly on my x1950gt WITH eyecandy and mic.


perixx

---

### Post by blaise69 on 2009-03-15
That also worked for me!

Here's my setup, it's all recently been installed, so it should be fairly test worthy and fresh

Ubuntu 8.10
Wine 1.0.1
Radeon X1950
OpenGL version 2.1.8087

I added the Registry settings as mentioned in the recentl previous posts.

With the starter string above here's what happend.

Steam loads fine, selecting a server is fine, connecting holds at the "Sending Client Info" part.

I check my terminal and here is the output string

"Corrupt JPEG data: 57 extraneous bytes before marker 0xdb"

As I click cancel to disconnect the terminal posts...

"CellID: Connecting to 208.111.182.250:27031. . .
CellID: Connect to 208.111.182.250:27031 took 108 MS
CellID: Nothing beat our old best time of 17 MS"

Strange I think, so I instantly try and reconnect to the same server, everything flashes through fast, and I connect instantly!

There's only one person on the other team though, so I cancel after a quick run around and try another server

Instant connect again, it looks like it works, no idea why it fails the first time.

Performance is playable, texture quality is set to lowest, which is a shame.

I'll experiment with different settings when I have a chance, but this is progress at least.

Cheers,

Blaise.

---

### Post by perixx on 2009-05-11
Well, that's as far as it goes, blaise69!


Ati has terminated support for the X19xx series for good - so that leaves us with a 2-years old card without new drivers (while the current state is satisfactorily at best). That is, if you don't count in the Radeon open drivers project, which recently has added support for our 'legacy' cards. I didn't try that one, but I don't expect any serious 3D-performance from this side.

Cheers,


perixx

---

### Post by Duskao on 2009-05-12
It shouldn't be too long till there is some decent 3D support for the open source drivers as AMD has just released a bunch of info and sort of how-to's to the open source developers. So basically it is in our hands now. All the amazing open source-ers out there have created ubuntu and many find distro's all over the place, I'm sure they will make some wicked drivers to go along with it, and thus not making the older video cards obsolete anymore even though they are "legacy". Phoronix has more details. [http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1)

---

### Post by asdfoo on 2009-05-12
> **Duskao said:**
> It shouldn't be too long till there is some decent 3D support for the open source drivers as AMD has just released a bunch of info and sort of how-to's to the open source developers. So basically it is in our hands now. All the amazing open source-ers out there have created ubuntu and many find distro's all over the place, I'm sure they will make some wicked drivers to go along with it, and thus not making the older video cards obsolete anymore even though they are "legacy". Phoronix has more details. [http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1)

It's all actively being worked on, but it takes a lot of time to write drivers that support everything which Wine needs to work well.

---

### Post by perixx on 2009-05-23
To be honest, I don't care about Wine anymore. 


Haven't had a single decent experience that would've been worth all the messing about. Usability and even more the functionality isn't what I expect from a mature application and the performance is too far behind native software. Regular crashes and Windows-API-inherited security holes don't make the situation better. It appears, that Wine starts implementing GL3 features, while it still hasn't implemented all of the previous versions. This is just natural, of course. The Programmers will always be behind on schedule trying to integrate all the new fancy Windows functions MS keeps producing.  

If not for games, which Wine isn't suitable for in my opinion, unless you got a Cray, real use for it scarce. Maybe for some special Windows-based company software, e.g. I don't really see the point in using Wine for common Windows software like MS-Office. May it be buggy and missing some features, native OSS software like OpenOffice will make a lot more sense here, I feel, and in some cases they even do a better job.
Perhaps some day Wine will really provide the neccessary speed, functionality, stability and security to help replacing Windows completely. But I guess by that time, Linux won't need Wine anymore.

For the reasons stated above, it's probably a far better idea to run Windows in a VM instead, which I'm gonna try out at some point.
Btw., for the troll- and heretic-hunters out there: this is my personal opinion and experience with Wine. I encourage everybody else to go for and try it, of course, if they will.

Well, I certainly hope, that the OSS 'radeon' driver will jump in as a fully accellerated 2D-replacement for the deprecated ATI driver, soon, so it can be used with Compiz-Fusion, for instance. The problem is, that ATI only releases information bit by bit and I doubt they will ever do it with all. There's legal reasons for that too, since they don't own all the technology patents themselves, from what I understand. That's why I don't expect any miracles too soon. Would be cool, if, say, stuff like Blender was fully 3D-supported some time, and all the GL2/3 featues.

regards,


perixx

---

### Post by asdfoo on 2009-05-24
Maybe you have some misconceptions.

> **perixx said:**
> To be honest, I don't care about Wine anymore. 


Haven't had a single decent experience that would've been worth all the messing about. Usability and even more the functionality isn't what I expect from a mature application and the performance is too far behind native software. Regular crashes and Windows-API-inherited security holes don't make the situation better. 

> **perixx said:**
> It appears, that Wine starts implementing GL3 features, while it still hasn't implemented all of the previous versions. This is just natural, of course. The Programmers will always be behind on schedule trying to integrate all the new fancy Windows functions MS keeps producing.  

If a Windows app uses OpenGL, it has full access to any OpenGL features provided by the video driver, that has nothing to do with Wine

> **perixx said:**
> 
If not for games, which Wine isn't suitable for in my opinion, unless you got a Cray, real use for it scarce.

My computer is 2 years old, and plays CS:S, TF2, Stalker and BF1942, which is all I'm interested in really, I also played all the left 4 dead campaigns to completion.  I don't really care about the latest titles.

> **perixx said:**
>  Maybe for some special Windows-based company software, e.g. I don't really see the point in using Wine for common Windows software like MS-Office. May it be buggy and missing some features, native OSS software like OpenOffice will make a lot more sense here, I feel, and in some cases they even do a better job.
Perhaps some day Wine will really provide the neccessary speed, functionality, stability and security to help replacing Windows completely. But I guess by that time, Linux won't need Wine anymore.

For the reasons stated above, it's probably a far better idea to run Windows in a VM instead, which I'm gonna try out at some point.
Btw., for the troll- and heretic-hunters out there: this is my personal opinion and experience with Wine. I encourage everybody else to go for and try it, of course, if they will.

Well, I certainly hope, that the OSS 'radeon' driver will jump in as a fully accellerated 2D-replacement for the deprecated ATI driver, soon, so it can be used with Compiz-Fusion, for instance. The problem is, that ATI only releases information bit by bit and I doubt they will ever do it with all. There's legal reasons for that too, since they don't own all the technology patents themselves, from what I understand. That's why I don't expect any miracles too soon. Would be cool, if, say, stuff like Blender was fully 3D-supported some time, and all the GL2/3 featues.

regards,


perixx

You use ATI?

So it seems the root of your problem is that you have poor video drivers which results in a bad user experience when it comes to the requirements of Wine, which is unfortunately because ATI have been not very interested in linux for the past 10 years or so, but nvidia have.


and fyi, I use Ubuntu for my desktop and games, but I run Windows Vista on my laptop for work stuff.

---

### Post by perixx on 2009-05-26
Yes, I'm aware of the incomplete and poor OpenGL-implementation in ATI's drivers. 
But I've also been reading about OpenGL2 not being fully implemented in Wine somewhere (can't say where it was anymore). 
This corresponds to my experience of getting TF2 running only after updating to the very latest version of Wine, which I had to wait for 2 months. I've updated the proprietary driver, too, around that time, though, so it's maybe not initially related to Wine and OpenGL. Or it's due to a mix of both of the ATI-driver- and Wine-improvements.

Although the binary drivers have improved much lately, they still provide a sorry performance, compared to the Windows pendant and have been taken from the development line now. If not using any eye-candy features and not the full native monitor resolution, some native 3D-shooters will perform not that bad. But Wine + TF2 are really out of the question.
This can't be all blamed on the binary driver. 
The regular Wine-crashes, it's poor UI and security problems inherited from the Windows-API are also reasons, I'm opting out of Wine for now.

Well, it's really doubtful, if I can await some decent open graphics driver for my card. I'd be happy to get some good drop-in replacement for 2D-accelleration, e.g. for Compiz-Fusion, though. After all, I'm too busy to play games anyway, lately.

regards,


perixx

---

### Post by asdfoo on 2009-05-26
> **perixx said:**
> Yes, I'm aware of the incomplete and poor OpenGL-implementation in ATI's drivers. 
But I've also been reading about OpenGL2 not being fully implemented in Wine somewhere (can't say where it was anymore). 
This corresponds to my experience of getting TF2 running only after updating to the very latest version of Wine, which I had to wait for 2 months. I've updated the proprietary driver, too, around that time, though, so it's maybe not initially related to Wine and OpenGL. Or it's due to a mix of both of the ATI-driver- and Wine-improvements.

Although the binary drivers have improved much lately, they still provide a sorry performance, compared to the Windows pendant and have been taken from the development line now. If not using any eye-candy features and not the full native monitor resolution, some native 3D-shooters will perform not that bad. But Wine + TF2 are really out of the question.
This can't be all blamed on the binary driver. 
The regular Wine-crashes, it's poor UI and security problems inherited from the Windows-API are also reasons, I'm opting out of Wine for now.

Well, it's really doubtful, if I can await some decent open graphics driver for my card. I'd be happy to get some good drop-in replacement for 2D-accelleration, e.g. for Compiz-Fusion, though. After all, I'm too busy to play games anyway, lately.

regards,


perixx

Native shooters don't use all the features of the video drivers required to effectively translate Direct3D to OpenGL, that's why you don't see problems with them.  I've been burnt by ATI too, but hopefully one day there will be good drivers.

---

### Post by TonyFordz on 2009-05-29
I have this game also on steam but I have never played it yet hell I cant even get the little games to work in steam so doubtful I will get much else to. As you can [see]("http://steamcommunity.com/id/TonyFordz") I have 60 games none of which I can play which really sucks I am very close to reformatting just so I can game because I am disabled & time is all I have & when I have nothing to do I go nuts.

---

### Post by Duskao on 2009-05-30
Most of those games should work fine in wine, even with an Ati video card. Check out winehq.org and the appdb for more info on each. 
I'm using a Radeon 4850 with wine and most of my games work quite well. There are a couple games that I am having issues with (left 4 dead, mass effect) but other then that no problems really. No, I'm not some savy programmer or anything like that. In fact I'm very new to ubuntu and linux in general, my start date with this forum shows that quite accurately. I have almost every source engine game running fine by my standards, and many more running near flawlessly. Some include, Oblivion, Fallout 3 (bit slower then in windows though), Guild wars, Escape from Butcher Bay, KOTOR, Doom 3, Vampire the Masquerade: Bloodlines (actually runs better in wine then windows, haven't had it crash yet, or fail to start), Starwars Republic Commando. Those are just to name a few of my favorites which run great, just a couple minor graphic facial glitches in Oblivion and Fallout 3. 
This is all done on Ubuntu 9.04 with the catalyst 9.5 drivers. 
Don't get me wrong, this isn't perfect, but not having to deal with virus's, malware, spyware and the bloated programs that are supposed to stop all that garbage, along with all the security holes within windows and explorer and microsofts incessant need to make newer buggier more bloated programs then the originals instead of fixing them and making sure the programs work properly... 
Well, I will happily take a couple minor set backs then deal with all that and more.

---

### Post by perixx on 2009-05-30
Now,

I've been able to run some Windows-based games rather neatly inside Wine: some (2D) game demos, Crazy Machines, Peggle - even music synthesizers - for a few minutes, that is. All of them crashed after a certain amount of time and I've tried several versions of Wine, also two completely different kinds of sound hardware and even with Alsa replaced by a recent version of OSS. Whether the crashes were due to a bad ATI OpenGL implementation, I don't know. 
Still, all Wine versions suffered from the same problems I mentioned above, like poor UI and stability issues in itself. I doubt, that ATI's to blame, if the Wine window can only be pushed outside the bottom of the screen, but not pulled back in, for instance, which happened to me with all versions even the above 1.xx ones.

Regarding the security of Wine and Windows apps, here's an interesting discussion: 
[http://ubuntuforums.org/archive/index.php/t-543419.html](http://ubuntuforums.org/archive/index.php/t-543419.html)

Another problem which isn't addressed there, are security holes in buggy binary graphics drivers, be it ATI or NVIDIA, which infected Windows apps might probably use to circumvent certain Linux security barriers, since parts of them are running in kernel mode: 
[http://www.phoronix.com/scan.php?page=news_item&px=NjAwMQ](http://www.phoronix.com/scan.php?page=news_item&px=NjAwMQ)

Somewhat outdated, perhaps, but it could happen anytime again. Recently implemented features like cloud computing abilities in those drivers might well result in additional security issues.
Security holes are a more general problem with badly designed binary drivers and proprietary software, though, like you can see here: 
[http://it.slashdot.org/article.pl?sid=07/07/18/0319203](http://it.slashdot.org/article.pl?sid=07/07/18/0319203)

But I don't want to fire up an off-topic discussion...


perixx

---

### Post by Duskao on 2009-05-30
I'll agree with you as far as the security holes, I never knew about the nvidia driver issues within that respect, however the requirements to actually have that security hole are quite extraneous as it seemed like it was gentoo only, and driver specific. Not to mention that it could be negated by a firewall.

Running windows applications with wine on linux certainly would have it's risks. Unfortunately, like any security issues, it's up to the user to protect themselves. First off, you NEVER sudo wine. So even if you did become infected, it will only effect the wine applications, and that is only potentially. If you are using crossover games or creating prefix's for each installation, that can actually protect you more. Second, most of the issues listed within the articles can be largely protected by a firewall. It doesn't matter what operating system you use, you should always use a firewall. Or if you feel the need, you can also use an antivirus. But it's like you said before, at least in your case, nothing seems to run for more then a few minutes before it crashes. So the reality of it is that the same thing would happen with a virus. 

If you are truly uncomfortable using wine within linux, then don't. There are plenty of good native linux games out there if that is what you are into. 

I however can understand you not being happy with the Ati drivers for linux. They aren't quite up to snuff, but they are getting better with each release. Plus as I mentioned before, with the release of the 3d code the open source drivers are inevitably going to come out on top, it's just a matter of when. 

If you truly do like ubuntu/linux but need the commercial games I'm sure there is nothing stopping you from dual booting. If you do decide to do that, I am going to recommend a small program for you for windows. In alot of ways it negates having to use AV's and security suites. Just try it and run it through the motions to see what I mean. Anyway, it's called geswall. But once again it's only as good as the user that is using it, but this one is a bit more fool proof. [http://www.gentlesecurity.com/](http://www.gentlesecurity.com/)

---

### Post by asdfoo on 2009-05-31
The Wine project does not aim to provide any sort of security measures, so I don't know why you're even bringing this up.  Ubuntu isn't really any more or less secure than Windows, there are many mitigating factors to consider in both.

---

### Post by perixx on 2009-06-01
@Duskao
ATI's drivers for sure have improved a lot. Unfortunately, the current driver's final state is unsatisfactory to me. The company's policy of declaring hardware as young as 3 years (e.g. X1950 series) is not acceptable. 
I won't be able to make the switch to newer Linux releases with X server 1.6, yet to Karmic and its upcoming X server 1.7. If they provided support up to the point where the radeon drivers are ready to replace the binary drivers, it would be fine with me. There's also been too much other trouble with installation-, stability- and functionality issues. My next card will most probably an Nvidia. 

GeSWall seems an interesting option for Windows, thanks for the hint! 
I'm just not convinced whether it can completely replace a real-time antivirus scanner and a firewall (not a personal firewall), yet with unobtrusively.
It's said to protect 'confidential' files, but how would the program know, what really is, without obtrusive user interaction - also, read-only access to the registry is okay for normal working at best, but updating virus scanner software can already require write access... I'd have to see that program in action to judge. But if it's really as reliable as promised, who can tell?

By the way, it's bad enough, that I'm having to deal with Vista at work, but I'm really not planning to get any future Windows version for personal use after XP anymore.  
 

@asdfoo
I brought up this security topic, because it's one of the problems I see with Wine, not being the only one. At present, we are not facing any real threat from infected executables under Wine, if suggestions like they can be found under the link above are followed - I see that your way.
It might change anytime, though, e.g. as soon as someone writes some 'Winux'-like thing that exploits a Wine bug, or when platform-independent virii, exploiting hardware driver bugs are propagated. I could also think of programs containing platform-independent scripts and malware, written in Python, Java or whatever.

Currently, Linux' best protection is its low degree of propagation in the desktop sector - around 1% on the market, if I'm not mistaken. 
The situation will change, as soon as the market share increases significantly, and crackers and organized crime are stepping up.
With Windows, all that users can do, is to sit and wait for MS (mayhaps) reacting and fixing their worst bugs, or someone selling them additional security for cash. 
With Linux, people can openly discuss upcoming threats and challenges and implement additional security features in advance instead of only reacting.

OK, so I've finally triggered off a security discussion :)


perixx

---

