---
title: "Slow mouse in World of Warcraft"
date: 2007-01-16
forum: Wine
---

### Post by Dylock on 2007-01-16
I seem to have a very laggy mouse in WoW + wine. It doesn't make the game unplayable but there is a definite disadvantage in game play and end up tab targeting. Has anyone heard of this before and know of a solution?

Thanks
Dylock

---

### Post by BitTorrentBuddha on 2007-01-16
I find tab targeting superior anyway, the only problem is the horrible range by default, add the following line to the bottom of your Config.wtf (located in folder called WTF in your WoW directory):```
SET TargetNearestDistance "52.000000"
```52.000000 implies a max distance of 52 meters, you can go higher or lower, but I have no solution for your mouse problem.

---

### Post by Dylock on 2007-01-16
alright ty i will try that out.  yea ive gotten use to tab targeting. this mouse thing though makes it take a lot longer to interact with the UI

---

### Post by Ferrat on 2007-01-17
Have you tried setting a high mouse sens??

---

### Post by Dylock on 2007-01-17
yes it still produces the same effect
my mouse is a LX5 logitech mouse if that makes a difference.
i might try a regular mouse later on.

---

### Post by Dylock on 2007-01-21
bump

---

### Post by NICU28 on 2007-01-22
I had this problem when running WoW in Direct3D mode instead of openGL.  You can add the extra lines in your config.wtf file to always run in OpenGL with 
```
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"
```
I've been having problems changing my video settings in OpenGL so I use -d3d instead of -opengl to change configurations.

---

### Post by Dylock on 2007-01-22
aye those settings have already been set but no luck so fat.

---

### Post by lawchilly on 2007-02-26
I have this also, The game doesnt feel laggy but the mouse is very slow at responding. The mouse works fine on the logon screen and character select just slow in game. I have tried tons of stuff, still no help.

---

### Post by Sizzler on 2007-03-01
Did anyone solve this problem yet? I'm in the same boat! :(

---

### Post by Sammi on 2007-03-01
Is it only the mouse that is lagging or are you also experiencing low frame rates in the game overall?

Have you tried everything in the community WoW/Wine howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ?

Have you tried updating or reinstalling your graphics drivers?

---

### Post by Sizzler on 2007-03-01
I think I went through those instructions already but I'll try again.
Yes its only the mouse lagging graphics are perfect.

---

### Post by Sizzler on 2007-03-02
I switched the mouse to an old  logitech laser mouse and bypassed the USB hub and plugged straight into the computer and this improved the mouse quality a bit.I am getting a new mouse soon so I hope that will improve things further.

Oh I only noticed this error as well
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

maybe this has something to do with the problem :)

---

### Post by Ferrat on 2007-03-02
> **Sizzler said:**
> I switched the mouse to an old  logitech laser mouse and bypassed the USB hub and plugged straight into the computer and this improved the mouse quality a bit.I am getting a new mouse soon so I hope that will improve things further.

Oh I only noticed this error as well
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

maybe this has something to do with the problem :)

I get that error aswell but have no mouse problems at all =( 

sound like it could be and issue with the USB hub/USB drivers ect. do you have an USB keyboard? 
is it on the same hub?
do you have USB 1.1 or 2?
do you have alot of USB gear connected? Webcam? Ipod? ect. could be that you got to much traffic on you USB circuit, I know that if I coonect all my USB stuff my comp. get real problems handling it all no matter what OS, I feel the diffirence

---

### Post by Sizzler on 2007-03-02
As far as I know the computers USB is 1.1 and the hub is 2.0.
The keyboard isn't a USB type.
I disconnected all USB devices except for the mouse and it's still the same.

---

### Post by dtruesdale on 2007-03-02
Well my issue is not a mouse lag just no response on mouse overs unless I move the mouse around. Everything else is perfect and the Game loads better in Wine than in cedega. I get that same message about SPI_SETMOUSESPEED and it's not implemented. That to me is a wine setting. If I can get this fixed I'll be using Wine to play WoW fulltime.

---

### Post by SKLP on 2007-03-02
The problem is that Hardware Cursor can't be enabled when running wow with the OpenGL mode. And if you use Direct3D mode it won't be playable.
Only solution I know of i either a) use windows b) use cedega+direct3d mode

