---
title: "Fallout3 on wine?"
date: 2008-10-30
forum: Wine
---

### Post by semitone36 on 2008-10-30
Hey all

I wouldnt be surprised if this has already been posted a thousand times (sorry if it has) but I was just wondering how long it takes for a brand new game to become wine-compatible?  I did a little [research]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322") and it doesnt look like much progress has been made but I wanted to get everyone's opinion.

I have never used wine before but Fallout 3 would be the game to get me onboard \\:D/

---

### Post by Progressive on 2008-10-30
Oblivion runs acceptably with Nvidia cards and with a native directx dll

Fallout 3 uses the same engine, and its progress should mirror Oblivion's pretty soon.

Hopefully newer ATI drivers will fix the problem for the rest of us. I wouldn't expect any progress soon though, because I have been waiting awhile.

---

### Post by ppl on 2008-10-31
Fallout 3 looks great, probably going to be as good as the first two, and it is like THE game I am waiting for years. 

I can wait if I must, but if they could get crossover working sooner, I wounldn't mind resume my account.

---

### Post by atryus28 on 2008-10-31
Well I just got fallout3 and installed it with the newest version of wine.  It installs and then seems to run fine except for one big caveat.  The mouse refuses to work it just gets stuck in the middle of the screen with a case of Parkinson's or something.  I never tried oblivion before so I will now have to find out which dll is needed to run oblivion.  I will post back if I make any progress.

---

### Post by ppl on 2008-11-02
Any news?

Looks like the mouse bug is [fixable]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322"), but the apparently, the game still not playable.

More information checkout [Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322"), lots of testing already going on there.

---

### Post by atryus28 on 2008-11-03
No, I have not gotten further.  Before even having the fix for the mouse issue I found that trying to start a new game just hung.

It's not looking good for now, and I really wanted to play the game.  Spending 3 hours trying to get it to run was enough.  The game is so much fun.  I am truly enjoying the updated version of fallout.  It's first person but the feel of the Fallout series has not been lost in my opinion and the graphics look great.  So for now I will need to use windows or some gaming needs.  I hate it but I don't have a choice for now.

We need to petition a company to port it to Nix.  Bethesda says they will not port it but they will let someone else port it if they want to.

i would buy the game again if someone would port it.

---

### Post by Adahn on 2008-11-03
I read the winappdb entry for F3.
I have the game but haven't installed it yet.

One piece of info I picked up is related to the securom disc check.
Installing the game from setup.exe rather than the installer may circumvent the securom install.
Either way, starting the game from fallout.exe rather than the falloutlauncher circumvents the disc check, all without a crack.

My sis was able to play discless in Winxp32 by starting from fallout.exe rather than using the launcher.

I'll test this at some point unless someone beats me to it.
I'd venture to guess that securom is not good for wine in any case.

---

### Post by atryus28 on 2008-11-03
Thanks for that info, I did notice both .exes but was not sure how each worked.  If nothing else at least this DRM is not nearly as intrusive as I was expecting.  It does not need to connect to the net to work or anything.

---

### Post by ppl on 2008-11-04
I'd suggest we who care about play Fallout 3 in wine vote it on winehq. I haven't get my game yet, as I am too busy with my Thesis deadline, but I already did a vote and hopefully it will get working sooner.

---

### Post by semitone36 on 2008-11-04
Haha so I guess the answer to my question would be: itll be awhile :)

---

### Post by ppl on 2008-11-05
Yes, it is still not working, and will crash inside the game! But as I am monitoring it on winehq for a few days, it is quite active right now and I am guessing because when a game is just released, it will grab more attentions.And if it didn't get enough attentions in the first few weeks to playable, it is probably not going to be playable for a while. 

Look at Fallout 1 and 2, I still had a hard time to play them in Wine last year and end up play them in Windows most of the time, and I am not alone! For some reason, Fallout 3 already have more vote than 1 and 2 altogether, so I will bet a fair chance that it will be playable pretty soon. Anyway, I guess Fallout is one of the few games worth my time and effort only try to make it working in my favourite OS.

---

### Post by Adahn on 2008-11-05
I installed this with wine (default version in II, 1.0.0.1 I recall) using the setup.exe on the dvd.
Nothing happens when opening the game via either the wine launcher or fallout.exe in the program file.

I will attempt to install a dx9.dll as suggested in the wineappdb for oblivion, since the games use the same engine.

