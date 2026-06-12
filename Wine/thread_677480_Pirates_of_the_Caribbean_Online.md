---
title: "Pirates of the Caribbean Online"
date: 2008-01-24
forum: Wine
---

### Post by Dwarrel on 2008-01-24
When i try to login i get this error.

fixme:wininet:InternetSetOptionExA Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_RETRIES: STUB
Detail Rule [61753699 0411314e35af91926e8d96d2a45c033a]
Detail Rule [30247155 2cb0e5416752964070ceb9ec323e0672]
Detail Rule [46552734 22d34ca500f1cc5089acf6816312e508]
Detail Rule [148309790 42de52e5001abb19172f0eac4e64a330]
Detail Rule [65983410 cf9ce67660fe5816f7a95e90cd08685e]
Detail Rule [4004393 a6c865a67ffd0c65767ee671ffedf08f]
Omitting File dx9_reqd_dll.mf
fixme:wininet:InternetSetOptionExA Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_RETRIES: STUB
VR Funnel URL = [http://download.piratesonline.com/logging/collector.php](http://download.piratesonline.com/logging/collector.php)
HitBox Funnel URL = [http://ehg-dig.hitbox.com/HG?hb=DM560804E8WD;DM51030813MR;DM5103083LCA&ln=en-us&gp=STARTGAME_DOCK&fnl=PIRATES_FUNNEL&vcon=/Pirates_Online/US/Release&c1=win32&c3=5_0__2195&n=LAUNCHER_LOGIN_INITIAL](http://ehg-dig.hitbox.com/HG?hb=DM560804E8WD;DM51030813MR;DM5103083LCA&ln=en-us&gp=STARTGAME_DOCK&fnl=PIRATES_FUNNEL&vcon=/Pirates_Online/US/Release&c1=win32&c3=5_0__2195&n=LAUNCHER_LOGIN_INITIAL)
sock_set_error: Success

I think wine is unable to connect to the login server, also i think this is a problem not only for this game, is there any known solution or does any one know when it might be supported?

---

### Post by Ferrat on 2008-01-25
Get the same problem, since PotCO uses a very basic dx and opengl for grafics my guess would be that wine is having problems connecting the http adresses to the game and to funnel the information, probably something minor that has been overlooked since it just req. dx3 or better

---

### Post by Dwarrel on 2008-01-26
so this might just be solved by time?

---

### Post by demons bell on 2008-02-01
I got the updates and what not but it wount let me log in says "there was a problem please verify"....pirates of the Caribbean Online  is all i whant lol, I do hope this is practical to fix.

---

### Post by demons bell on 2008-02-03
[http://wiki.winhq.org/FAQ#head-0344b4325219c69636aeffeaa3596d6855283afd]("http://wiki.winhq.org/FAQ#head-0344b4325219c69636aeffeaa3596d6855283afd")

---

### Post by demons bell on 2008-02-03
ignore that link

---

### Post by ssj3strife on 2008-02-11
Well, since the launcher can get online and download the updates, obviously the launcher can communicate with the game servers. So the problem isn't that the launcher can't find the server, but rather - and I'm guessing here - that the launcher isn't understanding what it gets back from the server when it tries to authenticate. 

Since the launcher is also not displaying anything in the "News" pane of the launcher, could there possibly be a problem with Gecko? Is there any alternative to that we might try to see if there is an improvement?

(If Gecko is a rendering engine only and isn't involved with the actual http requests, then I'm probably wrong...)

---

### Post by MopheadNo38 on 2008-02-27
I've been having the same problem with the game where whenever i try to log on it gives me a message saying it is unable to verify my username. :(

---

### Post by MopheadNo38 on 2008-02-27
Could this be happening because of the directx requirement as was suggested earlier? Because although it is connecting to the game server maybe directx is needed to verify the account and actually log in? Is there some alternative to directx or any way of getting it because I've tried and it gives an error message because this is not windows nor dos.

---

### Post by NeoFlexer on 2008-03-25
Kind of a bump, kind of wanting to help.

Is there an error log with wine?  I've noticed that when I install the a new game the term will stay open in the background while I'm playing it, but every time I open after that theres no term.

Is there any way to open this game from the command line so that I could get a read out of whats going on?

---

### Post by NeoFlexer on 2008-03-26
Just wondering.. Is there any way to install IE 7 on wine, or maybe even update java?  I don't know if that would help?

---

### Post by ssj3strife on 2008-03-27
You can run wine from a command line, try something like this:
(The paths may be different, I'm writing this from memory)

cd ~/.wine/drive_c/Program\ Files/Disney/Pirates\ of\ the\ Carribean\ Online
wine Pirates.exe

Hopefully I spelled that all right... :)

As far as IE7 or Java... I don't know, I've never tried! I'm guessing IE7 might be too complicated to be worth it, but I think you could probably install the Windows version of Java without too much trouble.

---

### Post by bdorminy on 2008-05-27
Just wondering if anyone has come up with a Solution to this. I was just trying to get POTC to work and after getting Wine installed ran into "the wall". I'm getting the Can't verify erro when I try to log in.

---

### Post by wactuary on 2008-06-04
> **ssj3strife said:**
> You can run wine from a command line, try something like this:
(The paths may be different, I'm writing this from memory)

cd ~/.wine/drive_c/Program\ Files/Disney/Pirates\ of\ the\ Carribean\ Online
wine Pirates.exe

The commandline to run the app (taken from the launcher that the installer created) is 
```
env WINEPREFIX="/home/[username]/.wine" wine "C:\Program Files\Disney\Disney Online\PiratesOnline\Launcher1.exe"
```

Note replace [username] with your home directory.  If you run that from a command line, you can see the wine output.

In doing this, here is the Wine output when trying to log in.  Unfortunately, I don't know how to interpret this.

```
Omitting File dx9_reqd_dll.mf
fixme:wininet:InternetSetOptionExA Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_RETRIES: STUB
VR Funnel URL = http://download.piratesonline.com/logging/collector.php
HitBox Funnel URL = http://ehg-dig.hitbox.com/HG?hb=DM560804E8WD;DM51030813MR;DM5103083LCA&ln=en-us&gp=STARTGAME_DOCK&fnl=PIRATES_FUNNEL&vcon=/Pirates_Online/US/Release&c1=win32&c3=5_1__2600&n=LAUNCHER_LOGIN_INITIAL
sock_set_error: Success

```

I'm another one stuck at the can't verify log-in spot.

---

### Post by Norwal on 2008-06-19
I'm having the same log in issue. I get the news displayed and the Links at the bottom of the page work fine.  Unfortunately I am not savvy enough to interpret the code above. :(

---

### Post by Faud on 2008-06-19
Its funny because the 1.0 version is listed as plat on winehq.org

Its the 1.0??? version that is messed up. I wonder if you can install the 1.0 version and see what the launcer is doing and then mimic that in the updated version

---

### Post by KlinerDraken on 2008-06-21
Not sure if this will help or not but here is what i get if i run "pirate.exe"

```
$ wine Pirates.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:shdocvw:PersistStreamInit_Load (0x7f021438)->(0x7f21e9ec)
fixme:shdocvw:OleControl_FreezeEvents (0x7f021438)->(1)
fixme:shdocvw:PersistStreamInit_Load (0x7f0218a8)->(0x7f21e9ec)
fixme:shdocvw:OleControl_FreezeEvents (0x7f0218a8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x7f021438)->(0)
fixme:shdocvw:OleControl_FreezeEvents (0x7f0218a8)->(0)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x7f0218a8)->(0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x7f0218a8)->(0)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x7f021438)
fixme:shdocvw:OleObject_Close (0x7f021438)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x7f0218a8)
fixme:shdocvw:OleObject_Close (0x7f0218a8)->(1)
Cleanign Up Thread
```

---

### Post by Dark Ares on 2008-06-22
@KlinerDraken: if you have 8.04 you need to adjust a couple of things to remove the failed reserve range problem. Got to this website and follow enstructions. [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by KlinerDraken on 2008-06-22
> **Dark Ares said:**
> @KlinerDraken: if you have 8.04 you need to adjust a couple of things to remove the failed reserve range problem. Got to this website and follow enstructions. [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)


Thanks! You rock :guitar:

---

### Post by Dark Ares on 2008-06-22
no problem. but after that you still should have problems with PofCO....sorry about that

---

### Post by AgentZ86 on 2008-07-27
> **MopheadNo38 said:**
> I've been having the same problem with the game where whenever i try to log on it gives me a message saying it is unable to verify my username. :(

Same here

The game seems to download and install just fine, and I get the login screen but the game screen says (There Was A Problem Verifying The Account ID)

So I can't get past this ?

---

### Post by klightspeed on 2008-08-02
I just discovered that part of it is written in python!!

Their graphics engine is Panda3D, which is free software, and is available for Linux.

They appear to have developed under Cygwin.

I wonder if they will create a Linux port?

If enough of us hassle them, then maybe they might??

Aanyway..

I did a packet capture on both a Windows computer and a Linux computer.
When you log in, it sends your login over _HTTPS_ to 198.105.196.11 (apps.pirates.go.com).

Now here's the problem:
Under windows, the SSL session is set up fine, and everything goes smooth.
Under Wine however, a _Plain-text HTTP_ request is sent, which is met with a hang-up (thus the "socket_set_error: Success").

Therefore, the problem is that SSL isn't working in PotC under Wine.

---

### Post by AgentZ86 on 2008-08-09
> **klightspeed said:**
> I just discovered that part of it is written in python!!

Their graphics engine is Panda3D, which is free software, and is available for Linux.

They appear to have developed under Cygwin.

I wonder if they will create a Linux port?

If enough of us hassle them, then maybe they might??

Aanyway..

I did a packet capture on both a Windows computer and a Linux computer.
When you log in, it sends your login over _HTTPS_ to 198.105.196.11 (apps.pirates.go.com).

Now here's the problem:
Under windows, the SSL session is set up fine, and everything goes smooth.
Under Wine however, a _Plain-text HTTP_ request is sent, which is met with a hang-up (thus the "socket_set_error: Success").

Therefore, the problem is that SSL isn't working in PotC under Wine.

Interesting, 

I wonder if this could be fixed manually, I wish I knew more about these things.
I would love to play with it.

---

### Post by Psy-Krow on 2008-08-11
here's to hoping for a linux port.
cheers

sent my e-mail in

---

### Post by Norwal on 2008-09-06
> **Psy-Krow said:**
> here's to hoping for a linux port.
cheers

sent my e-mail in

Good idea.  I just canceled my account.  I told them I have no need for Windows now that EVE Online has a Linux client.:lolflag:

---

### Post by dow mathis on 2008-10-29
I sent in a request for a Linux port as well, and I got a very polite and non-helpful response last night.

For your reading pleasere :D :

> Thank you for your feedback and your interest in making Pirates of the Caribbean Online a better place.

We are pleased to hear from our Guests and welcome your comments regarding our products and services.

Please keep in mind that the team of developers is continually balancing and updating Pirates Online in order to provide you the best experience possible.

The current minimum requirement for Pirates Online:

PC running Windows 2000, XP, Vista 
800 MHz or faster processor 
512 MB RAM (1GB recommended)
32 MB 3D graphics card 
DirectX 9 or better 
DSL or Cable Internet connection 
700 MB free disk space 

Mac running OS 10.4.6 (Tiger) 
512 MB RAM (1GB recommended)
DSL or Cable Internet connection
700 MB free disk space

In order to find out the type of video card and the date of your video driver, please follow the steps outlined below.

1) Go to Start and click Run
2) Type "dxdiag" and click OK
3) Click on the Display tab at the top of the screen

The video card manufacturer is listed in the "Device" section and the date for the video driver is in the "Drivers" section. Once you locate the card and driver version, please go to the card vendor's web site to search for any updates to your driver.

Note: If you have the Vista OS, the Run command is not enabled on the front of the Start Menu. You can find the Run command under All Programs | Accessories | Run to complete the steps outlined above.

If you feel your computer meets the minimum requirements listed above, and you received this message in error, please submit another bug report by going to the Report A Bug Web page:

[http://www.piratesonline.com/feedback.html](http://www.piratesonline.com/feedback.html)

We appreciate your feedback and we look forward to seeing you in Pirates Online soon!



It's good to know that my input is special... just like everybody else's

---

### Post by dert on 2009-01-10
No Gnus is BAD Gnus!!  I'm Gary Gnu and this it today's news...STILL NO NEWS ON THIS!!  Very irritating.  I'm writing into the studios now to let them now they're NOT maximizing shareholder wealth by continuing their stubborn refusal to port this game to Linux.  There's absolutely NO justification for it!  Perhaps a proxy vote to fire a few people might shake this up a bit.  DISNEY SHAREHOLDERS WITH LINUX SYSTEMS WANT IN!!!  NOW!!!  Whattaya think?

---

### Post by taurean on 2009-01-19
> **dert said:**
> No Gnus is BAD Gnus!!  I'm Gary Gnu and this it today's news...STILL NO NEWS ON THIS!!  Very irritating.  I'm writing into the studios now to let them now they're NOT maximizing shareholder wealth by continuing their stubborn refusal to port this game to Linux.  There's absolutely NO justification for it!  Perhaps a proxy vote to fire a few people might shake this up a bit.  DISNEY SHAREHOLDERS WITH LINUX SYSTEMS WANT IN!!!  NOW!!!  Whattaya think?


Wait, they still have NO intention? That for me is enough to cancel my sub, and quit using my windows boot to play the game. Up theirs. Im sick of people sticking linux, especially when it's the linux guys who make such GREAT distros, that we have to either ignore or fub around with to get these non-helpful morons things to work.

THEY need to get off the vista anus and start providing for ALL the damn OS's that people use, until then, I'll stop paying. If You See Kay them, Kay them all.

:mad:

---

### Post by 10snoopy1 on 2009-02-14
> **dow mathis said:**
> I sent in a request for a Linux port as well, and I got a very polite and non-helpful response last night.

For your reading pleasere :D :



It's good to know that my input is special... just like everybody else's



I got the same unhelpful message back in 2008 when I wanted them to make the game for Ubuntu so you can download it for Ubuntu instead of Windows. In 2009 I got a message saying "That we are currently working on making Pirates Online available for Ubuntu." The release date ranges from Fall 2009 to Fall 2010.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by imnotjack on 2011-03-02
Hey guys I got it
 I did it using playonlinux. heres the link to the details of how I did it.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1690760](http://www.uluga.ubuntuforums.org/showthread.php?t=1690760)

I logged in and played 2 times. but they still won't help refine it.

---

### Post by 10snoopy1 on 2011-06-15
I am able to play on CrossOver Games 10.1.0 using Lubuntu.

Everything seems to work like it should.
 On Lubuntu 11.04.

---

### Post by imnotjack on 2011-10-11
I'm glad theres more than one way to do it, but playonlinux is free and would be the cheaper choice.

---