It sucks I know :(

---

### Post by dtruesdale on 2007-03-02
Scary thing is in Cedega I run it in Opengl, no direct3d. It works fine over there so what is different?

---

### Post by K3nto on 2007-03-04
Im getting the mouse lag aswell. Ubuntu Edgy, laptop (4 usb ports, only 1 used for MS usb laser mouse) im using the latest wine with WoW, OpenGL.

---

### Post by Aramil Moonmist on 2007-03-06
same issue here. frame rates are definitely livable, everything seems to work fine (including my 1280x800 resolution switch in windowed mode), but the mouse lags. the hardware mouse check box is grayed out, and im also getting the mouseread 113 error (multiple times), as well as the same thing except 112.

ubuntu 6.10
lastest wine
4 usb ports
usb logitech mouse, nothing else is in any port
even the touchpad lags

if i switch to d3d mode, i get 2 cursors. the desktop one that doesnt lag, and the in game cursor that does.

this really kills the game, and ive been playing it via windows, but its kinda annoying when you gotta keep switching oses, because nearly everything else i can do in ubuntu

***EDIT***
i tried one of my high speed ports, still nothing

---

### Post by NoFearDJB on 2007-03-07
Bump. I'm experiencing the same ordeal thanks in advance if anyone can find a fix! :D

---

### Post by kenshintomoe225 on 2007-03-08
I just installed WoW and am having the same problem, frame rates are great, mouse is quite laggy.  I saw what was posted earlier about a conflict with OpenGL and that makes sense, however I can't see why someone doesn't have a fix now.

---

### Post by Sammi on 2007-03-09
You guys all need to post your system specs. CPU, RAM, graphics card, mouse type etc.

And please post your graphics card driver version too.

I'm going to look into filing this bug on Wine's official bug fix page.

---

### Post by jolger on 2007-03-09
> **Sammi said:**
> You guys all need to post your system specs. CPU, RAM, graphics card, mouse type etc.

And please post your graphics card driver version too.

I'm going to look into filing this bug on Wine's official bug fix page.

Having the same problem:

CPU: Pentium 4 630 3.0 GHz
RAM: 2048 MB
Graphics: GeForce 6600 GT (PCI express x16)
Mouse: A4Tech X-710 (connected to ps/2 via adapter, wont work if its in usb -_-)
MB: Asus, p5nd2-sli Deluxe
SoundCard(s): on board: nvidia mcp40 (cant remember if it was exactly that name).
                       the other one (not on board (the one i use :P)) Sound Blaster Live!
799 GB of HDD space...

So you see, it shouldn't be my system :P

---

### Post by wkdown on 2007-03-09
Sorry all.  I'm throwing this quick WoW question into the thread because I don't feel it warrants its own...

I am considering buying WoW.  Being that it is exclusively online and has been out awhile, am I going to have a really bad gaming experience? ie Too low level for anyone to blink at me, too many PKers (are they still called that?), or other reasons?  Or should I suck it up and get the game?

Thanks to whoever doesn't blow past my post.

---

### Post by Sizzler on 2007-03-09
Heres mine:

DELL 2.25GHz P4
768Mb Ram
NVIDIA GeForce4 Ti 4200 with AGP8X

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 Ti 4200 with AGP8X/AGP/SSE2
OpenGL version string: 1.5.6 NVIDIA 87.76

Kensington USB mouse

---

### Post by kenshintomoe225 on 2007-03-09
>  	Sorry all. I'm throwing this quick WoW question into the thread because I don't feel it warrants its own...

I am considering buying WoW. Being that it is exclusively online and has been out awhile, am I going to have a really bad gaming experience? ie Too low level for anyone to blink at me, too many PKers (are they still called that?), or other reasons? Or should I suck it up and get the game?

Thanks to whoever doesn't blow past my post.

it would be a wonderful idea to start playing wow.  There are a lot of players that are either too immature or too high and mighty of course, WoW has 8 million players.  However the good majority of players are quite helpful.  You don't have to worry about PK, unless you are on a PvP server, and I wouldn't worry too much about being low level.  It won't take long to really take off.  Get the game! and hey, if you play alliance give a shout out to Wilhem over on the echo isles server <$me , good luck


and for the mouse issues:

CPU: Intel P4 3.2GHz
GPU: Nvidia 5200 GeForce FX with the latest drivers from sudo apt-get install nvidia-glx (can't remember the repository)
Mem: 512 MB

Logictech USB optical mouse

Latest version of wine as well.  Running WoW in OpenGL mode, direct 3d mode doesnt allow for much ;)

---

### Post by sk8dork on 2007-03-11
just like to chime in and reiterate a previous post's point: you guys experience 'mouse lag' because hardware cursor is not an option in opengl. with hardware cursor turned off you are telling the game to draw the cursor and it will be slow and 'laggy' with lower fps, even low at around 30fps. i don't know if it's possible for the wine devs to impliment hardware cursor support in opengl mode but supposedly it will work in d3d mode, but of course other things don't work so well in d3d mode.

your problem is (most likely) hardware cursor not being an option, and not your system setup. those of you that noticed some kind of benefit to changing ports or mice were probably just noticing it in a higher fps area.

so be on the lookout for any updates to hardware cursor capability, or overall improvements in d3d support.

---

### Post by Sammi on 2007-03-11
> **sk8dork said:**
> just like to chime in and reiterate a previous post's point: you guys experience 'mouse lag' because hardware cursor is not an option in opengl. with hardware cursor turned off you are telling the game to draw the cursor and it will be slow and 'laggy' with lower fps, even low at around 30fps. i don't know if it's possible for the wine devs to impliment hardware cursor support in opengl mode but supposedly it will work in d3d mode, but of course other things don't work so well in d3d mode.

your problem is (most likely) hardware cursor not being an option, and not your system setup. those of you that noticed some kind of benefit to changing ports or mice were probably just noticing it in a higher fps area.

so be on the lookout for any updates to hardware cursor capability, or overall improvements in d3d support.
What I don't understand yet is why hardware cursors don't work.

---

### Post by Tantalus90 on 2007-03-12
Dunno if its much use but here it is anyway 

> December 22, 2006: Wine 0.9.28 Released

    Wine 0.9.28 was released today, with the following main changes:

        * OpenGL in child windows should work again.
        *** Better mouse support in games.**
        * Beginnings of new state management in Direct3D.
        * Improved audio and font support on Mac OS.
        * Lots of bug fixes.


from [http://winehq.org/](http://winehq.org/)

Couple more updates have been released since then , what ver of wine is everyone using ?

---

### Post by Sizzler on 2007-03-14
The version of wine I currently have is wine-0.9.32 
I bought a new Logitech G5 laser mouse hoping it would improve the situation but it didn't :(

---

### Post by Aramil Moonmist on 2007-03-17
bump

this is the one reason i need windows on my computer still, anyone figure it out?

---

### Post by lou1998 on 2007-03-20
I have a similar problem while using a wireless mouse.  When I use a regular mouse, it works much better.  No noticable lag.

---

### Post by jcam7044 on 2007-03-22
I had this problem aswell so I disabled beryl-manager from startup and now my mouse is working great.    Hope that helps

---

### Post by csb on 2007-03-25
I've been experiencing the same issue... even without Beryl running.

I also use a wireless mouse, but the computer doesn't know that... as far as the computer is concerned, it's just a USB mouse.  So, I wonder if this is perhaps something USB related??  I'm going to try a PS2 mouse and see if that changes anything and will post my results next time I play.

Also, the mouse problem seems to be intermittent... the mouse will track and function normally for 5 seconds, then not react for 3 seconds, then it will work for 8 seconds, then not for 1 sec.  There doesn't seem to be any set time intervals, but there's definitely a cycle.

---

### Post by konungursvia on 2007-03-25
Tab targeting is the way to go anyway, all the real hard core players use it pretty much exclusively. If I remember correctly, I had a problem like this in Win but there was an option in Wow's interface options that allowed hardware or software management of the mouse. I think. Just go in and play with those options and it may improve.

---

### Post by csb on 2007-03-25
Yeah, TAB targeting is definitely the way to go... along with about 300 other useful keyboard shortcuts.  

BUT... the problem with the mouse is more of a pain the **** when NOT in battle... like when trying to sell items in the Auction House, for example.  It's also a pain in the rear in group quests when the entire group is waiting for loot and it takes 10 seconds to loot a corpse because the mouse doesn't want to play nice.

I'm actually playing right now, but using a PS/2 mouse this time and it's much better.  I think the problem might have to do with how WINE uses USB.  I'm willing to bet that most USB mice (wireless or otherwise) would probably experience this problem.  PS/2 seems to work like a champ.

---

### Post by Aramil Moonmist on 2007-03-31
unfortunately for those of us with laptops, that may not be an option.

as for the hardware option konungursvia, that box is grayed out, and im pretty sure if i could check it, it would solve the mouse lag (i know it did for me in windows)

beryl isnt running either

---

### Post by Majorix on 2007-03-31
Use Cedega? Why use wine for gaming when there is a gaming counterpart of it?

---

### Post by Aramil Moonmist on 2007-04-02
because im cheap

---

### Post by Wiebelhaus on 2007-04-05
> **Aramil Moonmist said:**
> because im cheap

lmao..

---

### Post by ArtificialSynapse on 2007-04-05
> **NICU28 said:**
> I had this problem when running WoW in Direct3D mode instead of openGL.  You can add the extra lines in your config.wtf file to always run in OpenGL with 
```
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"
```
I've been having problems changing my video settings in OpenGL so I use -d3d instead of -opengl to change configurations.

They have a prog out that allows you to change your settings in openGL now, I forget what it's called, it's under the main WOW installation howto.

---

### Post by Wiebelhaus on 2007-04-05
> **ArtificialSynapse said:**
> They have a prog out that allows you to change your settings in openGL now, I forget what it's called, it's under the main WOW installation howto.


Does this allow you to enable hardware cursor/mouse in wow interface?

---

### Post by sirhalos on 2007-04-06
The slow mouse problem has to do with OpenGL you are unable to select Hardware Mouse. That is the problem Hardware Mouse is not supported in OpenGL the only way to get around it is lower your resolution down to the point your mouse is fast. In DirectX mode you can select Hardware mouse and your mouse will be fast. But I found that there is some kind of memory leak in DirectX mode with Cedega that when you move the mouse you get 0 FPS completely. The way to fix it though is unselect Hardware Mouse, click OK then select Hardware Mouse again and click OK.

---

### Post by sirhalos on 2007-04-06
And also by the way you can not use Hardware Cursor in Windows running in OpenGL either. This is NOT a WINE problem it is a problem with Warcraft in OpenGL mode.

---

### Post by Aramil Moonmist on 2007-04-09
so basically now the idea is to yell at blizz till they make a fix. although im surprised they havent already, in my experience theyre very good at details like this.

---

### Post by AndrewRiedi on 2007-04-09
I recently got some basic 32-bit cursor support into wine.  I have a completed hardware cursor patch that should fix this issue, so long as you can run WoW in D3D mode.  It will, however, take me some time to get this patch into wine as I need to write some tests and implement some legacy 32-bit cursor support for people without the Xcursor library first.  Anyhow, know that the issue is known, and that I am working on it.

Cheers!

---

### Post by Sammi on 2007-04-10
> **AndrewRiedi said:**
> I recently got some basic 32-bit cursor support into wine.  I have a completed hardware cursor patch that should fix this issue, so long as you can run WoW in D3D mode.  It will, however, take me some time to get this patch into wine as I need to write some tests and implement some legacy 32-bit cursor support for people without the Xcursor library first.  Anyhow, know that the issue is known, and that I am working on it.

Cheers!That's exactly what people want to hear. Please just don't let them down after giving them a half promise.

---

### Post by Jovec on 2007-04-10
Any of you with this mouse lag running numerous Ace2 addons?

---

### Post by Aramil Moonmist on 2007-04-21
finally gave in and tried cedega... it wouldnt even let me install wow, let alone play it with a nice cursor

---

### Post by AndrewRiedi on 2007-04-21
Guys, I have a working hardware cursor patch for D3D mode if you want it.  Only thing is, you will have to compile Wine from source to use the patch, unless one of you puts up a .deb somewhere for you all to use.  I am working on getting it in to Wine still, but I need to talk to some coders to figure out the correct method to get it accepted.  I need to first implement 32-bit legacy cursor support (for those without Xcursor).  Then I need to write a test program.  Finally, I can make last minute changes to the patch and send it in.   That said, all Ubuntu users should have Xcursor installed, and my hardware cursor patch will work juts fine for all you folks.

---

### Post by Sammi on 2007-04-21
> **AndrewRiedi said:**
> Guys, I have a working hardware cursor patch for D3D mode if you want it.  Only thing is, you will have to compile Wine from source to use the patch, unless one of you puts up a .deb somewhere for you all to use.  I am working on getting it in to Wine still, but I need to talk to some coders to figure out the correct method to get it accepted.  I need to first implement 32-bit legacy cursor support (for those without Xcursor).  Then I need to write a test program.  Finally, I can make last minute changes to the patch and send it in.   That said, all Ubuntu users should have Xcursor installed, and my hardware cursor patch will work juts fine for all you folks.
Great news :D

You should give us a link to the patch and instructions on how to compile Wine with it, then the community would be able to test this little thing of yours.

---

### Post by Stormweaver on 2007-04-23
This is most likely because I am stupid and new to linux, but why can't we run WoW in Direct X mode??  If the issue of bad mousing is limited to Open GL, whats wrong with going with the mode that works??

---

### Post by Aramil Moonmist on 2007-04-23
> **AndrewRiedi said:**
> Guys, I have a working hardware cursor patch for D3D mode if you want it.  Only thing is, you will have to compile Wine from source to use the patch, unless one of you puts up a .deb somewhere for you all to use.  I am working on getting it in to Wine still, but I need to talk to some coders to figure out the correct method to get it accepted.  I need to first implement 32-bit legacy cursor support (for those without Xcursor).  Then I need to write a test program.  Finally, I can make last minute changes to the patch and send it in.   That said, all Ubuntu users should have Xcursor installed, and my hardware cursor patch will work juts fine for all you folks.

Sweet, thanks man.  i dont suppose we could get a fix for open gl also? ; P

as for stormweaver. im not altogether clear on this myself, but as i understand it, d3d is a part of direct x, and open gl is the competitor to that
[http://en.wikipedia.org/wiki/DirectX](http://en.wikipedia.org/wiki/DirectX)

---

### Post by AndrewRiedi on 2007-04-23
> **Stormweaver said:**
> This is most likely because I am stupid and new to linux, but why can't we run WoW in Direct X mode??  If the issue of bad mousing is limited to Open GL, whats wrong with going with the mode that works??

Direct3D mode will eventually have a Hardware Cursor (once my patch is accepted).  However, D3D mode is currently slower than OpenGL mode.  Because the Blizzard programmers don't know how to create a hardware cursor with OpenGL (it is not as easy, as OpenGL itself doesn't do anything with cursors.  However, that doesn't make it impossible, just much harder.), there is no way to create an OpenGL hardware cursor.

This said, try testing WoW in D3D mode, if it runs well enough for you, and you want a hardware cursor, just let me know and I will post my patch here.  Of course, you will then have to get someone to explain to you how to compile programs under Ubuntu.  (ie. what packages to install and whatnot) because I do not use Ubuntu.

Update on the patch:  I have written a 32-bit legacy cursor patch (step 1 in getting the hardware cursor patch into Wine, but won't directly affect any of you folk), but I need to have a specific person take a look at it, and he hasn't had time yet.  I will then have to make a D3D testcase and run it under Windows.  (This is the hardest part left.)  Then I can do some last minute fixes and send it in with my hardware cursor patch for D3D.  However, I don't have a lot of time to fool with this stuff, so it may not make it in for a while still.

PS:  Let me know if you want the patch posted here.

---

### Post by Stormweaver on 2007-04-23
Then if I was running in Direct X on windows, does that mean I would run in D3D the same way? I mean I'm learning here... Teach me all you can!

---

### Post by AndrewRiedi on 2007-04-24
D3D mode is the default mode for WoW, in Linux or Windows.  Use the -opengl switch for OpenGL.

---

### Post by Stormweaver on 2007-04-24
So which one is the cause of the slow or lazy cursor?  Cause I am having the same issues and if I can resolve by switching modes well then ya know :)

---

### Post by AndrewRiedi on 2007-04-24
Currently you will get a slow (software) cursor in both Direct3D and OpenGL in Wine.  Like I said, if you know how to compile Wine, I will give you my hardware cursor patch for D3D, just let me know.  I haven't been able to get in touch with someone who I want to look at some of my pre-requisite code yet.  (32-bit legacy cursor support.)  I also still have to write a test case before getting the patch into Wine.  This said, the patch works just fine and will work for Ubuntu users because they all have the Xcursor lib. installed.

---

### Post by Stormweaver on 2007-04-25
I am less then 2 weeks old in my Linux life.... Which means unless we can find someone on the forums to help write up a how to on doing this, I will have to wait.  I reconfiged a bunch of my C's to use their combat skills on the keyboard today so that I only really have to fiddle with the mouse in between, but still waiting 10 seconds to click an item is kicking my tail, and even got me booted from a group tonight for dragging feet, even though I told them what was up.  So I hope that the guy you need to look at this patch gets time soon, cause I and many others I am sure would love to see this thing fixed.


Stormweaver

---

### Post by AndrewRiedi on 2007-04-25
I will try to get it in as soon as I can, but I don't think I can get it into 0.9.36.  Anyhow, I might install Ubuntu on my brother's computer.  If I decide to, and I figure out how to get the build environment set up, I can write a howto.  Otherwise, I hope someone else can post on how to do it.

---

### Post by foug on 2007-04-25
I have the same mouse lag in opengl. But it seems I get less lag when my FPS goes up really high (60-100+). I too also get the error (SPI_SETMOUSESPEED)

---

### Post by Aramil Moonmist on 2007-04-25
andrew, could you post a link to the code for me? id like to test it out myself.

---

### Post by AndrewRiedi on 2007-04-25
> **Aramil Moonmist said:**
> andrew, could you post a link to the code for me? id like to test it out myself.

[Here]("http://www.google.com/base/a/1064814/D14612295624945758443") it is.  There are two patches there, one for wine-0.9.35, and one for wine-git.

---

### Post by Coilcore on 2007-04-30
Either I have a different problem or I'm not sure that the software cursor is the problem everyone is having.  I'm guessing a problem in a software cursor would mean a that the drag would be slow; you move the mouse and its like watching a freeze frame of the cursor move.

The problem is that the mouse-overs don't seem to trigger frequently or if they do they are very delayed (seems upwards of 2-3 seconds).     This requires moving the mouse over a button or an icon, noting that it its not 'backlit' then moving the mouse elsewhere then back on until the button is lit.  

I have a very high frame-rate, running at 1280x1024 on a Core2duo 2.4Gz, 2MB, and 7600gt Nvidia.  The game moves smoothly AND the cursor movement is smooth.  System is not taxed at all.  Tried with a modified UI (lots of Ace2 pluggins) and once with the clean Blizzard UI - same thing.

I guess this could still be the gl hardware cursor problem, but I wanted to make sure.  Because if its just some mouse-sensitivity setting in Wine that I'm missing that would be great.

---

### Post by Sammi on 2007-04-30
There's also one big thing about this error that I haven't understood yet:

What is the difference between the set up of a user who does and one who doesn't experience this problem?

---

### Post by slayerboy on 2007-04-30
Coming late into this topic, I have not had ANY problems with the mouse.  however, I have noticed that the lower the resolution, the "snappier" the mouse seems.  I have WoW running at the same resolution as my setup, which I beleive is at 1280x960 (native monitor resolution).  If I lower the WoW resolution, I notice the mouse is a little quicker, but if WoW somehow crashes, X stays in the lower resoultion (say 800x600) and I have to either manually change the resolution or restart X.  I also noticed that having a USB mouse was actually a little slower.  I do know that it's NOT advisable to have a mouse/keyboard plugged into a USB hub if they are USB.  PS/2 is the better way, for most people there is NO difference, and it allows 2 USB ports to be free.

Not saying this is the issue, but thought I'd offer my input.

AMD Sempron 2.0Ghz
1GB Ram / 2GB swap space
Nvidia Geforce 6200 256MB
250GB IDE HDD / 80GB IDE HDD
19" Hanns-G LCD Monitor @ 1280x960 native resolution
PS/2 keyboard
PS/2 Kennsington Optical Mouse
XFCE w/ Gnome/KDE support
Running WoW w/ Wine using AOSS

---

### Post by AndrewRiedi on 2007-04-30
Hardware cursors basically just make your mouse instantly snappy.

Update on HW cursor support in Wine:  I got my legacy cursor patch in.  :)  I need to write tests now to figure out Windows' behavior in a very specific area of my code to make sure I am doing the right thing.  The patches posted above should still work.

---

### Post by Jovec on 2007-05-01
> **Coilcore said:**
> Either I have a different problem or I'm not sure that the software cursor is the problem everyone is having.  I'm guessing a problem in a software cursor would mean a that the drag would be slow; you move the mouse and its like watching a freeze frame of the cursor move.

The problem is that the mouse-overs don't seem to trigger frequently or if they do they are very delayed (seems upwards of 2-3 seconds).     This requires moving the mouse over a button or an icon, noting that it its not 'backlit' then moving the mouse elsewhere then back on until the button is lit.  

I have a very high frame-rate, running at 1280x1024 on a Core2duo 2.4Gz, 2MB, and 7600gt Nvidia.  The game moves smoothly AND the cursor movement is smooth.  System is not taxed at all.  Tried with a modified UI (lots of Ace2 pluggins) and once with the clean Blizzard UI - same thing.

I guess this could still be the gl hardware cursor problem, but I wanted to make sure.  Because if its just some mouse-sensitivity setting in Wine that I'm missing that would be great.

I experienced this same behavior

If you are using a bunch of Ace2 addons try downloading the no-ext versions (that don't include the embeded libraries) and manually installing the necessary libraries you need.  As an example, the following are the libraries I need to meet my dependencies (for my 51 Ace2 addons) for the no-ext versions, otherwise, I'd have literally dozens and dozens of copies of the below libraries as every released Ace2 addon includes a copy of the libraries it needs.

```
#Dependencies and Libraries
wget http://files.wowace.com/AbacusLib/no-ext/AbacusLib.zip
wget http://files.wowace.com/Ace2/no-ext/Ace2.zip
wget http://files.wowace.com/AnchorsAway/no-ext/AnchorsAway.zip
wget http://files.wowace.com/Babble-2.2/no-ext/Babble-2.2.zip
wget http://files.wowace.com/BanzaiLib/no-ext/BanzaiLib.zip
wget http://files.wowace.com/CandyBar/no-ext/CandyBar.zip
wget http://files.wowace.com/CrayonLib/no-ext/CrayonLib.zip
wget http://files.wowace.com/Deformat/no-ext/Deformat.zip
wget http://files.wowace.com/DewdropLib/no-ext/DewdropLib.zip
wget http://files.wowace.com/FuBarPlugin-2.0/no-ext/FuBarPlugin-2.0.zip
wget http://files.wowace.com/GloryLib/no-ext/GloryLib.zip
wget http://files.wowace.com/GratuityLib/no-ext/GratuityLib.zip
wget http://files.wowace.com/InFlight_Load/no-ext/InFlight_Load.zip
wget http://files.wowace.com/ItemBonusLib/no-ext/ItemBonusLib.zip
wget http://files.wowace.com/JostleLib/no-ext/JostleLib.zip
wget http://files.wowace.com/Metrognome/no-ext/Metrognome.zip
wget http://files.wowace.com/PaintChipsLib/no-ext/PaintChipsLib.zip
wget http://files.wowace.com/ParserLib/no-ext/ParserLib.zip
wget http://files.wowace.com/PeriodicTable-3.0/no-ext/PeriodicTabe-3.0.zip
wget http://files.wowace.com/Quixote/no-ext/Quixote.zip
wget http://files.wowace.com/RollCall-1.0/no-ext/RollCall-1.0.zip
wget http://files.wowace.com/RosterLib/no-ext/RosterLib.zip
wget http://files.wowace.com/SharedMediaLib/no-ext/SharedMediaLib.zip
wget http://files.wowace.com/SpecialEventsEmbed/no-ext/SpecialEventsEmbed.zip
wget http://files.wowace.com/SurfaceLib/no-ext/SurfaceLib.zip
wget http://files.wowace.com/TabletLib/no-ext/TabletLib.zip
wget http://files.wowace.com/TouristLib/no-ext/TouristLib.zip
wget http://files.wowace.com/Waterfall-1.0/no-ext/Waterfall-1.0.zip

```

A tar.bz2 of my Addons dir went from 45MB to 4MB  once I made this change.

---

### Post by sk8dork on 2007-05-01
one good way to test and see if your problem is like everyone elses (software cursor is slow, hardware cursor is not an option) is to go to a big city and see how responsive your cursor is. also, press ctrl+r to note your framerate. most likely your framerate will go down and so will the speed that your cursor updates in its movement (slow = choppy). now go to a place where there are little to no mobs or anything in front of you. sometimes this will work when you look straight up or straight down, and i have found that i get upwards of 100fps (the most i ever get in game) while i am down the stairs on the first landing of the sepulcher (horde). look straight at the wall, there is nothing for the game to draw beyond that point, no maps, no characters, no nothing, so framerate goes sky high. now if your cursor is very quick and smooth, you are experiencing the same issue as everyone else who does not have a hardware cursor. hardware cursor has nothing to do with your actual mouse or the interface (ps/2 - usb). hardware cursor just means that the actual computer hardware, most likely the graphics card, is creating the cursor. software cursor means that the software is creating the cursor, most likely wow or wine.

another way to see the difference is to get on a slow windows machine that can play wow, but not with very good fps. i played on a friend's machine that typically got 15fps. omg that is slow, but since it was windows and was using d3d by default, hardware cursor was available, and the game was still playable. if i told the game to run in opengl or just disabled the hardware cursor then i'd get the same issue that we get in linux.

is this d3d hw cursor patch going to be in a future release of wine? is it in already? i have tried d3d in the past, but some things video optionsreally make it go crazy. i am wiling to turn down all settings to get a hardware cursor. personally i can deal with low fps in game graphics if the cursor is lightning fast and responsive. if you need more testing before it can get into wine then i'd be glad to help.

edit: i also have experienced the small problem of mouse clicks not registering. i have done a bit to see what the issue was, and it appears to be that if you move the cursor slowly it won't behave properly, but if you move it quickly it will. you can test this by dragging the size of a chat window. dragging slowly won't make it move, but dragging it quickly will. i don't know if a hardware cursor will help this or not. i think i may have noticed similar behavior in other apps in wine (flstudio) but i'm not sure. flstudio is probably using a software cursor anyway.

---

### Post by SKLP on 2007-05-01
> **AndrewRiedi said:**
> Hardware cursors basically just make your mouse instantly snappy.

Update on HW cursor support in Wine:  I got my legacy cursor patch in.  :)  I need to write tests now to figure out Windows' behavior in a very specific area of my code to make sure I am doing the right thing.  The patches posted above should still work.
Good work :D

However, until Wine D3D is optimized OpenGL mode will offer higher FPS :/
So I was thinking, it should be possible to make a hack that basically forces the normal X cursor to be drawn above the wow window. (Or am I wrong here? :P)
Anyway, this could be a nice hack if its easy to implement...


ciao

---

### Post by sk8dork on 2007-05-01
> **SKLP said:**
> Hw cursor is grayed out in opengl mode even if you are running it in windows, it's probably disabled since the OpenGL mode is not meant to be used (except for the Mac version of the game, and it works there)

opengl hw cursor in mac?? jerks!

---

### Post by AndrewRiedi on 2007-05-01
> **sk8dork said:**
> is this d3d hw cursor patch going to be in a future release of wine? is it in already? i have tried d3d in the past, but some things video optionsreally make it go crazy. i am wiling to turn down all settings to get a hardware cursor. personally i can deal with low fps in game graphics if the cursor is lightning fast and responsive. if you need more testing before it can get into wine then i'd be glad to help.

The HW cursor patch is not in Wine currently, but I am working to get it into Wine.  It will be in some future release, but I don't know which one because I don't know exactly how much work I have left.  I can, however, say that I will keep trying until it gets in.  :)

---

### Post by AndrewRiedi on 2007-05-01
> **sk8dork said:**
> opengl hw cursor in mac?? jerks!

Could email Blizzard and tell them that you would enjoy an OpenGL HW cursor.

---

### Post by AndrewRiedi on 2007-05-01
> **SKLP said:**
> Good work :D

However, until Wine D3D is optimized OpenGL mode will offer higher FPS :/
So I was thinking, it should be possible to make a hack that basically forces the normal X cursor to be drawn above the wow window. (Or am I wrong here? :P)
Anyway, this could be a nice hack if its easy to implement...

Thanks.  :)  You know how to compile Wine from source?  I could implement such a hack in 5 mins., but kind of pointless if you can't compile it, as it will have zero change of getting into the main Wine tree.  Anyhow, if you can compile from source I can implement it and post it online for you to download and use.  One thing though, the regular software cursor will still be drawn, so you will have the infamous double cursor problem from D3D, but in OpenGL.

