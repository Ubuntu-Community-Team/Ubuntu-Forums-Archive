---
title: "Half-life 2 + Source Games on Wine"
date: 2007-10-20
forum: Wine
---

### Post by Baerun on 2007-10-20
I'm trying to set up HL2  and the other source games to work with wine. I'm using Wine -0.9.47 on Ubuntu 7.04. I can run non-source games on Steam (half-life, counter-strike 1.6, TFC, DoD), but when I try to run Half-life 2, it starts up, changes my res, and then quits. With DoD:S and CS:S I get the background for the menu and the loading icon in the bottom right before it quits. All of them give me the same error:
 ```

fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x13bd58) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x13bd58) Event query: Unimplemented, but pretending to be supported 
fixme:avifile:AVIFileExit (): stub!

```
I looked around for info on this and a lot of people said that this started happening since wine version 0.9.44 so I tried using 0.9.43 and just ended up with a different error that I couldn't find much info on. I've tried messin around with the wine config and there has been no change. I've also tried a bunch of different launch options in steam and still get the same thing. 

Any help would be much appreciated.

---

### Post by FlamingGooch on 2007-10-21
I'm having the exact same problem as you are Baerun. Half-Life 2 changes my resolution and quits. Bump for help!

---

### Post by wh1terabb1t on 2007-10-21
I have run into the same issue with Ubuntu 7.10 and WINE 0.9.46 with Counter Strike : Source.  Even in forced windowed mode CS:S crashes during the loading screen.  I read that desktop effects might cause the issue, has anyone heard similar? Any help would be greatly appreciated. 

-Andrew

---

### Post by eljoeb on 2007-10-21
Right click the game you want to start in the My Games menu.  Click properties and then set launch options, and then do a "-h xxxx -w xxxx" to your resolution.

So for example, my resolution is 1280 x 1024.  So my half life 2 launch options are:

-w 1280 -h 1024

At least I think so.  Those might need switching.  But I had the same problem and this seemed to fix it.

---

### Post by eljoeb on 2007-10-21
> **wh1terabb1t said:**
> I have run into the same issue with Ubuntu 7.10 and WINE 0.9.46 with Counter Strike : Source.  Even in forced windowed mode CS:S crashes during the loading screen.  I read that desktop effects might cause the issue, has anyone heard similar? Any help would be greatly appreciated. 

-Andrew

I don't recommend desktop effects with wine.  Its a resource hog.  Your games will run much faster with them turned off.

---

### Post by wh1terabb1t on 2007-10-21
I disabled desktop effects and attempted to run CS:S again, resulting in the same issue as before.  The last thing in terminal after the window says something about an AVIFile Stub or something.

---

### Post by eljoeb on 2007-10-21
> **wh1terabb1t said:**
> I disabled desktop effects and attempted to run CS:S again, resulting in the same issue as before.  The last thing in terminal after the window says something about an AVIFile Stub or something.

If I remember right there is a launch option that turns off the videos... -novid maybe?  That might take care of it.  Try that.

---