I'm guessing that w/o a crack, we're hosed, since the game uses securom.
I think they're out already.

---

### Post by atryus28 on 2008-11-05
I have successfully gotten the game to run without the DVD in the drive and getting it to start in wine is nto hard.  Just every thing else.  Use the fallout.exe not the launcher.  You can try setting it to be vista as well.

---

### Post by Adahn on 2008-11-06
Still no-joy using either the .dll suggested for Oblivion or the fallout3 no-cd cracked exe.

---

### Post by ppl on 2008-11-08
Adahn, I didn't do any testing but wouldn't be surprised if your wine version doesn't working with Fallout 3. 

Also an update from winehq, it seems [almost there]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322"), from what I see, there are no more mouse and headless bugs here and just need more testing and someone make a workng .deb patch for us who don't want or too scared to make a patch from diff file. It seems need a wine 1.18 version.

---

### Post by Adahn on 2008-11-08
I just upgraded to the 1.1.8 version and still nothing.

---

### Post by ppl on 2008-11-09
hi, Adahn, if you are still trying I found information in [here]("http://www.nabble.com/Big-test-coming-up%3A-fallout-3-td20175752i60.html") might be helpful for you, they found two version of CD crack helpful--one from TPB and another one seems legal, not sure which one you've tried and some even have detailed information about what they did step by step to get it so far(still not playable). 

Sorry I don't have a copy of Fallout 3 and probably wouldn't have time to test it until next week, but hopefully with the newest patch it will works more toward playable. There is another positive test result just posted on winehq, in summary: characters in F3 will have heads now and it seems playable but he still got some problem in mouse click.   

Good luck, and have fun.

---

### Post by lingnoi on 2008-11-13
Please don't link to nabble they just steal content from websites and put it on their own. The exact same information is [available on the wine website]("http://forum.winehq.org/viewtopic.php?t=2672") which is where they stole it from.

Also for anyone that doesn't already know, you shouldn't use cracks when submitting bug reports, in fact I don't believe you need a crack for this game at all.

I know people have got the game running, you need to go into regedit and add the following to HKEY_CURRENT_USER/Software/Wine/Direct3D

"DirectDrawRenderer"="gdi"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"SoftwareEmulation"="enabled"
"UseGLSL"="enable"
"VertexShaderMode"="hardware"
"VideoDescription"="NVIDIA GeForce 9600 GT"
"VideoDriver"="nv4_disp.dll"
"VideoMemorySize"="256"

If you have ATI graphics card then these values are different as is if your graphics card is a different model.

---

### Post by atryus28 on 2008-11-13
Thanks i will have to try this one out and see if it works.   Especially since I now have a Radeon HD4850, should be ultra quality as well, it is in windows.

---

### Post by Dawey on 2008-11-13
The game runs quite fine with patched Wine 1.1.8 and Ubuntu 8.10 with a 8800GTS 640MB.