---

### Post by sk8dork on 2007-05-01
ok, i uninstalled wine and compiled it from the source after aplying your patch. it looks promisnig, as the cursor is definitely snappy, but one small(large) problem is that the cursor disappears in travel. that is, i can see it if i'm sitting still, but when i move it smoothly it disappears until the moment i either slow down or stop. moving it slowly has the same effect, except your movements slow down enough that it stops and appears for a fraction of a second. i might note that the unresponsiveness described in one of my previous posts is gone. moving slowly fastly or anything wil lhighlight buttons the instance my cursor goes over them. 

so, if it can be improved to always show the cursor then it would be perfect (for running in d3d) but in the meanwhile the ol double cursor glitch would help greatly in this case.

---

### Post by sk8dork on 2007-05-01
additional notes: the amount of time you get to see the cursor while moving it seems to be dependent on the framerate. while i'm in an area that is getting around 30 or less, the cursor flashes in more and i can see it better. when i'm getting 50+ fps i absolutely can't catch a glimpse of the cursor as i move it, only when stopped. i hope this makes sense. i could take a video of it if necessary. also of note: i turned all graphical settings and extras off/down and restarted the game, didn't affect anything regarding the cursor.

---

### Post by AndrewRiedi on 2007-05-02
Thanks for the reply, information, and testing sk8dork!  If you want me whip up a patch to keep the hardware cursor always drawn (so you don't have to have the dual cursor thing) just let me know.

The issue about the cursor not appearing when it needs to I will investigate more.  I have two ideas about what it might be.  One of them is related to the code I need to make a test for, and the other idea is about some other part of Wine unrelated to my patch.  I will eventually fix it either way.

---

### Post by sk8dork on 2007-05-02
> **AndrewRiedi said:**
> Thanks for the reply, information, and testing sk8dork!  If you want me whip up a patch to keep the hardware cursor always drawn (so you don't have to have the dual cursor thing) just let me know.

The issue about the cursor not appearing when it needs to I will investigate more.  I have two ideas about what it might be.  One of them is related to the code I need to make a test for, and the other idea is about some other part of Wine unrelated to my patch.  I will eventually fix it either way.

awesome. keep us posted on the status of the fix. if you could whip up that other patch i'd appreciate it. thanks a lot, andrew.

btw, as it currently stands d3d isn't terribly bad to play in, from my experience. i have noticed that some things look a little glitchy (i.e. frost traps on the ground after they've been triggered), and whenever you approach an area where the game has to load something, i don't know if it's characters or npcs or other parts of the map, it drops down to about 5-6 fps, but then recovers. the great part about the hw cursor is that it's not affected much by the drop in fps (other than the drawing issue i noted above).

---

### Post by SKLP on 2007-05-02
> **AndrewRiedi said:**
> Thanks.  :)  You know how to compile Wine from source?  I could implement such a hack in 5 mins., but kind of pointless if you can't compile it, as it will have zero change of getting into the main Wine tree.  Anyhow, if you can compile from source I can implement it and post it online for you to download and use.  One thing though, the regular software cursor will still be drawn, so you will have the infamous double cursor problem from D3D, but in OpenGL.
Yeah I know how to compile wine; in fact i was the original author of the Ubuntu WorldofWarcraft in wine howto ;-)
About the patch, it would be very nice to have that implemented :)

