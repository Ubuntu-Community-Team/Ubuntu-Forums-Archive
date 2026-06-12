---
title: "Eve-Online for Ubuntu 9.04 64-bit???"
date: 2009-09-20
forum: x86 64-bit Users
---

### Post by CD27 on 2009-09-20
I just switched over to Linux full time now. I've dabbled in it before, but now I'm serious about sticking with it. Windows is just pissing me off more and more and I refuse to go to mac. I have put alot of time, effort, and money into the MMO game Eve-Online ([www.eveonline.com](www.eveonline.com)). Unfortunately they only have installers for windows and mac and there's an unofficial one for linux but I'm using ubuntu and not the version they were speaking about in the tut i read on google.

I installed vbox and installed eve-online in there, but I'm not getting anything from it. It starts up like normal, but before it even gets to the login screen the whole thing goes invisible except for the the title of the app at the bottom of the start bar (showing active apps that have been minimized or are open). I click it and it acts like it's opening, but doesn't show anything.

Is there a way to get it to work with vbox or is there a method of getting this to work on Ubuntu?

---

### Post by Ms_Angel_D on 2009-09-20
Did you try looking at wine? From what I've read in my short google they discontinued support for the Linux client last March [http://www.linux-gamers.net/modules/news/article.php?storyid=2532](http://www.linux-gamers.net/modules/news/article.php?storyid=2532).

Here's the page in wine's appdb for ubuntu 9.04 64bit

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15922&iTestingId=44035](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15922&iTestingId=44035)

If your like me you may wish to avoid editing by hand, and try a couple of front ends for wine first. The first free one that comes to mind is [Play On Linux]("http://www.playonlinux.com") But if that doesn't work or you have issues, then I suggest trying just wine.

If you don't mind paying there's also [crossover]("http://www.codeweavers.com") & [Cedega ]("http://www.cedega.com/")

---

### Post by CD27 on 2009-09-20
Well, I don't want to pay any more than I already have, which is alot, just for the game. I've tried using wine, and it runs the installer, but it won't download the files it needs to install and errors out.

---

### Post by Artemis3 on 2009-09-20
I wonder why people ask about general Ubuntu issues on Eve's forums, and come to Ubuntuforums to ask about running Eve :P

Anyway: [http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463](http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463)
[I wrote this](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1007680) a while ago, most of it still applies, make sure you change "intrepid" with "jaunty" when you add wine repos.

In short: It runs with [Wine](http://www.winehq.org/), **current** wine (1.1.27+).

> **CD27 said:**
> I've tried using wine, and it runs the installer, but it won't download the files it needs to install and errors out.

That thing actually works, if you try it many times, but i don't like the process it leaves running behind... So, instead, download the [full installer](http://www.eveonline.com/download/?fallback=1&).

---

### Post by CD27 on 2009-09-20
I'll most definitely have a look at this after work. I posted the thread here because the eve forums have utterly horrible layout. There's no way I could have a link emailed to me, and I would have to literally search for the thread by exact name. It's rather annoying. I've given up posting in that forum long ago.

But thank you again for the links, I will definitely be trying this out. I'll get back with you here as far as how it goes and if I have any questions for problems.

-CD

---

### Post by CD27 on 2009-09-20
Alright, I've downloaded the package you showed there, and went to your thread on eve, but when i ran the first code:

```

glxinfo | grep rendering

```

This is the response I got:

```

psinetic@Psinetic:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
psinetic@Psinetic:~$ lspci -v | grep VGA
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
psinetic@Psinetic:~$ 

```

My graphics card supports SLI, but I only have one so I don't even have it setup, nor need it for that matter.

When I did this part of your tutorial, it told me the file didn't exist:

```

Modify user.reg: Append the following to ~/.wine/user.reg (hit alt-f2 and type gedit ~/.wine/user.reg)

[Software\\Wine\\Direct3D]
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="256"

```

When I double click the installer for the .exe, it shows on the task bar "opening ~name~.exe" and then just goes away and I never see anything more of it. It doesn't install anything at all.

---

### Post by Artemis3 on 2009-09-21
That glxinfo result shows there is a problem with your 3d, possibly don't have the driver enabled, or you installed the driver by hand and failed to install it again after a kernel update.

If you install Ubuntu 9.04 fresh, your 3D should be working without you doing anything. As you can see, i happen to have the same card.

Until you fix your 3d, you may not continue with the guide.


If the fIle ~/.wine/user.reg does not exist, it could mean you failed to do the previous step: 
> # Configure wine: in a terminal or alt-f2 type: padsp winecfg
Audio settings in winecfg are set to: OSS Driver; Hardware Acceleration: Full; Default Sample Rate 48000; Default Bits Per Sample: 16; Driver Emulation: enabled. This step populates ~/.wine

---

### Post by CD27 on 2009-09-21
I have been dealing with this graphics problem for the past few days, and I have no idea how to fix it. I don't like to have to keep reinstalling the OS, it gets rather annoying and tedious after a while (and I've done several reinstalls too many as it is). I've been round-about with this one driver so many times my head hurts from it.