I posted a video @ Youtube: [http://www.youtube.com/watch?v=wbm8j4D1wTU](http://www.youtube.com/watch?v=wbm8j4D1wTU)

---

### Post by Milos_SD on 2008-11-15
> **Dawey said:**
> The game runs quite fine with patched Wine 1.1.8 and Ubuntu 8.10 with a 8800GTS 640MB.

I posted a video @ Youtube: [http://www.youtube.com/watch?v=wbm8j4D1wTU](http://www.youtube.com/watch?v=wbm8j4D1wTU)

What patch did you applyed so that VATS doesn't slowdown your FPS?

---

### Post by Dawey on 2008-11-15
> **Milos_SD said:**
> What patch did you applyed so that VATS doesn't slowdown your FPS?

I applied the patch you can find here because the game was supposed to crash without it: [http://bugs.winehq.org/show_bug.cgi?id=15839](http://bugs.winehq.org/show_bug.cgi?id=15839)

I see a quite big slowdown when I use VATS, but I do not know if this patch improves the framerate in VATS.

---

### Post by Arthur Millar on 2008-11-16
> **Dawey said:**
> The game runs quite fine with patched Wine 1.1.8 and Ubuntu 8.10 with a 8800GTS 640MB.

I posted a video @ Youtube: [http://www.youtube.com/watch?v=wbm8j4D1wTU](http://www.youtube.com/watch?v=wbm8j4D1wTU)

please can you post how you got it running?
The wine howto is jibberish 
where do you type patch -p1 < filename.diff  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322&iTestingId=33601](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322&iTestingId=33601) 
I just dont UNDERSTAND

---

### Post by lingnoi on 2008-11-16
> **Arthur Millar said:**
> please can you post how you got it running?
The wine howto is jibberish 
where do you type patch -p1 < filename.diff  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322&iTestingId=33601](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322&iTestingId=33601) 
I just dont UNDERSTAND

You do it wherever you have a copy of the wine sourcecode

The "-p1" means "this directory". So you would have to cd into your "wine" folder with the sourcecode before using that, otherwise it won't be able to find the files to patch.

"< filename.diff" is use the file "filename.diff" to patch wine.

So whenever someone tells you to apply xyz.patch.. you do "patch -p1 < xyz.patch" inside the project which needs patching.

---

### Post by Arthur Millar on 2008-11-16
> **lingnoi said:**
> You do it wherever you have a copy of the wine sourcecode

The "-p1" means "this directory". So you would have to cd into your "wine" folder with the sourcecode before using that, otherwise it won't be able to find the files to patch.

"< filename.diff" is use the file "filename.diff" to patch wine.

So whenever someone tells you to apply xyz.patch.. you do "patch -p1 < xyz.patch" inside the project which needs patching.

arthur@art-pc:~/wine-1.1.8$ patch -p1 < filename.diff
bash: filename.diff: No such file or directory

---

### Post by Arthur Millar on 2008-11-16
my mistake

arthur@art-pc:~/wine-1.1.8$ patch -p1 < attachment.cgi
patching file dlls/wined3d/directx.c
patching file dlls/wined3d/wined3d_main.c
patching file dlls/wined3d/wined3d_private.h

thats better hey? 
:)

im sorry about this next bit but i dont think this is correct 
```

fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:setupapi:do_file_copyW Unsupported style(s) 0x144
Clearing Windows version back to default
Executing wine regedit /home/arthur/.wine/drive_c/winetrickstmp/unset-winver.reg
Install of directx9 done
winetricks done.
arthur@art-pc:~$ err:rundll32:WinMain Unable to load L"streamci"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:rundll32:WinMain Unable to load L"streamci"
fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d0659f8, overlapped 0x7d0659dc): stub
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"

```

---

### Post by Arthur Millar on 2008-11-16
I have the loaderscreen 
if i click PLAY it says it cant load fallout 3 no audio device found 
directX ?

---

### Post by ppl on 2008-11-16
Looks like you need using Fallou3.exe instead FalloutLauncher, I remember read something from [winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322"), but now the closest one I can find is the one posted by Bogdan on 13th 2008, 19:58

---

### Post by Arthur Millar on 2008-11-17
> **Arthur Millar said:**
> I have the loaderscreen 
if i click PLAY it says it cant load fallout 3 no audio device found 
directX ?

this was because of "pulseaudio" I just end the process with system monitor
and it works

---

### Post by lingnoi on 2008-11-17
> **Arthur Millar said:**
> 

im sorry about this next bit but i dont think this is correct

Wine has a ton of debug messages, if you set all the debug messages on you'll get 4 meg text every second.

If you are playing a game and want it to be faster you can stop wine from printing anything out.
```
WINEDEBUG=-all wine Fallout3.exe
```

because it's not printing out any error messages it might speed up by a few seconds.

**However** never send a bug report when you have disabled error messages.

---

### Post by jstableford on 2008-11-17
I get the exact same error when trying to install directx9 with winetricks... what gives?

> **Arthur Millar said:**
> my mistake

arthur@art-pc:~/wine-1.1.8$ patch -p1 < attachment.cgi
patching file dlls/wined3d/directx.c
patching file dlls/wined3d/wined3d_main.c
patching file dlls/wined3d/wined3d_private.h

thats better hey? 
:)

im sorry about this next bit but i dont think this is correct 
```

fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:setupapi:do_file_copyW Unsupported style(s) 0x144
Clearing Windows version back to default
Executing wine regedit /home/arthur/.wine/drive_c/winetrickstmp/unset-winver.reg
Install of directx9 done
winetricks done.
arthur@art-pc:~$ err:rundll32:WinMain Unable to load L"streamci"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:rundll32:WinMain Unable to load L"streamci"
fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d0659f8, overlapped 0x7d0659dc): stub
err:rundll32:WinMain Unable to load L"streamci"
err:rundll32:WinMain Unable to load L"streamci"

```

---