### Post by shad0w_walker on 2007-10-21
The options i have sucessfully tested (I don't require them but they work) are

-novid (disables intro videos)
-dxlevel 80 (Forces the mode to directx level 8)

---

### Post by aoanla on 2007-10-21
It seems that a lot of people (including me) have found the more recent builds of Wine to be very unreliable with Source engine games like Half life 2.

If you downgrade to wine 0.9.42, this seems to be the most stable version for most people, at present.

---

### Post by coldguy on 2007-10-21
I'm a noob. How do I use the older version of wine?

Same problem. I just upgraded to Gutsy 7.10 and I assume the latest wine from repositories. HL 1 games run fine. Source engine games crash right back to desktop after my monitor clicks. Setting -novid -dxlvl80 -h800 -w1024 don't work either. Steam says drivers outdated and lists Direct3D HAL version 6.14.0.0. I assume thats my DirectX level? I'm not sure if I'm using the best driver. I have a Gigabyte mobo with AMD690G integrated ATI express 1250 gfx. I enabled the ATI accelerated graphics driver in the restricted drivers manager. How does that compare to compiling the driver from ATI's website?

Also of note..If Steam is running, UT2004 linux version has no sound, but sound still works for everything else. I have Wine set to use ALSA drivers because if I check OSS it kills all sound to everything, desktop, media players don't even show the volume controls, I get that error about the device being busy.

Before I upgraded to Gutsy, I was able to get to the menu for CS:S and HL2 with the 3d scene in the background. HL2 would crash when trying to start a game, CS:S was able to start, but ran at 2 fps. Then I tried something from a forum post to fix the driver and it broke all source games, instant crash. (I also somehow broke synaptic trying to add mediabuntu reps, not related except thats why I did a fresh install with Gutsy)

---

### Post by Baerun on 2007-10-22
I have also tried the -novid and the dxlevel options with the same results. I am also not using any desktop effects. I found this: [http://bugs.winehq.org/show_bug.cgi?id=9572](http://bugs.winehq.org/show_bug.cgi?id=9572)
they say that if you turn off the steam-community in-game setting under setting it will fix it but this does not work for me.

---

### Post by aoanla on 2007-10-23
> **coldguy said:**
> I'm a noob. How do I use the older version of wine?


If you were using Feisty, still, I'd tell you to go here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
download the relevant deb package, and install it with
sudo dpkg -i nameofpackage

Unfortunately, there are no builds of wine with versions below 0.9.46 for Gutsy, so you'd probably have to compile from source.

> 
Same problem. I just upgraded to Gutsy 7.10 and I assume the latest wine from repositories. HL 1 games run fine. Source engine games crash right back to desktop after my monitor clicks. Setting -novid -dxlvl80 -h800 -w1024 don't work either. Steam says drivers outdated and lists Direct3D HAL version 6.14.0.0. I assume thats my DirectX level?


Sort of. Wine seems to return this to DirectX games, even though it actually supports most of DirectX 8, and enough of DirectX 9 for many games to run using it.

> 
 I'm not sure if I'm using the best driver. I have a Gigabyte mobo with AMD690G integrated ATI express 1250 gfx. I enabled the ATI accelerated graphics driver in the restricted drivers manager. How does that compare to compiling the driver from ATI's website?


People seem to have variable success with different versions of the ATI proprietary driver. There's a *brand new* version due out by the end of this week, though, so it might be worth waiting for that to see if it improves things. (The current bleeding edge driver improves things for me, but has been unstable for others.)

> 
Before I upgraded to Gutsy, I was able to get to the menu for CS:S and HL2 with the 3d scene in the background. HL2 would crash when trying to start a game, CS:S was able to start, but ran at 2 fps. Then I tried something from a forum post to fix the driver and it broke all source games, instant crash. (I also somehow broke synaptic trying to add mediabuntu reps, not related except thats why I did a fresh install with Gutsy)

Well, unfortunately, the versions of wine that come with Gutsy seem to be particularly problematic for those with ATI cards - which is apparently more due to problems with the fglrx drivers than with wine, but that doesn't help much.

---

### Post by Tavorisch on 2007-10-23
Okay, So I am using the latest restricted nvidia drivers or rather for (the latest cards) I have a 8600GTS by MSI... compiz fusion works unremarkably well, over 400FPS with full rain and everything.. So I decide to install wine and wine-dev from gutsy synaptic,, and I get tahoma, and install steam, and run the browser command.. steam installs perfectly and runs... So i have no sounds and it freezes on the first loading screen after the valve logo and copyrights.. I uncheck everything in audio drivers including driver emulation, and check ALSA, BAM sounds works and everything passes the first loading screen and loads really fast, to the 3d rendered backround image which works perfectly, and when I try and start a game it gets all the way to the end. and just stops with the first little sound clip repeating itself.. should i install an older version of wine? .2 instead of .6??? or is there something I need to mess with in wine config... any help would be amazingly appreciated.. thanks

-patrick

---

### Post by Baerun on 2007-10-23
> **aoanla said:**
> It seems that a lot of people (including me) have found the more recent builds of Wine to be very unreliable with Source engine games like Half life 2.

If you downgrade to wine 0.9.42, this seems to be the most stable version for most people, at present.

I tried downgrading to wine 0.9.42 and ended up with this error: 
```
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x1bb710) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:D3D9CB_CreateSurface (0x1bb710) IDirect3DDevice9_CreateSurface failed
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0xdd6c938
fixme:d3d9:IDirect3DDevice9Impl_CreateTexture (0x1bb710) call to IWineD3DDevice_CreateTexture failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1bd6e8) Event query: Unimplemented, but pretending to be supported
err:d3d:pbuffer_find_fbconfigs Failed to find exact match, finding alternative but you may suffer performance issues, try changing xfree's depth to match the requested depth
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  809
  Current serial number in output stream:  811

```
Has anyone heard of this error?
I also tried the patch that was posted on the bug page and got the same error as before. :confused:

---

### Post by MichaelLerch on 2008-02-11
Time to bring a old topic back to life!  I'm suffering this very same problem.. I have a quad-core processor and it seems the videos are just zooming by.  I think everything is just going to fast?

---

### Post by saz on 2008-02-22
same problem here... pls help

---

### Post by karnerblue on 2008-02-24
I'm having the same problem where my steam games make it to the Valve loader screen and crash, or just crash period. I'm downloading Portal right now to see if that will work, but so far I've tried HL2 and HL2:Deathmatch with no luck. I've got an HIS Radeon HD 3850 and so far it's been nothing but a pain in the ***, sadly. I just switched to Ubuntu after getting finally fed up with Windows, and I'm regretting having bought an ATI card.. But anyway,

My setup:
Ubuntu 7.10 Gutsy
Wine 0.9.46
Radeon HD 3850 

Here is what has **not** worked for me so far:
-Disabling Steam Community In-Game
-Disabling desktop effects
-Installing ATI drivers for windows through wine to c:/ so that Steam would think I have the right drivers (Kind of a long shot, but tried it anyway with no luck)
-HL2 Launch settings -w 1280 -h 1024 -novid

Now it crashes so hard that when I try to load it it logs me out of Ubuntu. I've been working on this for a couple days now, is there a really intensive walkthrough on this anywhere or something?

---

### Post by naz37 on 2008-03-01
i had this problem, hl2 hanging at loading screen. i fixed it by enabling ALSA audio support.

open terminal, run winecfg
On the audio tab _disable_ OSS support and _enable_ ALSA

hopefully source based games(CSS/HL2/Portal) should start.

---

### Post by MadnessRed on 2008-05-17
OK had the same problems, I set the launch options to 

-w 1280 -h 1024 -novid

and disables steam community and all that and all allerts, and the game runs but really flaky, not jumpy, i mean like you get a load of black triangles on the screen, would post a screenshot however game crashed when someone talked to me on aMSN so i didn't get a chance, gonan run it again now

Computer info

Abit IP-95
GeCube Radeon HD3850 512mb
Intel P4 3059 MHz
2gb RAM DDR 2
Ubuntu 8.04 LTS fully updated
WINE 1.0-rc1

Hope this is useful and get you underway. Will run HL2 Lost coast and give a comparative benchmark as well.

---

