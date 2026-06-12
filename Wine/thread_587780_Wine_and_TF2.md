---
title: "Wine and TF2"
date: 2007-10-23
forum: Wine
---

### Post by upbeat.linux on 2007-10-23
If you're like me you had a few issues getting Team Fortress 2 to run smoothly in Ubuntu under wine.  Here are a few helpful hints I've compiled......

1. Follow the great guide here (note, for those who purchased it online, don't worry about copying the DVD files over...obviously):

[http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/)

2. Make sure you have the correct wine repository added:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

then run

 ```
 sudo apt-get update
```

Note, you may have to your restart your session for this to work (CTRL+ALT+Backspace)

3. Disable Steam Community Settings

i. Open Steam and go to the File Menu
ii. Select "In-game tab"
iii. Uncheck "Enable Steam Community In-Game

4. Within the game go to: Options | Video | Advanced and set "Model Detail" to "Low". Note, you can change this back to whatever setting you desire after the game is running smoothly.

5. To open the wine "registry":

i.  Press ALT+F2,  type regedit, then hit enter. 
ii. If it doesn't already exist add the following key 

```
Direct3D
```

under 

```
HKEY_CURRENT_USER\Software\Wine 
```

The full path should look like: 

```
HKEY_CURRENT_USER\Software\Wine\Direct3D
```

iii. Add the following STRING values under Direct3D

```
OffScreenRenderingMode fbo
PixelShaderMode Enabled
UseGLSL Enabled
VideoMemorySize 256

```

Hope this helps!!!

---

### Post by upbeat.linux on 2007-10-24
If you're having issues launching Steam and receive an error message akin to:

```
Could not connect to Steam Network. Either the Steam network is currently not running, or your internet connection is down. Please check your internet connection and try again.
```

Make sure moblock is turned off:

```
sudo killall moblock
```

or that you have added the proper exception to allow Steam an outgoing connection.

---

### Post by B00R4dL3y on 2007-10-25
When I quit, hl2.exe goes <defunct>.  Is there a way to kill the process?  Steam won't let me exit.  It says there's an application still running and won't let me exit.

---

### Post by Hyperkill on 2007-10-25
I have tried all of the above and my game still crashes just after the chick yells, "Gordon" in the beginning of the game.  Any help is appreciated.

---

### Post by Alex Carroll on 2007-10-25
> **B00R4dL3y said:**
> When I quit, hl2.exe goes <defunct>.  Is there a way to kill the process?  Steam won't let me exit.  It says there's an application still running and won't let me exit.

Press Alt+F2 and type wineserver -k

That'll close all Wine apps.

---

### Post by upbeat.linux on 2007-10-25
What version of Wine are you running .47 or .46? You may need to downgrade to .46. 

While running .47 TF2 would crash unless the model detail was set to low. For some reason .46 doesn't seem to have this issue.

> **Hyperkill said:**
> I have tried all of the above and my game still crashes just after the chick yells, "Gordon" in the beginning of the game.  Any help is appreciated.

Also, make sure Wine is set to emulate Windows XP and not 2000. I had to reinstall Wine not too long ago and it defaulted back to Windows 2000 emulation causing all Source based games to crash.

---

### Post by Hyperkill on 2007-10-25
> **upbeat.linux said:**
> What version of Wine are you running .47 or .46? You may need to downgrade to .46. 

While running .47 TF2 would crash unless the model detail was set to low. For some reason .46 doesn't seem to have this issue.



Also, make sure Wine is set to emulate Windows XP and not 2000. I had to reinstall Wine not too long ago and it defaulted back to Windows 2000 emulation causing all Source based games to crash.

I can't thank you enough dude.  Your advice has fixed every issue for me.  Hopefully I don't run into anything somewhere along the way.

---

### Post by upbeat.linux on 2007-10-26
You're welcome.  Hopefully more people will find this useful and add to it. 

More likely than not there I are things I missed especially since multiple bugs for TF2 are filed on the Wine Application DB page. 

Here's hoping the Wine team will take note of the Source problems inherent to 0.9.47 and make the appropriate changes.

Cheers!

---

### Post by karth on 2007-10-26
I can confirm the "Low model details" trick under Wine 0.9.47, in TF2.

I also experienced crashes at random when playing ingame videos (i.e. video map briefing).
Skipping it ASAP prevented me from being frozen. I'd recommend the "-novid" wine option if you encounter this issue. Can someone confirm?

---

### Post by dayvideg on 2007-10-28
I am able to fire up steam and load tf2 but once i spawn on a server there is uncontrollable spinning. Anyone else have this problem?

---

### Post by sfunk1x on 2007-10-28
I don't see the spinning, but I had lock ups on map start until I turned all my detail settings to low. But it's working great now.

Thanks guys.

---

### Post by EXCiD3 on 2007-10-28
So what do you guys think of TF2? Is it worth getting orangebox?

---

### Post by dayvideg on 2007-10-29
its worth it hl2+ep1+ep2+tf2+portal.  portal is a refreshing change for fps & puzzle games too bad its short

---

### Post by TestTubeBaby on 2007-10-31
you guys getting the spinning are getting farther than me.  TF2 launches fine and I see the valve logo and if I hit Esc I can even see the TF2 loading screen for a few seconds before it just flat out closes.  I'm running 0.9.48

---

### Post by dayvideg on 2007-11-02
i got the game runnning and no spinning. The following command line options for me seem to work:

SDL_VIDEO_X11_DGAMOUSE=0 SDL_MOUSE_RELATIVE=0 WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \ -width 800 -height 600 -applaunch 440 \ -heapsize 1000000 -novid -gl 

I think the first part fixed the mouse spinning issue, some of the other options ie: resolution and heapsize can be modified to what will work on your system.

I couldn't get the game to run on wine .47 had to switch back to .46. Also I remember changing regedit and added some lines for Direct3D. Not sure if the instructions were on this forum or one on a linux gamer forum.

---

### Post by karth on 2007-11-16
Can anyone tell if I'm the only one who crashes whenever I get "dominated" by somebody.

I hear the jingle and when the message is supposed to show up, the game crashes...

---

### Post by dayvideg on 2007-11-16
haven't run into that problem might want to try setting the video settings to low and then slowly crank up the settings once you can get it running

---

### Post by karth on 2007-11-17
Sadly, setting everything to the lowest didn't help, I tried already. I played with the Direct3D in the registry too, with no luck

I'm running under 0.9.49; and I've been experiencing this since 0.9.47
I don't want to go back to 0.9.46; that said, if no solution comes up, I guess I'll wait for a possible fix in the later wine relases

---

### Post by upbeat.linux on 2007-11-20
Try disabling "Color Correction"....

Also, try removing wine completely, cleaning packages, and then reinstalling wine.

---

### Post by nchase on 2007-11-20
Thanks a lot for posting this guide. I followed your instructions to the 'tee' and my performance is far better now. The game used to run very well for me until I updated WINE. Now that I have downgraded to 0.9.46, it runs far better.

The game seems to stutter a bit after a game loads up, but about two minutes into the map -- which is i guess after more information is cached? -- the game runs as I remember.

Thanks again.

edit: Now, if only I could get my mic working.

---

### Post by karth on 2007-12-05
Sorry for replying so late

Since I am running TF2 in dx81 mode, the Color Correction option is locked (and it reads "disabled").
I tried almost every possible configuration, with and without support of various features.
I'm also experiencing strange problems with in game fonts (they look unusually small and crippled) as shown in the* attached screen shot.*

Also, I would like to know... Does this very screen represent what I am supposed to see while waiting to re spawn under Wine? If so, I definitely have a problem which may lead to my repeating crashes since it's not what I'm seeing.

Screen: [http://appdb.winehq.org/appimage.php?iId=13544](http://appdb.winehq.org/appimage.php?iId=13544)

---

### Post by aaargh486 on 2007-12-05
Works great here, in Dx81. Every setting on high, works fast and stable. Tomorrow I'm going to download Wine .50 and try it in DX90 mode.
Thumbs up!:lolflag:

---

### Post by karth on 2007-12-07
Ok, so I think I have got rid of my repeating crashes when being dominated...

The problem was with the french version of TF2, probably linked with the font rendering bug known to crash other multiplayer source games.

I translated TF2 to the english version and suddenly, no more crashes.

Edit: here is the link to bugzilla. I repeat: I only suspect my problem to be related to this (regarding my previous post about font rendering problems)
[http://bugs.winehq.org/show_bug.cgi?id=7698](http://bugs.winehq.org/show_bug.cgi?id=7698)

---

### Post by Sonja on 2008-01-07
How do I buy it online and download it on Ubuntu in the first place?

---

### Post by jpbelauskas on 2008-01-07
install wine.  install steam ([www.steampowered.com](www.steampowered.com)), buy games through steam and start playing after you've gone through the fixes in this thread.

---

### Post by Bannor on 2008-01-07
> **Alex Carroll said:**
> Press Alt+F2 and type wineserver -k

That'll close all Wine apps.

wineserver -k will not fix the registry problem

---

### Post by Bannor on 2008-01-07
so Halflife 2 runs great with Wine door and Winedoors says I have downloaded and installed Directx 9.  But Team fortress 2 says it requires dx8  to run and immeadiately shuts down.

I have the newest version of wine install.  wine doors I have set a number of dlls to native I have dragged a bunch of dll's from windows I have run the dx9 install.  I have tried forcing directx 8 and 9. and nothing works.  I have read every tutorial  i have even gone to youtube to see folks install adn rund TF2 but nothing works 

amd 2x 2.2ghz 
ati x550 256mb video card
2 gigs of ram 
ubuntu 32 bit kernal
gutsy gibbon. 

wine .52

game runs fine on the window partition. 

HELP!!!

---

### Post by Bannor on 2008-01-08
any update or thoughts

---

### Post by Duncan Hollands on 2008-01-24
Hey I was wondering if anyone could help. 
Getting the 'need directx 8.0 to run properly error' 

I'm running on a IBM Thinkpad T42, 
Intel(R) Pentium(R) M processor 1.80GHz
1 Gig Ram
 Radeon Mobility M7 LW [Radeon Mobility 7500]  
    only 32MB ^^  

Currently using wine 0.9.53
with many dll overrides to try and get dx9 working  **EDIT** removed dll overrides from user.reg and re-installed wine using synaptic
Graphic Options: 
  Allow Pixel Shading
  Run in wine desktop window
  (not allowing window manager to control windows)
Sound Options:
  Checked ALSA tickbox, sound test works ok
  Unchecked OSS
RegEdits 
  none (currently)
  


I feel  like I've tried pretty much everything and a lot of things actually made it worse. I regressed to 4.6 (as there seemed to be a lot of positive feedback on it), tried editing the direct3d settings with regedit, using different windows versions. Didn't help, likewise in wine 0.9.53.  

Eventually tried to install dx9 using [http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html]("http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html")
didn't get a dxdiag.exe to run, and then on reading subsequent posts in forums found out it was pretty much pointless anyway. 
Essentially it seems to me like the ATI card in my notebook is the problem, I was just wondering if anyone knew anyway round it (replacing it is not going to happen).

---

### Post by Duncan Hollands on 2008-01-25
I found this guy
[http://mixman.res.lt/?status=articles&show=4]("http://mixman.res.lt/?status=articles&show=4")
who is offering a patch for different engine.dll's to fix the 'directx 8.0 required' error (he gives different ones depending on the system).
He seems legit, but does anyone have any opinions? I don't really know a whole lot about dll's.

---

### Post by DeElent on 2011-04-10
Does anyone know why the game wont launch for me? I get the initial popup window that says "team fortress 2 is preparing to launch..." for around 10 seconds then the window disappears and the game doesnt launch. Nothing crashes, I get no error messages, it just doesnt launch. Any help would be appreciated.

---

### Post by leonarven on 2011-08-06
> **DeElent said:**
> Does anyone know why the game wont launch for me? I get the initial popup window that says "team fortress 2 is preparing to launch..." for around 10 seconds then the window disappears and the game doesnt launch. Nothing crashes, I get no error messages, it just doesnt launch. Any help would be appreciated.
I have just a same problem. Any solutions?

---

