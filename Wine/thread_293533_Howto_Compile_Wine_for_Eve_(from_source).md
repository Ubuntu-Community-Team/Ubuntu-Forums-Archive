---
title: "Howto: Compile Wine for Eve (from source)"
date: 2006-11-05
forum: Wine
---

### Post by stuart.crouch on 2006-11-05
This guide is now useless (other than as an example of how to apply patches to wine).  Wine has come a long way since I wrote this over two years ago.

For the best way of setting up wine - Grab the latest version and then look at this page  

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2249](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2249)

Click on version you want to run (usually the one at the bottom of the screen) and follow the tips it suggest)

Redundant guide follows

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

This Howto will walk you through each step needed to go from a base install of Edgy (with just the Graphics system configured) to having a copy of wine and Eve installed.

Lets begin!

First we need to install all the things required to compile WINE.  (Can someone with a clean system help me here?  I've already set up my system as I had to install ATI drivers, so there may be more packages are required.)

```

sudo apt-get install build-essential flex bison xlibs-dev x11proto-gl-dev libgl1-mesa-dev fontconfig libfreetype6-dev fontforge checkinstall

```

Grab the wine source code and the current eve setup program (this will be different when a new version is released, go to [www.eve-online.com](www.eve-online.com) for new versions).  I'm dumping everything in my home directory.  If you do the same then you should be able to follow these instructions to the letter.

```

cd ~/
wget http://kent.dl.sourceforge.net/sourceforge/wine/wine-0.9.24.tar.bz2
wget http://ccp.vo.llnwd.net/o2/EVE_Setup_25245.exe

```

Now grab the patches and hacks that will allow us to run eve
```

wget http://elfe.mine.nu/eve/linux/eve-2006-10-20.diff
wget http://elfe.mine.nu/eve/linux/MachoNet.bash

```

Extract the wine files, put the patch in the right place (so it can find the files) and patch the code.

```

tar -xvf wine-0.9.24.tar.bz2
mv eve-2006-10-20.diff wine-0.9.24
cd wine-0.9.24
patch -p1 <eve-2006-10-20.diff

```

Set up the wine compile environment (the CFLAGS is essential!) and build.  If you dont add the cflags then when you try to run wine you'll just get "Segmentation fault. Core dumped."

```

./configure CFLAGS=-fno-stack-protector
make depend && make

```

Now go away and make dinner or something.  This took 45 minutes on my AMD Athlon 3200+.  Once it finishes we want to install wine as a package.  This allows us to 1) Take a copy of this version of wine that definitely works (incase future versions of wine break EVE) 2) Uninstall it via Synaptic 3) Give it to your mates/install it on another pc without compiling

```

sudo checkinstall

```

Choose yes to generate package documents (if necessary)
For the description enter &#8220;Wine 0.9.24 (patched for EVE)&#8221;.  This is what appears on the installer/uninstaller description, so if you want to list the known bugs too feel free.  

Wine is now installed :D. We now need to configure it a bit.  With EVE there is no need for winetools or anything that "taints" the wine installation.

```

winecfg

```

Set the default windows version to windows 2000.  Make sure the audio tab has some sort of audio set.  At present my one only has OSS, after fiddling with ubuntu to get my soundcards right (I have onboard and a plug in) this works fine.  ALSA should also work.

Next task, install EVE &#8211; (Replace 25245 with whatever version you downloaded.)

```

cd ..
wine EVE_Setup_25245.exe 

```

After successful installation, run the bash file to create the extra directories.  If you dont do this Eve will authenticate your account, then just reset to the username/password boxes.  This stumped me for hours til I tried it on windows and saw it was caching bulk data

```

chmod u+x MachoNet.bash
mv MachoNet.bash ~/.wine/drive_c/Program\ Files/CCP/EVE/
cd ~/.wine/drive_c/Program\ Files/CCP/EVE
./MachoNet.bash

```

And now the moment you've all been waiting for

```

nice -19 wine ~/.wine/drive_c/Program\ Files/CCP/EVE/EVE.exe

```

nice -19 is needed in order to give WINE enough space to allow sound to be sent out.  If you dont add it, the music and speech will be garbled as everything fights for resources.

Known bugs with this version are

1) Graphical corruption of own portait (all other portaits/images appeared fine in my week of testing)
2) Ubuntu mouse cursor appears over eve cursor
3) Can crash when switching between wine and other applications (eg open office and this firefox browser ;).  Staying ingame seems to keep things stable.
4) May still be a memory leak in there, as it got really slow for me after about 4 hours of playing.  Quiting and re-entering solved that problem