I did all of the steps, step by step as instructed in the guide. If it didn't populate the file then I have no idea why, but I did the step.

---

### Post by CD27 on 2009-09-21
I just got my graphics to work properly now with the following thread at post #25:

[http://ubuntuforums.org/showthread.php?t=909460](http://ubuntuforums.org/showthread.php?t=909460)

So now i'll see if it works out.

---

### Post by CD27 on 2009-09-21
Alright, so I was able to install it and configure it and everything. I couldn't get a chance to play yet because it just so happens to be downtime at the moment. HOWEVER, I just ran into another problem. For some reason Eve crashed, ok, crap happens. Looks like, actually, all my graphics crashed. So I went back into appearances and put my graphics back from none (where it wasn't supposed to be) back to "extra" (where it was put at to begin with). I went to run even, and I got this error:

```

Error
Could not launch "Play Eve"
Failed to change to directory '/home/psinetic/.wine/dosdevices/c:/windows/temp/nsl6341.tmp' (No such file or directory)

```

Any idea what this means or what I would have to do in order to solve it?

-CD

---

### Post by CD27 on 2009-09-21
Alright, I decided just to wipe and reinstall the OS entirely, get rid of some of the leftover junk that's been mistweaked here or there and do it right the first time. Graphics worked the first time without having to make any adjustments, which is awesome. Everything else is working as well, had to turn up my volume as usual (which is kinda gay), and i'm installing eve right now. So i'll respond again to this thread when everything is done to see if there's anything i missed or might have done wrong if it doesn't work this time. thank again for all of your help.

-CD

---

### Post by CD27 on 2009-09-21
Ok so I followed the steps as shown in that tutorial. The first one I just used the complete download. It kept telling me it wasn't working and errored out, and then i realized i wasn't using the shortcut you told us to make. So i used that, and it worked fine, but it go to the main page, and the graphics are all kinds of jacked up. The license page I can't even scroll down to complete, the menus for the settings pages I can't even see half of the buttons. So it was pointless, I couldn't do anything with it.

So then I tried the regular installer you pointed to in your tut there, and it was taking so long I just went to sleep and woke up to this error:

```

Validation failed. Expected checksum is f9276eda4bc57280a53f56c91000b50b but was 2d8e7a12b3d457fdd5162c6481d2dee4

Click here to download manually

```

I'm really lost at this point on exactly what's wrong, any ideas? Did I miss a step or something, or input something wrong or i dunno.

-CD

---

### Post by Artemis3 on 2009-09-21
The validation almost always fail at the end of the install/update, so that really doesn't matter. It should run just fine.

The full installer also works, maybe you didn't download all the data? check the file size carefully.

The "other" installer iirc uses bittorrent dna to download the very same full installer you should have downloaded earlier, which is the process that eats all your bandwidth if you leave it running. I think it goes somewhere under ~/.wine/drive_c/windows/profiles/yourusername/local configuration?/Application data?/CCP/EVE/c_program_files_ccp_eve_tranquility/cache (these folders are tricky because most of them change name with your locale, i have no idea how they are called in japanese ^^!)