thx for ur work

---

### Post by AndrewRiedi on 2007-05-02
**sk8dork** and **SKLP**:

I posted a patch [here]("http://base.google.com/base/a/1064814/D14612295624945758443") for you guys.  It should satisfy both of your needs.

---

### Post by SKLP on 2007-05-03
> **AndrewRiedi said:**
> **sk8dork** and **SKLP**:

I posted a patch [here]("http://base.google.com/base/a/1064814/D14612295624945758443") for you guys.  It should satisfy both of your needs.
will d3d-hack.patch.txt cause the normal cursor to not hide itself while in opengl mode?

---

### Post by sk8dork on 2007-05-03
i extracted the txt files from both zips into the wine 9.36 source directory, successfully patched the main patch and then patched with the d3d hack patch, configured, make depend and maked, sudo checkinstalled, and it appears to be the same as before. ideas?

by the way, when i tested out the cursor disappearing thing again i think i can better describe it like this: when the framerate is really low, around 3-6fps, the cursor is almost perfect, never disappearing as far as i can tell, and responsive as all hell, but as the framerate increases the cursor starts disappearing when moving. i think the cursor disappears whenever a frame is drawn and the cursor is in movement.

---

### Post by AndrewRiedi on 2007-05-03
> **SKLP said:**
> will d3d-hack.patch.txt cause the normal cursor to not hide itself while in opengl mode?