The only thing left to do on this how to is create a shortcut.  Unfortunately I cant figure out how to do this on gnome.  I used the right click create menu on the desktop, but the file it created didn't seem to actually execute.

I'd also like a games/EVE directory on my Applications menu, but the ala carte editor seems to have disappeared since Dapper.

So, let me know about missing features for the apt-get line, let me know how to create short cuts, and most of all let me know how you got on :D

See you in space!

---

### Post by Ipsissimus on 2006-11-06
Wonderful! I've been trying to compile Wine on Edgy for a few days, wish I found that './configure CFLAGS=-fno-stack-protector' flag earlier. As for EVE... freakin' great! Finally have it working on Ubuntu. Runs great at decent frame rates, but still there are certain bugs that will keep me from running EVE in PvP/Fleet battles. The capacitor looks buggy and does not display correctly, which make fighting quite scary. But Great for switching skills at work.
  Works great on laptop and ATI x1400 card. Will try at home later on nVidia card.
  EVE is the ONLY thing keeping a windows partition at home... we'll see with Kali.

-- Thanks stuart.crouch!

---

### Post by WhiteDawn on 2006-11-07
> **Ipsissimus said:**
> wish I found that './configure CFLAGS=-fno-stack-protector' flag earlier.
Same here! I was so confused as to how wine was giving me that segmentation fault!
Although I don't play eve, I hope that nice -19 might help in some games with garble

Thanks, even though I don't play EVE, you've helped me alot!

---

### Post by Ipsissimus on 2006-11-15
Eve runs fine, but when I try to run the process niced from the command time I get an error:

```

[EVE 62] nice -19 wine eve.exe 
setpriority: Permission denied.
[EVE 63]
```

I'm not going to run EVE as root, is that what its asking for here?

-- Thanks

