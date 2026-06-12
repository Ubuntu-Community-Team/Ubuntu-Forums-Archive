---
title: "Vanguard: Saga of Heroes"
date: 2007-03-20
forum: Wine
---

### Post by GBE on 2007-03-20
Hi folks,

Has anyone managed to get Vanguard running successfully under linux using either Wine or Cedega? I'm about to start messing around with trying to get it running myself, so any info anyone can share would be handy.
I would love to rid myself of the curse of Win XP, this game is the only reason I keep using it.

---

### Post by mbm1980 on 2007-03-20
Until recently it wasn't possible however there has been some improvements.
There still need some bug fixes and improvements but so far it looks good.

Follow the progress here: [http://appdb.winehq.org/appview.php?iVersionId=6422](http://appdb.winehq.org/appview.php?iVersionId=6422)
You'll also find guidelines on how to get it to work there.

---

### Post by airtonix on 2007-03-23
i thought this game was in the progress of requiring vista?....could be wrong though

---

### Post by compiledkernel on 2007-03-23
Actually from all ive heard the move to DX10 for the Wine guys will be a relatively easy one. So even if it required Vista only, eventually here pretty quickly Wine will catch up.

---

### Post by alinuxfan on 2007-04-05
> **mbm1980 said:**
> Until recently it wasn't possible however there has been some improvements.
There still need some bug fixes and improvements but so far it looks good.

Follow the progress here: [http://appdb.winehq.org/appview.php?iVersionId=6422](http://appdb.winehq.org/appview.php?iVersionId=6422)
You'll also find guidelines on how to get it to work there.

Yes, there has been a lot of improvement lately.  
I tried the beta and it didn't work and I haven't even opened the box for the game.  I have it sitting right next to my computer though.  
Maybe I'll delve into WINE this weekend and see if I can get something accomplished.

---

### Post by alinuxfan on 2007-04-11
Anyone know yet if Cedega 6.0 runs Vanguard or not?
I am tempted to try it out, but WINE runs all my other gaming needs.  I don't want to fork over money to them unless I am going to get something in return.

Either that or WINE should be coming out with .9.35 soon...


:confused:

---

### Post by Ferrat on 2007-04-12
You can get Vanguard to run but it has issues but the game has issues even in Windows, preformance is a big issue for many players. 

GLSL shaders are far from done on wine and this is a big problem since the code is not very good even for Windows play, so you will have very very low FPS and glitches ect.

---

### Post by Polygon on 2007-04-12
its an unreal based game, so maybe a linux port is not out of their reach.

but i also heard that the game is pretty hard to place performance wise even for windows players

---

### Post by alinuxfan on 2007-04-12
really? performance is that bad on Windows?
I have been out of reach since launch.  I was really rooting for this game.  I even thought about getting a Windows XP to play it (I have since thought against it)
It irks me that it is so buggy.
I loved EQ back in the day and I was hoping that this would be a nice upgrade.
WoW is just too damned easy and Guild Wars only keeps my attention for about 2hrs a month if that
At least with Guild Wars, I don't have to pay a monthly subscription for those 2hrs
/sigh

---

### Post by Darkdelusions on 2007-04-12
With Cedega 6 I was able to get alot further then I could before.... I can not acutally get the splash screen to come up but then it tosses me an unknow error. and I am unable to get it to run at the console right... 

I am working with another V:SOH player hopefully we will be able to hash something out I will keep you all posted on my findings.

---

### Post by shazzed on 2007-04-12
I bought it and then left within a month.
It should be still in BETA.

---

### Post by alinuxfan on 2007-04-13
> **Darkdelusions said:**
> With Cedega 6 I was able to get alot further then I could before.... I can not acutally get the splash screen to come up but then it tosses me an unknow error. and I am unable to get it to run at the console right... 

I am working with another V:SOH player hopefully we will be able to hash something out I will keep you all posted on my findings.

Please Do!
On the WINE appdb there are a few people who have the game running, just not very well...


and

[QUOTE=Shazzed]I bought it and then left within a month.
It should be still in BETA.[/QUOTE]

How is the gameplay compared to EQ?  I am basically looking for a newer, better looking and feeling version of EQ

---

### Post by rbhigday on 2007-08-06
This game is about the only reason I am still a dual boot. This game does not require Vista as I play it on my xp with no problems at all. 

Going to have to find me a wine or Cedega installation guide and see what fun I can have. The more I use windows the more I detest it.

Vanguard feels a lot like EQ1 if you liked eq1 you will like vanguard.

---

### Post by rbhigday on 2008-01-29
any one get this game to work in Ubuntu?

The game has improved drastically in the past few months. Finally a real game and not in beta like the first 9 months or so :)

---

### Post by staryuche on 2008-12-31
Ok, ive spent the night trying to get Vanguard working on Ubuntu.  I took the whole sony file Straight off of Windows on another HD, i had to move all the files in the Station Folder and put them in my home directory (which i hated doing, hate the clutter:P) because the patcher wants to have it there and if i dont it will download to there.  once that is done I have to run Vanguard from the folder, as my applications menu shortcut i set up wants to re-download the entire game somewhere (dont know exactly where its trying to download it to?) but if i just start the file from the folder itself it doesnt do this (odd considering my command for the applications folder is just the same as the filepath??? (i did trying to use aoss to try to not have to switch my audio settings in wine to oss which worked for using WoW and Vent when i got them working under wine, but then just tryed the filepath and it still does this odd downloading thing) anyway it plays sortuv so far.  fairly slow, curser has a perma-box around it, and names on peoples heads dont show right.  Might try to let it just download the game from the applications so i can command -opengl on it.  anyone have suggestions.  Anyone know how to make wine programs download to a particular path, and not just make me rearrange my files and clutter my home directory???

thanks for listening,
star

---

### Post by staryuche on 2008-12-31
ok i moved ALL the files to the home directory and now it patches correctly from the terminal or applications menu but now when it gets to the point of actually getting onto the game i can hear the game but dont see any of my characters...any thoughts.  also still looking for a better way to do this than copy everything to the home directory.

thanks 
star

---

### Post by rbhigday on 2009-01-02
Well staryuche, your getting father along then I am. I did not have the dl problem you did because I just had the program dl the game to the directory that it wanted which ended up in a vanguard folder on the virtual c drive for wine, just like in windows.

Then once I load up the restricted drivers for my video card I get to the splash screen just before character selection and poof, fatal error message and everything closes.

anyway for terminal to log everything that happens or just a cut a paste job?

---

### Post by rbhigday on 2009-01-04
I am attempting to play vanguardsoh

It has install and patches fine

I have 8.10 of Ubuntu and just upgraded to 1.1.12 of Wine

I receive my error right before the loading of the character section screen. The error I receive is:

wine: Call from 0x7b8456d0 to unimplemented function d3dx9_36.dll.D3DXGetShaderConstantTable, aborting
[01/03/09 08:39:00] FATAL: Critical: FD3DVertexShader::Serialize
[01/03/09 08:39:00] FATAL: Critical: UD3DRenderDevice::SerializeCompiledShaders
[01/03/09 08:39:00] FATAL: Critical: UD3DRenderDevice::LoadCompiledShadersFromFile
[01/03/09 08:39:00] FATAL: Critical: UD3DRenderDevice::Flush
[01/03/09 08:39:00] FATAL: Critical: SetViewport
[01/03/09 08:39:00] FATAL: Critical: UD3DRenderDevice::Lock
[01/03/09 08:39:00] FATAL: Critical: UViewport::Lock
[01/03/09 08:39:00] FATAL: Critical: UWindowsViewport::Lock
[01/03/09 08:39:00] FATAL: Critical: Vignette::_Draw
[01/03/09 08:39:00] FATAL: Critical: Vignette::Draw
[01/03/09 08:39:00] FATAL: Critical: UGameEngine::Init
[01/03/09 08:39:00] FATAL: Critical: InitEngine
[01/03/09 08:39:00] FATAL: Exit: Executing UObject::StaticShutdownAfterError
[01/03/09 08:39:00] FATAL: Exit: Executing UWindowsClient::ShutdownAfterError
[01/03/09 08:39:00] FATAL: Exit: OpenAL Audio subsystem shut down.
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
[email]richard@richard-desktop:~/.wine[/email]/drive_c/Program Files/Sony/Vanguard$



any ideas as to where I should look?

---

### Post by rbhigday on 2009-01-06
I can get in using Wine and it last for about 10 seconds if I am lucky then it freezes. the FPS was the same as in windows for me.

Getting closer.

---

### Post by SBFC on 2009-01-07
Back when I still played (cancelled half a year ago or so) it ran fine in Wine with the exception of a tree bug. The trees would all glitch out and leaves would be way larger than intended. A lot of them would even block the camera. 

The tree detail slider would have to be set to 0 to stop the problem but that caused the trees to all look very ugly. 

Aside from that though it was very playable.

---

### Post by staryuche on 2009-01-10
ok I got it working, somewhat.
this is my computer=
Proc- AMD 64x2 Athlon 3.1Ghz
RAM- 4GB DDR2 800 
GPU/VRAM- Nvidia 9600GT
HD1- WD 10kRPM 150GB
OS1- Ubuntu 8.10 desktop ed. (x86)
HD2- WD 7200RPM 160GB
OS2- Windows Vista 64bit HP sp1
PSU- 450Watt PSU
Wine- Version 1.1.12

This is what I did=
1. moved the whole Sony file from Vista HD to Ubuntu HD
2. copyed the contents of my Sony/Station/Launchpad to my home directory (patcher wants to put it there for some reason)
3. deleted ALL .log files and character.ini files
4. run vanguard.exe by exploring the the c drive/Sony/Vanguard/ and double clicking on it

This is what happened=
1. it makes an empty file folder for the station/launchpad in program files for some reason
2. it plays with three issues
     a. Cursor has some artifacting
     b. Fonts in game are changed 
        (possibly fixed by getting correct font)
     c. NPC names have like a shadow that makes them invisible
        from some viewing angles, like straight ahead 
     d. performance hit is something like -60% from same my 
        Vista HD
     e. after about 15-20minutes of play it crashes 
(I have none of these issues on the Vista HD)

Things not to do-
1. do not unclick full-screen mode- your screen will dissapear (fix- go and delete all your .log/character.ini files to re-set to default full screen)
2. do not change resolution- for some reason if i change the resolution at all I get unrecoverable errors from then on when trying to log on from then on like others have stated. (fix- go and delete all your .log/character.ini files to re-set to default)
3. open vanguard from terminal or applications shortcut you made- when i do this it wants to re-download all my files directly into my home directory (fix- dont do it)

Things I'd like help with-
If anyone wants to I need help with-
1. trying to get wine to force the launcher to download/look in the right folder and not my home directory
2. if someone can go to the link towards the begining of this forum string to wine.hq and explain to me what that website is suggesting to add to the regedit in really really plain english step-by-step, so i can add that and possibly get better performance.
3. at the same website on wine.hq he mentions a .dll file for game crashes, if someone could tell me where i need to put that .dll file for it to start working
4. if anyone has any ideas about anything else that might help.

Well thats it,
Star

---

### Post by staryuche on 2009-01-10
ok error above more than three issues, i cant count

---

### Post by issashu on 2009-01-22
I am running vanguard on Ubuntu with a 90% success.
From all the problems you listed, I am facing only the following:

1. Tree leafs all over the screen (found a fix though)
2. NPC names dissapearing (possible fix)
3. Strange shadows (possible fix)

Frame rate for me is the same as under windows XP.


Forgot to say my PC config.:
Intel Core Duo @1.66 Ghz
2 GB RAM
Geforce Go 7600
Ubuntu 8.10
Wine 1.1.13

The game downloading files in the home directory is an old issue. There was a fix at one point, but can't remember what it was :( (something with setting up the application paths...trying to find it again myself). For now easiest way is to run the game from it's own directory and not via shortcuts.

About the tree problem. Set tree details to minimum and it dissapears. 

NPC names and the shadows I encounter have a possible fix, but not sure what to edit in vgclient.ini...
I faced the same problem in Everquest II and the solution there was to increase/decrease the number of light effects and sources, untill everything gets back to normal.

About the mouse cursor. This is also an old issue. Wine doesn't support the type of animated cursors Vanguard uses. Untill recently the cursor wasn't visible at all. So some patch has been aplied and the cursor now appears onscreen, even if with some artifacts.

For registry editing. Here is a step by step how to:
1. Open a terminal and type regedit
2. Browse Current User//Software//Wine//Direct3D
3. If direct3D is not available, create it (new key under wine).
4. Inside find the following OffscreenRenderingMode (look at right panel). If it doesn't exist, create it.
5. Double click OffscreenRenderingMode and on the second row enter pbuffer , fbo or backbuffer. Try each one and see which works best for you.

About the d3dx9_36.dll: Google can help you download it. After that copy it to your wine C:\windows\system32. Run the wine configuration and in libraries, select native for this dll.

Also to change screen resolution and windowed mode, use the vgclient.ini file. The ingame settings crash the game, as you found out.

---