The patch makes no changes to OpenGL mode.

---

### Post by AndrewRiedi on 2007-05-03
> **sk8dork said:**
> i extracted the txt files from both zips into the wine 9.36 source directory, successfully patched the main patch and then patched with the d3d hack patch, configured, make depend and maked, sudo checkinstalled, and it appears to be the same as before. ideas?

by the way, when i tested out the cursor disappearing thing again i think i can better describe it like this: when the framerate is really low, around 3-6fps, the cursor is almost perfect, never disappearing as far as i can tell, and responsive as all hell, but as the framerate increases the cursor starts disappearing when moving. i think the cursor disappears whenever a frame is drawn and the cursor is in movement.

Hmm.. It still gives you the same problem?  Did you try maybe right clicking to turn your char (since it should disappear if you do that normally, but with the patch it shouldn't.)?

---

### Post by sk8dork on 2007-05-03
> **AndrewRiedi said:**
> Hmm.. It still gives you the same problem?  Did you try maybe right clicking to turn your char (since it should disappear if you do that normally, but with the patch it shouldn't.)?

i can left click, right click, etc. and the cursor will always show up (we're talking about the wow glove cursor, not the ubuntu arrow cursor). the wow cursor is always there except for when it is in movement. while i move it from one place to the other it will disappear. with higher framerates the cursor is 'more disappeared' (no opacity changes, sorry if this is confusing) but with a low framerate the cursor is almost always visible. the ubuntu arrow cursor is never there. if necessary i will film the problem tonight.

edit: let's see if i can better explain what i think is happening. let's say i am getting 60fps. while the cursor is sitting still i can see it fine. when i move the cursor it will not be visible for 60 frames in a second. that is to say it will disappear 60 times in a second, once for each frame per second i am getting. so if i move my cursor at all it seems like it's just gone, regardless of the speed that i move it. now let's say i'm getting 3fps. the cursor will be perfectly visible when it is sitting still. when i move the cursor it will only disappear for 3 frames per second, giving the appearance that it never disappears. that is to say that in one second of time it will only disappear 3 times, each fram that it 'drops' is practically unnoticable. so with 3fps i can move my cursor with lightning speed and precision and it will be there every step of the way, while the rest of my graphics lag.

---

### Post by AndrewRiedi on 2007-05-04
Weird stuff sk8dork.  So the hack doesn't help you then I guess but did exactly what I expected it to do.  What Gfx card do you have?  What drivers version?  I would bet it might be a bug in the drivers, although I could be wrong.  In any case, I will fix this somehow, just have to figure out what is wrong first.  :)

---

### Post by shaner12 on 2007-05-05
i dont know if this has been answered or not, but is there some way for me to remove my regular ubuntu cursor?  i dont have any problems with my wow one going slowly, its just that i see both at once and its kind of annoying. any ideas?

---

### Post by AndrewRiedi on 2007-05-05
> **shaner12 said:**
> i dont know if this has been answered or not, but is there some way for me to remove my regular ubuntu cursor? i dont have any problems with my wow one going slowly, its just that i see both at once and its kind of annoying. any ideas?

Here are a few options:

1) Play in OpenGL mode.  ( wine "c:\Program Files\World of Warcraft\WoW.exe" -opengl )
2) Use my hardware cursor patch above and recompile Wine with it.
3) Wait a couple months until I can get around to fixing the problem and getting the code integrated into the main Wine source tree.