Update:  I have just compiled and installed the new 0.9.25 version of Wine with a more recent patch ([http://elfe.mine.nu/eve/linux/eve-2006-11-05.diff]("http://elfe.mine.nu/eve/linux/eve-2006-11-05.diff")). Not only does EVE work well, it works with xGl running! The downside is that EVE is pretty slow while running under xGl because it does not allow direct rendering. But if you want to run xGl for your desktop but get good performance in EVE just run it on the non xGl display by using the following script (remember to set it 'chmod +x' and adjust to where your eve.exe is):

```
#!/bin/sh
DISPLAY=:0 wine /home/lukasz/.wine/drive_c/EVE/eve.exe
```

---

### Post by zaziork on 2006-11-16
I get as far as the initial Eve splash screen, and am then greeted with the message "No Audio Drivers Detected".

winecfg only presents me with the OSS option (I usually use alsa). I've tried changing my system settings to use OSS, to no avail; I still get the same result when attempting to run Eve.

I'd like to stick with alsa if possible; why is this option not offered in winecfg? I've previously installed an un-patched version (.deb package) of the same release of wine via the repository (using apt), and more sound options were available (including alsa).

Any ideas anyone?

TIA.
Dan.

EDIT: Solved: Hardware acceleration needs to be set to "Emulation" under the audio tab. Crackles a bit, but better than nothing...

---

### Post by Ipsissimus on 2006-11-16
I never play EVE with sound and have it turned off in the .ini file ('sound=0' or something). When I try to change to the sound tab in winecfg it crashes for me. Eve runs fine without sound though. Although I wouldn't mind getting it to work in case I need it at a later date.

---

### Post by Shabutie on 2006-11-17
eve installed fine, great howto! small problem though, when trying to connect to eve, the status bar gets half way through authentication and then quits... any suggestions?

---

### Post by stuart.crouch on 2006-11-17
Did you do the machonet bit.  This sounds like what stumped me for hours...  Basically, it authenticates, then tries to download all the cache needed for the game.  The directories don't exist so it fails and drops you back to the login area.  Running the machonet bash (and it finishing successfully, no text is written to the screen) will create those directories and it will authenticate and then the same progress screen will say something about grabbing cache files.

> 

After successful installation, run the bash file to create the extra directories. If you dont do this Eve will authenticate your account, then just reset to the username/password boxes. This stumped me for hours til I tried it on windows and saw it was caching bulk data

```


chmod u+x MachoNet.bash 
mv MachoNet.bash ~/.wine/c/Program\ Files/CCP/EVE/ 
cd ~/.wine/c/Program\ Files/CCP/EVE 
./MachoNet.bash


```


Glad this tutorial has been helping people :D (and that it didnt need any major ammendments)

---

### Post by Shabutie on 2006-11-19
right, when i did that the first time it didn't work, but i didn't catch it cuz i wasn't paying much attention.  had to change /.wine/c/Program\ Files/CCP/EVE/ to /.wine/**drive_**c/Program\ Files/CCP/EVE/..... works great now!! thanks again for the howto, sorry i didn't post quicker but i was too busy playing EVE

---

### Post by testbenchdude on 2006-12-03
I get to this part 

./configure CFLAGS=-fno-stack-protector

and then I get this error:

no suitable lex found. Please install the 'flex' package.

Please help?

---

### Post by testbenchdude on 2006-12-03
NM figured it out.

apt-get install flex

and then it wanted somethins calle "bison"
so...

apt-get install bison

and bada-bing! On to make depend && make. :)

---

### Post by hikaricore on 2006-12-03
> **testbenchdude said:**
> I get to this part 

./configure CFLAGS=-fno-stack-protector

and then I get this error:

no suitable lex found. Please install the 'flex' package.

Please help?

```
sudo aptitude install flex
```

This should install everything you need

Have you already installed build-essential ?

---

### Post by testbenchdude on 2006-12-03
> **hikaricore said:**
> ```
sudo aptitude install flex
```

This should install everything you need

Have you already installed build-essential ?

Hmm? No I didn't.. do I need to? I followed the directions and I get the splash screen for about a minute but then it disappears...

EDIT*

I did apt-get install build-essential and it installed.

When I launch EVE I get the splash screen, then it dumps me back. Here's the text displayed in terminal:

fixme: process:IsWow64Process (0xffffffff 0x33fc34) stub!
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347acc

edit--there is no space between the first fixme: process. If I put them together a smiley is displayed :P :P :P

Help again please?

---

### Post by Ipsissimus on 2006-12-03
Before you configure/compile Wine I suggest you run:

> sudo apt-get build-dep wine

This will install all pre-requisite packages needed to compile Wine. Just to be sure, I suggest you add the following repositories to apt-get. From System->Administration->Software Sources, go to the 'Third Party' tab and add:

> deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


This should install everything you need to build, and if you need it 'sudo apt-get install build-essential'. Then follow the 1st post for instructions.

Hope that helps,
-- Ipsissimus

---

### Post by testbenchdude on 2006-12-04
Thanks for trying, but still no joy. 

[email]root@ubuntu-leet:~/.wine[/email]/drive_c/Program Files/CCP/EVE# wine eve.exe
fixme:process:IsWow64Process (0xffffffff 0x33fc34) stub!
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347acc
fixme:process:IsWow64Process (0xffffffff 0x34a428) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x349e90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x349e90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x349e90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x349e90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x349cac,0x00000000), stub!
wine: Call from 0x2e291dc to unimplemented function DDRAW.dll.DdEntry23, aborting
err:seh:setup_exception nested exception on signal stack in thread 001b eip 7efd3b3f esp 7ffddc00 stack 0x241000-0x350000

This sure is one tough nut to crack.

---

### Post by Ipsissimus on 2006-12-04
Okay, I tried to find a little information for you. I went to my .wine/drive_c directory and searched for your file and got:

> find . -type f -name '*msvc*'
./windows/system32/msvcrt.dll
./EVE/bin/Microsoft.VC80.CRT/msvcm80.dll
./EVE/bin/Microsoft.VC80.CRT/msvcp80.dll
./EVE/bin/Microsoft.VC80.CRT/msvcr80.dll

I don't know whether EVE normally installs the bin/Microsoft.VC80.CRT directory, but I did have to run the bin/RedistD3DXOnly.exe file because I was getting errors. Running that fixed the DirectX errors, and might have created that directory with the .dll you're missing perhaps?

Also, what version Wine are you running now? For EVE Revelations to work you'll need the latest:

> [http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.26.tar.bz2](http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.26.tar.bz2)
[http://elfe.mine.nu/eve/linux/](http://elfe.mine.nu/eve/linux/) (.diff file)

Now... what **I** actually do is just add the following repositories to Edgy, System->Administration->Software Sources, go to the 'Third Party' tab and add:

> deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

Then I just run:
> sudo apt-get source wine

Which downloads the newest Wine from winehq servers, and applies any Edgy patches to Wine. (NOTE: It makes all files owned by root). THEN I apply the EVE patch, compile, and play. Perhaps you are having problems because you are not applying the Edgy patches? If you're still having problems I may write up a 'from scratch' install step-by-step that I use... but it'd me near identical to the thread creator's.

---

### Post by pseudo.sanity on 2006-12-09
Greetings all,

I have been toying with Linux distros for a few years now... but I still consider myself as a noob when it comes to this stuff.  Plus this is the first time I have ever compiled something... normally I complain to my manager at work and he does it for me :) .