---

### Post by CD27 on 2009-09-21
I took screen shots of it for you to see what i'm talking about. It is rather annoying, but I do have one question that may have something to do with this.

In the eve tut ([http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1007680](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1007680)) it has a part here:

```

Modify user.reg: Append the following to ~/.wine/user.reg (hit alt-f2 and type gedit ~/.wine/user.reg)

[Software\\Wine\\Direct3D]
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="256"

Change the VideoMemorySize value to the size of your video ram.

```

Now I don't know my videomemorysize value, so I just left it the way it was (I assumed, that since we both have the same card, that the number would be the same as well), would this have anything to do with why my screen looks the way it does when i launch eve? 

EDIT: I was able to figure out my correct size and correct it. it was 512. But it didn't chnage anything, so the pictures remain the same.

Also, when configuring wine, i don't have the option to check "Driver Emulation: enabled."


[ATTACH]129329[/ATTACH]

[ATTACH]129325[/ATTACH]

[ATTACH]129326[/ATTACH]

[ATTACH]129327[/ATTACH]

[ATTACH]129324[/ATTACH]

---

### Post by CD27 on 2009-09-25
...:confused: it's still not working.

---

### Post by CD27 on 2009-09-26
is anyone going to respond?

---

### Post by CD27 on 2009-09-27
Alright, so searching google for HOURS on end (no thanks to anyone here for not replying for days), I found this:

[http://thelinuxbox.org/downloads/fonts/msttcorefonts.tar.gz](http://thelinuxbox.org/downloads/fonts/msttcorefonts.tar.gz)

That's the link to the arial font. Apparently you can't accept the EULA to get to the login page because you can't see it. You put those files (not the folder, the files in the folder) int he following file path:

/home/yourusername/.wine/drive_c/windows/Fonts

After that, run your desktop app and it should let you login.

The next thing I found was I wanted the game to be completely fullscreen. It's kinda annoying having part of my screen cut off due to the taskbar and I didn't want the little orange title bar either. I wanted a completely fullscreen mode.

You can easily do this in Compiz (I had to play around with it a few hours).

Open up compiz Configuration
System->Preferences->CompizConfig Settings Manager

Then go to Windows Rules (should be at the very bottom)

In the "Matches" tab under the following:

Skip Taskbar
Fullscreen

Copy and paste the following command:

```

(all) | name=explorer.exe

```


Make note: This will make it fullscreen alright, but if you don't have anything to alt+tab to, you'll have to shutdown the game in order to get back to your desktop. I was able, however, to get back to my desktop via alt+tabbing to amsn messenger.

Another thing: It'd probably be best for you to log off the game initially rather than quit game (My entire computer up and froze completely when i just quit game), and then you alt+f4 while the blue screen shows before eve reloads itself (or just set eve to not reload after logoff).

---

### Post by Sophont on 2009-09-27
Hi - just stumbled into this thread.
I've been playing EVE Online on Linux for years - it usually works fine. Occasionally an update makes it incompatible - but it usually only takes at most a few days for some hacker to provide a patch to wine and it's rare to begin with.

There is a Linux EVE Forum: 
[http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463]("http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463")

Please note the sticky with pointers to EVE Wiki entries etc...

Apart from a current wine install you need to install mstcorefonts (for Arial - so that EULA screen works) and a few wine settings that I see were already mentioned above. All explained in that forum and EVElopedia entry.

The rest depends on your graphics card. In general NVidia with proprietary drivers works almost fine. With ATI cards it's more a matter of the particular model and the drivers are heavily in flux. The next few months promise to bring great advances on the ATI front.

---

### Post by Artemis3 on 2009-09-28
Looks ok except for the EULA. Do you have the fonts in ~/.wine/drive_c/windows/fonts ?

Did you install DirectX with winetricks?


Nvm if you solved it. All your issues are covered in my guide you said you read. There were steps for winetricks install of both fonts and directx.

---