---

### Post by AndrewRiedi on 2007-05-16
> **AndrewRiedi said:**
> I recently got some basic 32-bit cursor support into wine.  I have a completed hardware cursor patch that should fix this issue, so long as you can run WoW in D3D mode.  It will, however, take me some time to get this patch into wine as I need to write some tests and implement some legacy 32-bit cursor support for people without the Xcursor library first.  Anyhow, know that the issue is known, and that I am working on it.

Cheers!

> **Sammi said:**
> That's exactly what people want to hear. Please just don't let them down after giving them a half promise.

D3D hardware cursor patch was accepted into Wine Git this mourning.  It will be in Wine-0.9.38.

---

### Post by AndrewRiedi on 2007-05-16
> **sk8dork said:**
> i can left click, right click, etc. and the cursor will always show up (we're talking about the wow glove cursor, not the ubuntu arrow cursor). the wow cursor is always there except for when it is in movement. while i move it from one place to the other it will disappear. with higher framerates the cursor is 'more disappeared' (no opacity changes, sorry if this is confusing) but with a low framerate the cursor is almost always visible. the ubuntu arrow cursor is never there. if necessary i will film the problem tonight.

edit: let's see if i can better explain what i think is happening. let's say i am getting 60fps. while the cursor is sitting still i can see it fine. when i move the cursor it will not be visible for 60 frames in a second. that is to say it will disappear 60 times in a second, once for each frame per second i am getting. so if i move my cursor at all it seems like it's just gone, regardless of the speed that i move it. now let's say i'm getting 3fps. the cursor will be perfectly visible when it is sitting still. when i move the cursor it will only disappear for 3 frames per second, giving the appearance that it never disappears. that is to say that in one second of time it will only disappear 3 times, each fram that it 'drops' is practically unnoticable. so with 3fps i can move my cursor with lightning speed and precision and it will be there every step of the way, while the rest of my graphics lag.

I am still looking into this very awkward bug.  Is it possible to test with current Git?

---

### Post by sk8dork on 2007-05-16
> **AndrewRiedi said:**
> I am still looking into this very awkward bug.  Is it possible to test with current Git?

the latest test was with current git, at the time. if you have an updated patch for the newest git then i can try it again.

---

### Post by AndrewRiedi on 2007-05-16
> **sk8dork said:**
> the latest test was with current git, at the time. if you have an updated patch for the newest git then i can try it again.

The latest patch it *in* current git.  No need to apply it.  I made one or two minor changes to it before it got in.  I just want to make sure that I am working with a bug that still exists.  Anything I could do to reproduce it on another computer would be good too.  If not, well, I will still find a way to fix it, but it will be more difficult.

---

### Post by Nehvrook on 2007-05-17
Edit

---

### Post by Sammi on 2007-05-17
> **AndrewRiedi said:**
> D3D hardware cursor patch was accepted into Wine Git this mourning.  It will be in Wine-0.9.38.
You are fantastic :D

---

### Post by sk8dork on 2007-05-17
> **Sammi said:**
> You are fantastic :D

i don't know how i missed the 'will be in .9.38.' post.
i will try to check this out soon and will report back with my results.

---

### Post by AndrewRiedi on 2007-05-18
Ok, I believe I understand **sk8dork**'s cursor issue now.  I will see if I can find a quick hack for the mean time to get it working properly for those of you that have it while I see if I can design a proper fix.  I do, however, have some homework this weekend so I probably won't have it complete for a while.  I will post back here with the hack when I complete it.

On a real design, I am thinking I might just wait until I can move some of the cursor code into wineserver.  This would allow me to do all sorts of things and fix some nasty bugs like this one in a more proper way.  However, doing this will require a lot of work and time, so don't expect anything any time soon.  I will probably work on my animated cursor stuff (which also will take a lot of time) before I do the move into the wineserver.

---

### Post by sk8dork on 2007-05-20
> **AndrewRiedi said:**
> Ok, I believe I understand **sk8dork**'s cursor issue now.  I will see if I can find a quick hack for the mean time to get it working properly for those of you that have it while I see if I can design a proper fix.  I do, however, have some homework this weekend so I probably won't have it complete for a while.  I will post back here with the hack when I complete it.

On a real design, I am thinking I might just wait until I can move some of the cursor code into wineserver.  This would allow me to do all sorts of things and fix some nasty bugs like this one in a more proper way.  However, doing this will require a lot of work and time, so don't expect anything any time soon.  I will probably work on my animated cursor stuff (which also will take a lot of time) before I do the move into the wineserver.

cool, let us know when you've got something. i haven't tried latest git mainly because i've never used 'git' before. i'll try to give it a shot if you still think i should.

---

### Post by AndrewRiedi on 2007-06-01
Wine 0.9.38 was released minutes ago.  There should be builds pretty soon.  This release has my hardware cursor patch in it.  I still haven't gotten time to come up with a quick fix for your problem yet.  Have lots of school stuff.  :-|

---

### Post by sk8dork on 2007-06-02
just upgraded to 9.38. d3d seems to be a lot better, but alas still have the cursor problem (does not draw at high framerates, 40-50+)

edit: here's a video clip. sorry for the flicker, recorded with a vid cam at 1/60 shutterspeed.
[http://www.sk8dork.com/files/misc/d3dhardwarecursorwow.tar.gz](http://www.sk8dork.com/files/misc/d3dhardwarecursorwow.tar.gz)

---

### Post by AndrewRiedi on 2007-06-02
Just posted a patch [here.]("http://www.google.com/base/a/1064814/D14612295624945758443")  It is called, "0003-wined3d-Fix-D3D-HW-cursor-blinking-bug.txt".  Do you think you could test it for me?  Thanks :)

EDIT:  Just posted yet another potential fix here.  Also, this post is mainly directed at **sk8dork**, but anyone having this problem is free to test the patches and report if they work.  I would be thankful to know if they work or not.  :)

---

### Post by sk8dork on 2007-06-02
tried both patches, didn't work with either of them. i compiled with the latest available source file from the wine sourceforge site (9.38). same problem. but here's something new, i think...with the last patch (0004) i started up wine and can tell right away that it didn't work, cuz with the high fps at the login screen my cursor was disappearing in movement, and for some reason i decided to run winemine while wow was up at the login screen, and over winemine i see the wow cursor...and it stays constantly, no disappearing. when moving the cursor over into wow i get the problem again. did you watch the video i posted in my post on the bottom of the previous page? it appears that whenever frames are being drawn in wow it won't draw the cursor...or something. i really have no idea. i am really surprised that no one else is experiencing the issue i'm having. the hardware cursor d3d support is in wine now, people need to test by running wow in -d3d mode.