I seem to be having a different issue when I try to run Eve.. when the splash screen show up i get a "Microsoft Visual C++ Runtime Library" error box that says;
---
Runtime Error!
Program: C:\Program Files\CCP\EVE\bin\ExeFile.exe
R6034
An application has made an attempt to load the C runtime library incorrectly.  Please contact the application's support team for more information.
---
Terminal says;
---
root@psychosis:/home/tbrown/wine-0.9.26~winehq0~ubuntu~6.10# ./wine /home/tbrown/.wine/drive_c/Program\ Files/CCP/EVE/eve.exe 
fixme:process:IsWow64Process (0xffffffff 0x34fc24) stub!
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347a6c
root@psychosis:/home/tbrown/wine-0.9.26~winehq0~ubuntu~6.10# 
---

I've tried recompiling... reinstalling eve... tried wine 0.9.22 and 0.9.26... patching wine... not patching wine... always comes up with the same error...

Has anyone else come across this?

Thanks.

---

### Post by Ipsissimus on 2006-12-09
People having errors with the "msvcr80.dll" file I would say try running this:

```
wine ~/.wine/drive_c/Program\ Files/CCP/EVE/bin/RedistD3DXOnly.exe
```

As far as I can tell this creates the .dll files some of you are missing. After this, try eve again.

Hope this actually works.

---

### Post by Azriphale on 2006-12-11
WOOHOO!

I did this with Wine 0.9.25

I have Guild Wars (almost) playable. I just need to dl the cursor patch, and I will test EVE in a couple of days when I get another time code (being out of EVE Time sucks, btw). And then I can probably ditch windows on my desktop as well.

Thanks for a great howto!

---

### Post by Lost Ninja on 2007-02-07
I did everything as listed in the guide. I have patched to latest version.

How do I manually find the cache folder?

I am also unable to enter a password, any ideas as to what is wrong?

---

### Post by steevk on 2007-02-07
I followed the instructions to the letter, this is what I get:

> steev@steev-desktop:~/.wine/drive_c/Program Files/CCP/EVE$ wine eve.exe
fixme:process:IsWow64Process (0xffffffff 0x34fc24) stub!
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347a6c
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17c618) : stub, simulating 64MB for now, returning 64MB left
fixme:imm:ImmReleaseContext (0x20026, 0x1603b0): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34a950, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34a974, 260): stub


Running that command didn't help.


So I download msvcr80.dll and put it in my system32 folder, and I get this:

> steev@steev-desktop:~/.wine/drive_c/Program Files/CCP/EVE$ wine eve.exe
fixme:process:IsWow64Process (0xffffffff 0x34fc24) stub!
wine: Call from 0x7c4508dc to unimplemented function MSVCR80.dll._except_handler4_common, aborting
err:seh:setup_exception stack overflow 1188 bytes in thread 000e eip b7d19dc3 esp 00240b5c stack 0x241000-0x350000
[email]steev@steev-desktop:~/.wine[/email]/drive_c/Program Files/CCP/EVE$

Ideas?

---

### Post by Lost Ninja on 2007-02-08
> **Lost Ninja said:**
> I did everything as listed in the guide. I have patched to latest version.

How do I manually find the cache folder?

I am also unable to enter a password, any ideas as to what is wrong?

For reference for anyone else, I'll assume I'm not the only beginer here either: :D

Assuming also that you followed the OP's instructions, the cache file/directories should be @ /home/<username>/.wine/drive_c/Program\ Files/CCP/EVE/cache/