---

### Post by AndrewRiedi on 2007-06-02
> **sk8dork said:**
> tried both patches, didn't work with either of them. i compiled with the latest available source file from the wine sourceforge site (9.38). same problem. but here's something new, i think...with the last patch (0004) i started up wine and can tell right away that it didn't work, cuz with the high fps at the login screen my cursor was disappearing in movement, and for some reason i decided to run winemine while wow was up at the login screen, and over winemine i see the wow cursor...and it stays constantly, no disappearing. when moving the cursor over into wow i get the problem again. did you watch the video i posted in my post on the bottom of the previous page? it appears that whenever frames are being drawn in wow it won't draw the cursor...or something. i really have no idea. i am really surprised that no one else is experiencing the issue i'm having. the hardware cursor d3d support is in wine now, people need to test by running wow in -d3d mode.

Thank you for testing the patches.  I looked at the video again.  I will see if I can think up anything else that might solve the problem without some of the major work I was talking about before.

---

### Post by sk8dork on 2007-06-19
wine was updated in the repos again, now it's 0.9.39, still does the same thing. i don't know if this helps or not, but i noticed that if i click on something like a scroll bar or something that requires me to hold the button and drag the cursor will stay constant without flickering at all. could it be that the cursor is not getting the priority that it needs when just moving around screen?

---

### Post by AndrewRiedi on 2007-06-19
> **sk8dork said:**
> wine was updated in the repos again, now it's 0.9.39, still does the same thing. i don't know if this helps or not, but i noticed that if i click on something like a scroll bar or something that requires me to hold the button and drag the cursor will stay constant without flickering at all. could it be that the cursor is not getting the priority that it needs when just moving around screen?

Perhaps.  I am really not quite sure on this.  I am not even sure if it is a Wine problem or an Xorg problem.  Anyhow, I will see what I can come up with when/if I get some time.

---

### Post by downtownkb on 2007-07-11
hey man i just had the same problem for the slow mouse (laggy mouse). go to the device manager.(right click my computer, properties, click the hardware tap, click device manager, go to ur display adapters) and update the driver. it worked for me. hope this helps ya cuz i found it quite bothersome lol. then i went to video options (in game) and u have to enable smoth mouse.

---

### Post by hikaricore on 2007-07-11
> **downtownkb said:**
> hey man i just had the same problem for the slow mouse (laggy mouse). go to the device manager.(right click my computer, properties, click the hardware tap, click device manager, go to ur display adapters) and update the driver. it worked for me. hope this helps ya cuz i found it quite bothersome lol. then i went to video options (in game) and u have to enable smoth mouse.


This is not a Windows support site....

Did you miss the memo?

---

### Post by Sammi on 2007-07-11
First time I've seen that happen on the forum. Downtownkb this is a Ubuntu LINUX forum. Hilarious and cute at the same time :D

---

### Post by drlabel on 2007-08-08
Ppl can any one try this i don't know who to compile WINE
[http://bugs.winehq.org/show_bug.cgi?id=7660](http://bugs.winehq.org/show_bug.cgi?id=7660)

[Patch]("http://bugs.winehq.org/attachment.cgi?id=6764&action=view")

Tks ...

---

### Post by Corvo78 on 2007-08-10
> **Coilcore said:**
> Either I have a different problem or I'm not sure that the software cursor is the problem everyone is having.  I'm guessing a problem in a software cursor would mean a that the drag would be slow; you move the mouse and its like watching a freeze frame of the cursor move.

The problem is that the mouse-overs don't seem to trigger frequently or if they do they are very delayed (seems upwards of 2-3 seconds).     This requires moving the mouse over a button or an icon, noting that it its not 'backlit' then moving the mouse elsewhere then back on until the button is lit.  

I have a very high frame-rate, running at 1280x1024 on a Core2duo 2.4Gz, 2MB, and 7600gt Nvidia.  The game moves smoothly AND the cursor movement is smooth.  System is not taxed at all.  Tried with a modified UI (lots of Ace2 pluggins) and once with the clean Blizzard UI - same thing.

I guess this could still be the gl hardware cursor problem, but I wanted to make sure.  Because if its just some mouse-sensitivity setting in Wine that I'm missing that would be great.

I have the exact same problem... although I am using Crossover 6.1.0.
Some more info: I'm using Ubuntu 7.04 on PC with a GeForce 7800GT, AMD Athlon64 3200+ and 1GB RAM.

Just like Coilcore wrote, is this related to the hardware cursor or not??
I'm still hoping it's some simple setting I missed...

---

### Post by sk8dork on 2007-09-25
latest version of wine and latest patch in wow and i now have smooth hardware cursor with direct3d. so nice.

---

### Post by Dylock on 2007-09-25
my problem was fixed after i added another 1.5g ram to my rig :D

---

### Post by sk8dork on 2007-09-26
> **Dylock said:**
> my problem was fixed after i added another 1.5g ram to my rig :D

i am willing to bet your problem is just 'better'. with no hardware cursor in opengl mode (which is what you're likely using) the problem won't be 'fixed'. with the latest version of wine (and actually also with 9.43, which is what i'm using now) you can get hardware cursor in d3d mode. the feeling of having an ultraresponsive mouse cursor while the game is at 9fps (new bloated outland zones) is great. d3d mode is still too slow compared to opengl though, so i suffer with a software cursor.

one difference i noticed between 9.43 and 9.45 is that somewhere after 9.43 and before or at 9.45 they fixed the unresponsive cursor problem. this problem was the one where if you moved the mouse slowly, like physically dragged it slowly, buttons and things would not respond to the mouse's movement. the problem made resizing chat windows hell, for example. but 9.45 has the crashing on exit bug that 9.43 does not have, so i sit and wait in 9.43.

---

### Post by hikaricore on 2007-09-26
sk8dork: Honestly it depends from system to system for folks based on hardware and other random crap.  I can use D3D mode with no cursor differences from OpenGL mode.  Dylock may be using D3D mode or OpenGL mode, but it's not really up to you to tell them that they are incorrect about which is being used.  Besides starting pointless arguements is my job.

---

### Post by sk8dork on 2007-09-26
hikaricore: heh, not intending to start arguments. =) 
i just want to prevent confusion that the hardware cursor issue is what is being covered here. it appears that as of at least 9.43, d3d hardware cursor works beautifully. there is absolutely no hardware cursor in opengl mode, regardless of what hardware anyone has. can you go to the laggiest (graphically) place you can find in the game, with framerates below 30, and tell me that in opengl mode your cursor does not slow down with the framerate? and in d3d mode, with hardware cursor checked on in the video options, can you do the same and tell me that the cursor stays responsive and quick regardless of framerate? you should also be able to tell specifically during the loading screens, in which the game drops to around 3 fps. you can't really tell the framerate at a loading screen because it doesn't show the number, but in opengl mode your cursor will stick in place for long periods of time (read, 1/3 of a second), while in d3d mode the cursor will be responsive and quick 100% of the time.

increasing your system's specs so that you will get higher fps will surely make your opengl (software accelerated, not hardware) mouse cursor snappier along with the game framerate. 

i am very happy that hardware cursor is present in d3d mode now, but unfortunately d3d still produces lower framerates, at least for me. in some zones the framerate is so low i can't justify using d3d mode just for the hardware cursor.

finally, i didn't mean to tell anyone that they are incorrect over what mode they are using. if anything i want people to use d3d mode to see how far it has come along, and experience true hardware cursor performance, and compare this to their opengl software cursor performance. i long for the day when either d3d is as fast as opengl on a system of my specs, or opengl has hardware cursor.

p.s., your sig PLUR link is broken, it's missing the /wiki/ part. should go here: [http://en.wikipedia.org/wiki/PLUR](http://en.wikipedia.org/wiki/PLUR)

---

### Post by hikaricore on 2007-09-26
> **sk8dork said:**
> p.s., your sig PLUR link is broken, it's missing the /wiki/ part. should go here: [http://en.wikipedia.org/wiki/PLUR](http://en.wikipedia.org/wiki/PLUR)

Actually I ran out of room in my signature.  >.<

So I settled for the 404 forwarding page.  ROFL  :guitar:

---

### Post by zzeus303 on 2008-02-08
Hi,

I still have this laggy mouse in WoW under Ubuntu .
It works with d3d mode but , cant really play in d3d mode because then all other stuff is too slow , except the mouse oO.

Believe if someone would have found a solution, it would had been posted here already, right ?

I wonder if someone noticed any changes in using different hardware ? 
currently i use a logitech mx 310 ...

all input appreciated !!:)

---

### Post by dominicd on 2008-02-20
I seem to have the same problem =(
Any suggestions much appreciated.

---

### Post by Sammi on 2008-02-20
> **dominicd said:**
> I seem to have the same problem =(
Any suggestions much appreciated.If you've read this tread, then you know as much as anybody, as this is the most comprehensive tread on the issue.

---

### Post by dominicd on 2008-02-20
> **Sammi said:**
> If you've read this tread, then you know as much as anybody, as this is the most comprehensive tread on the issue.

I have a short update on my problems.

I went from a crappy D3D and non-working opengl
to a less crappy but still crappy D3D and perfect opengl (with laggy mouse).
Thanks to [http://ubuntuforums.org/showthread.php?t=357112](http://ubuntuforums.org/showthread.php?t=357112)

At this point I figured an update of wine was worth a try (from 9.35 to 9.55)

I gather the mouse-patch is in this version and the upgrade fixed some issues. What it comes down to though is that at this moment I have to choose between opengl with a somewhat laggy mouse or D3D with low FPS. Maybe if I ran WoW in a lower resolution since it's at 1680x1050 atm the FPS will improve but that would still be less than perfect. Since I could run that resolution just perfect in windows with a normal fuctioning mouse =\

---

### Post by dominicd on 2008-02-23
> **SKLP said:**
> The problem is that Hardware Cursor can't be enabled when running wow with the OpenGL mode. And if you use Direct3D mode it won't be playable.
Only solution I know of i either a) use windows b) use cedega+direct3d mode

It sucks I know :(

After many attempts I went for option b) and I want to confirm that it solved my problems 100%. I now have WoW running perfectly. Of course you have to pay, but for those desperate enough to get it working and considering to buy I just want to let you know that in my case it solved my problems.

PS: If you're FPS sucks try running it in full screen mode if you haven't already.

---

### Post by andrewjoy on 2008-03-05
> **AndrewRiedi said:**
> D3D mode is the default mode for WoW, in Linux or Windows.  Use the -opengl switch for OpenGL.

The opengl flag is now deprecated you have to edit the config file in Program Files/World of Warcraft/WTF

and add 

```
SET gxApi "opengl"
```

---

### Post by dcarpenter on 2008-03-09
This is a problem with the World of Warcraft client and not Wine or Ubuntu.  The Mac WoW client, which runs opengl natively, has support for Hardware cursor and the Windows client does not.  There are plenty of threads about this issue on the official WoW forums, so maybe they will finally get around to fixing it.

---

### Post by sadris on 2008-04-14
Anyone else have the issue of--when running in D3D mode--that the terrain textures are missing (grass, roads, etc) since patch 2.4 ?

---

### Post by emshains on 2008-04-14
It is laggy, but I can live (play) with that. The real problem of mine is that when I click on buttons border it sort of gets repetetive, it lags 10-60seconds, nothing bad when your traveling, a gravestone if you are in an instance.

---

### Post by DennisIsAwesome on 2008-07-14
so...no fix?...

---

### Post by Mahinva on 2008-07-15
> **dcarpenter said:**
> This is a problem with the World of Warcraft client and not Wine or Ubuntu.  The Mac WoW client, which runs opengl natively, has support for Hardware cursor and the Windows client does not.  There are plenty of threads about this issue on the official WoW forums, so maybe they will finally get around to fixing it.

This confuses me. The copy of WoW I own is a PC version (I have played WoW on XP since 2005). Currently, I have WoW installed on my Ubuntu partition and my XP partition. If I play WoW on the XP partition, I do have the Hardware Cursor option. In Ubuntu, I do not.

Now, a bit of hopefully logical questions...

1) If a person owned a Mac version of WoW, could they play it on Ubuntu?
2) Would the Mac version of WoW play natively, or would a Wine-like program need to be used?
3) Would the Mac version support Hardware Cursor?
4) Why is it that when I play WoW on XP, I can enable Hardware Cursor, but in Ubuntu, I cannot?