If the password is no enterable, apparently that was broken with patch 1.3, you need to copy arial.ttf from a windows install or [**here**](http://www.ocf.berkeley.edu/~gordeon/arial.zip) into the windows fonts directory. /home/<username>/.wine/drive_c/windows/fonts/

Obviously replacing <username> with whatever your username is, for me it looks like: /home/jc/.wine/... etc.

Hope that helps someone else.

---

### Post by b4t3m4n on 2007-02-08
I did this guide, but used the new 0.9.30 source and the 1-17-07 eve patch and everything worked fine.  The performance is semi questionable, 15-20 fps in space.  The big problem is I crash all the time with a single error that repeats itself over and over and over again.

```
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> 0x502 from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)

```

I using a nvidia 7900 with latest apt-get'ed drivers.

---

### Post by Zilulil on 2007-02-24
I'm very new at this... I just installed Ubuntu for the very first time.

i'm following the instructions and when i get to the 
```
wine EVE_Setup_####.exe
```
 part it doesn't work for me... mine is just EVE_Setup.exe and when i tell wine to run it in the command line i get
 ```
wine: could not load L"c:\\windows\\system32\\EVE_Setup.exe": Module not found
```

---

### Post by Cappy on 2007-02-25
The website says "as of the 15.02.2007 the git tree and >=wine-0.9.31 should contain all patches to play EVE"

I don't think you need to compile WINE from source and patch it anymore.

---

### Post by Cappy on 2007-02-25
> **Zilulil said:**
> I'm very new at this... I just installed Ubuntu for the very first time.

i'm following the instructions and when i get to the 
```
wine EVE_Setup_####.exe
```
 part it doesn't work for me... mine is just EVE_Setup.exe and when i tell wine to run it in the command line i get
 ```
wine: could not load L"c:\\windows\\system32\\EVE_Setup.exe": Module not found
```
You need to change to the directory EVE_Setup.exe is in.

---

### Post by potterzot on 2007-02-26
I'm so close.  It starts and loads, but the screen doesn't resize from teh login screen, and so I can only see a portion of the full thing.  Also, my gnome mouse is about 3-4 inches lower than the in game mouse, so I can't click on anything in the bottom 4 inches, which is everything :)

---

### Post by Scyphus on 2007-03-19
Splash screen shows up.

Then I get this far:
[ATTACH]27862[/ATTACH]
And the application hangs.

The only drivers I have available to me are the OSS drivers, unfortunately. I'm using onboard sound for an Asus A8N-SLI, and have a driver package downloading right now, but if anyone knows of a way to make the OSS ones work (other than the 'set to emulation' trick. I tried it, and it didn't work), or if this is something else entirely, please advise?

---

### Post by drj on 2007-03-22
Hello.  The client does the initial splash screen then goes black.  I look at the underlying terminal and find this message, repeated over and over until I kill the process:

"fixme:cursor:create_pixmap_cursor Currently no support for cursors with 32 bits per pixel"

So, I'm assuming the system I'm using has some sort of color depth challenge, but I don't know where, if anywhere, I can go to address the pixel depth the client is looking to use.  If I can lower the resolution, I might be able to go further.  It's a very old system, Dell Inspiron 1100, so I'm just glad I can get some basic OpenGL working and was just hoping for enough playability to do skills from remote sites.

Any thoughts, suggestions and/or insight would be greatly appreciated.

Thanks so much.

-dj

---

### Post by Nephtali on 2007-03-28
Hi everyone,

I meet troubles after downloading and installing (with Wine) successfully the EVE client.
I have an Ubuntu 7.04(unstable yet) an ati graphic card mobility radeon 9000, using the "ati" driver and wine 0.9.22

I have the same problem than pseudo.sanity, that is to say :

I try to run the EVE client by typing : wine /mypathtothefile/eve.exe -opengl 

it returns this :
libGL warning: 3D driver claims to not support visual 0x4b
fixme:process:IsWow64Process (0xffffffff 0x33fc34) stub!
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347adc

The nice picture of revelation (meaning that the client is loading) appears and 3 seconds after, a window entitled "Microsoft Visual C++ Runtime Library" where is said :
"Runtime Error!
Program: C:\Program Files\CCP\EVE\bin\ExeFile.exe
R6034
An application has made an attempt to load the C runtime library incorrectly
Please contact the application's support team for more information"

I tryed what Ipsissimus purposed :
[quote="Ipsissimus"]People having errors with the "msvcr80.dll" file I would say try running this:

Code:

wine ~/.wine/drive_c/Program\ Files/CCP/EVE/bin/RedistD3DXOnly.exe

As far as I can tell this creates the .dll files some of you are missing. After this, try eve again.

Hope this actually works.[/quote]

but it doesn't work ...  it returns :
```
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:SetWindowTextA setting text "RedistD3DXOnly Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "RedistD3DXOnly Setup" of other process window (nil) should not use SendMessage
libGL warning: 3D driver claims to not support visual 0x4b
fixme:reg:GetNativeSystemInfo (0x33fb38) using GetSystemInfo()
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33f628
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44
fixme:profile:GetPrivateProfileIntW result may be wrong!
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44
fixme:profile:GetPrivateProfileIntW result may be wrong!
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44

```

No way to run the client.

Does anyone has an idea concerning this trouble ? And even more, does anyone has a solution to allow me playing the best mmorpg of ever on my linux system ?

Thanks

---

### Post by somethingsin on 2007-04-18
Hey,
I ran trough the whole installation procedure, only for version 0.9.33 of wine, and the latest patch for EVE, found on the same site as the other one.
However, when I try to run EVE there's a error caused by missing D3DX.
Any way out of here?
Thanks

---

### Post by Tylo on 2007-04-28
Yes, probably. Run RedistD3DXOnly.exe
It is located in the **bin** folder in your Eve's install directory.

---

### Post by baseballguy on 2007-05-02
fixme:imm:ImmReleaseContext (0x10026, 0x160980): stub
fixme:imm:ImmReleaseContext (0x10026, 0x160980): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE


This is what I get. I get the entire client up and able to type in my account but I cant type in my password in. I click in the password section and I get the above results and I can not get anything to come into the password area. Any ideas.

---

### Post by godd4242 on 2007-07-24
> 
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2468 < primary_done=2472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2468 < primary_done=2472)
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1eb4a0
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=5180 < primary_done=5184)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3416 < primary_done=3420)



Aww hell

I have sound set to Emulate too, any ideas whatsup?

---

### Post by ipreferpi on 2007-07-27
> **Tylo said:**
> Yes, probably. Run RedistD3DXOnly.exe
It is located in the **bin** folder in your Eve's install directory.

I try to run that .exe, but nothing happens. at all.

---

### Post by insomnias on 2007-10-09
fixe the link please.


wget [http://ccp.vo.llnwd.net/o2/eve_setup_25245.exe](http://ccp.vo.llnwd.net/o2/eve_setup_25245.exe)
--16:48:35--  [http://ccp.vo.llnwd.net/o2/eve_setup_25245.exe](http://ccp.vo.llnwd.net/o2/eve_setup_25245.exe)
           => `eve_setup_25245.exe'
Résolution de ccp.vo.llnwd.net... 87.248.221.192, 87.248.221.194, 87.248.221.147, ...
Connexion vers ccp.vo.llnwd.net|87.248.221.192|:80...connecté.
requête HTTP transmise, en attente de la réponse...404 Not Found
16:48:35 ERREUR 404: Not Found.

---

### Post by insomnias on 2007-10-09
i found it here.


wget [http://ccp.vo.llnwd.net/o2/EVE_Setup_37459.exe](http://ccp.vo.llnwd.net/o2/EVE_Setup_37459.exe)

for fresh install

---

### Post by insomnias on 2007-10-09
wget [http://elfe.mine.nu/eve/linux/eve-2006-10-20.diff](http://elfe.mine.nu/eve/linux/eve-2006-10-20.diff)
--17:37:40--  [http://elfe.mine.nu/eve/linux/eve-2006-10-20.diff](http://elfe.mine.nu/eve/linux/eve-2006-10-20.diff)
           => `eve-2006-10-20.diff'
Résolution de elfe.mine.nu... 217.9.26.15
Connexion vers elfe.mine.nu|217.9.26.15|:80...échec: Connexion refusée.


another bad link fix it please !

---

### Post by cogadh on 2007-10-09
Dude, this thread is almost a year old. It's pretty likely that sites that originally hosted those files don't exist anymore, especially considering that a Linux native (sort of) client for Eve is currently in beta testing.

---

### Post by redmonster13 on 2007-10-10
Amazingly enough I got it running today on my ATI box \\:D/ and I am having trouble on my nvidia box. On the first one I had to mess with so many settings I dont know what finally made it work. I know that I had to edit the prefs.ini so that all the sound was disabled and my framerates arent very good. I think the framerate problem is due to the 9600xt and not the emulation.

If I get it working on the nvidia box tomorrow I will post how I did it and a link to the prefs.ini file.

---

### Post by InfSauce on 2008-09-22
Doesnt work, my patience with linux is wearing thin, im sorry to say... But I'm not giving up yet, this is fun. =)

---

### Post by Antiklontermiddel on 2008-11-13
Can someone please update the first post? I really want EVE to run nicely under WINE, as the Cedega version doesn't run EVE as smoothly as WINE is supposed to.

All I am interested in is the so-called hacks that are mentioned in the first post. They are not present anymore (404 File not found), and I do think they are somehow key to running EVE smoothly.

---