If the lack of Hardware Cursor is Blizzard's fault, is it because many Ubuntu users have to add **SET gxApi "opengl"** to their config/wtf? Does this cause WoW to say "okay, I'll play the game in openGL mode, but I can't turn on hardware cursor" ?

I really do want a solution to come along. Changing the mouse sensitivity ingame to the maximum setting only does a bit of good.

I'd love Dell to come along and say to Blizzard,

"Hey, guys... You know, we offer Ubuntu now as an OS, and we have a deal with you for our laptops. Maybe you should support Ubuntu, so people who try to run Ubuntu on our WoW-edition laptops can actually play WoW without having to jump through hoops."

---

### Post by wisedrunkard on 2008-12-12
bump

---

### Post by aaronsol on 2009-01-27
I noticed this hasn't been updated in more than six months, has any found any solutions to this problem yet?

---

### Post by boogarat on 2009-01-27
Ditto the last guy, 6 months and no update? I'd just like an update refresher letting us linux noobs know if its still a problem with opengl not having a hardware cursor option, or if there has actually been some sort of fix out there for the lag hell for wine and cursors in WoW.

---

### Post by Zoquara on 2009-01-28
I found a fix.. at least, I think I did. Under Video>Resolution (in-game settings) I set my refresh to 69 (the highest I could) and it seems to have helped w/ the mouse lag issue, w/o making anything else lag.

---

### Post by aaronsol on 2009-01-28
I'll give that a try in the morning when I get up. Hopefully that will solve the problem.

---

### Post by aaronsol on 2009-01-29
Unfortunately that doesn't seem to have made much of a difference to mine. Or rather, if it did, it's a very small difference, because I can't tell if it's a little bit better or if right now is just one of the good times where it works almost right.

---

### Post by SKLP on 2009-01-30
I hope this helps :)
[http://ubuntuforums.org/showthread.php?p=6644716](http://ubuntuforums.org/showthread.php?p=6644716)
Atleast It has worked great for me :)

---

### Post by Snypercell on 2009-02-22
i had no idea this issue had been around for so long. wow. i cant believe blizz wont recognize this as a real issue.... i mean, its all over their forums, as well.

anywho, off to play some WoW

---

### Post by NightMKoder on 2009-02-22
According to Wine's AppDB ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154):](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154):)
> 
Mouse cursor slow

Try running the game in Windowed mode, but do note that the jerky mouse is due to failure of Blizzard not implementing the Hardware Cursor, so it will not be perfectly smooth, but at least it wont delay.

 If that has not worked, then there is no other fix


You can try the patch for wine that forces a cursor, but that is far from the best solution.

---

### Post by gasparov on 2009-04-23
I'm on gentoo, gentoo recently moved to xorg 1.5 and i didn't have this problem before.

New xorg, new ati drivers and the mouse problem popped out

I dodn't have this problem on ubuntu( i don't have wow on ubuntu) but still maybe  it could help somebody sorting out the issue

---

### Post by BigRedd on 2010-05-08
I've been having a similar problem as many of the people above (surprise surprise), and I took a shot in the dark looking at the mouse settings in ubuntu. By default, ubuntu disables the mouse cursor when typing, which carries over into games (which, at least for me, explained why my mouse would lag after keypresses, for example).

Disabling that setting in the mouse options fixed things for me, or at least as far as mouse lag is concerned.

---

