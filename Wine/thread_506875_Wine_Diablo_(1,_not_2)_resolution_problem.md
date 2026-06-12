---
title: "Wine Diablo (1, not 2) resolution problem"
date: 2007-07-22
forum: Wine
---

### Post by El Lance-O on 2007-07-22
Ok, so I have searched high and low for an answer, but all I can find is threads related to Diablo 2 or LOD, which is not what I need help with.

Everything works fine, I fixed the menu with the hacked ddraw.dll that is provided on the Wine App HQ tutorial, but there is just one last problem.

Whenever I run it in fullscreen (I am using a Dell Inspirion 1505n at 1280x800 resolution) it cuts off a lower section of the screen so I am unable to see the dialog box and other buttons.

It is fine when I run in as a window, but it's at 640x480, which isn't very pleasant to play in.

I have tried everything, running it under a virtual desktop at my screen resolution, but it doesn't matter what resolution I make it, it always comes up at 640x480.

Alt-Enter doesn't work, resizing doesn't work, NOTHING WORKS.

I even tried the 'wine explorer /desktop=name,1024x768 program.exe' command with no luck, it won't even start then.

So please, can someone, PLEASE help me solve this so I can play it fullscreen? This game was a major aspect of my gaming childhood and I would really, REALLY like to revisit it.

Edit: When I tried to take a screenshot of it fullscreen, it didn't cut off the bottom so I think the problem is that it's not setting the screen position correctly.

Edit 2: I realized that the 'wine explorer /desktop=name...' command does work, but still opens it at 640x480. It didn't work before because I had the wrong ddraw.dll in the Diablo folder at the time I tried it.

---

### Post by Nkari on 2007-07-22
That game only ran at very low resolutions in its native windows environment out of the box, Diablo 2 came out with an 800x600 option and that was touted as a big improvement over the original game.

So maybe have a look and see if there are ways to make it run at higher resolutions under windows first then apply those findings if there are any.

---

### Post by cogadh on 2007-07-22
Diablo's maximum resolution is 640X480, you can't set it any higher than that. Judging by your stated resolution, you appear to have a widescreen monitor, which brings in even bigger issues. Your monitor has an aspect ratio of 16:9 while the game has an aspect ratio 4:3. Since the game cannot do higher than 640X480 and it can't do the wide screen aspect ratio, the only way you will be able to play it correctly is in windowed mode. You can offset the resolution a bit by setting your desktop resolution to the lowest it can do (as long as it is equal to or higher than 640X480), that way the window will be as close to full screen as possible.

---

### Post by El Lance-O on 2007-07-22
I appreciate the responses, but you obviously didn't read the last 2 edits I posted.

The resolution is fine, nothing wrong there at all. Sorry for the misinforming title, but I didn't realize it until after I made the thread. It's just the position that the game is mapped to on my screen, so it is too far down. There is no black areas or anything, the whole screen is filled. It's just an issue of it being positioned incorrectly.

And I have tried using different resolutions, including the native 640x480 but no difference, there is still a cutoff.

So I am looking for either a wine argument line I can put in when running it or something to that extent to reposition it.

---

### Post by cogadh on 2007-07-23
It might not be Wine, it could be you xorg.conf file. It sounds kind of like when you have it configured with a virtual desktop size that is larger than the currently viewed resolution. You might want to review your xorg.conf file for any odd configurations of viewport or virtual entries. Sorry I can't be more specific, I'm not in front of my 'buntu box right now and can't reference my own for the details.

---

### Post by El Lance-O on 2007-07-23
Well the probably only arises when I don't use the virtual desktop option in winecfg. It forces itself into 640x480 whenever I use that option, as I stated in my first post.

But here is parts of my xorg.conf file that would be relevant:

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Looks like everything is fine to me?

---

### Post by cogadh on 2007-07-23
Well there's the problem. Wine can only set resolutions that are already present in your xorg.conf file. Since you don't have the 640X480 resolution available in your xorg, it is likely choking when it tries to set the default resolution while you are not using the "Emulate virtual desktop" option. If your monitor is capable of 640X480 resolution, add that to 8, 16 and 24 depth subsections under "Screen" and then try launching the game.

---

### Post by El Lance-O on 2007-07-23
Nope, still the same problem.

I got really excited there too haha!

But thanks for all of your help so far.

So what should I do now?

---

### Post by cogadh on 2007-07-23
I forgot a step, you have to restart the Xserver after changing the xorg.conf (log out, CTRL-ALT-BACKSPACE, log back in). Did you do that  before trying the game again?

---

### Post by El Lance-O on 2007-07-23
Yup, sure did.

I hope you aren't running out of ideas... :(

---

### Post by cogadh on 2007-07-23
Not out of ideas yet, but I need to think about this a little more. The solution is probably something way too obvious that we are both missing. I'll do a little messing around on my system and see if I can come up with anything new.

---

### Post by El Lance-O on 2007-07-23
Yeah it seems like it would be an easy fix, I thought using a line argument like -w 640x480 would work, but it didn't, so I assumed that there would be an argument similar to that which would work.

I really hope you can get it to work as I really want to play Diablo again, I love nostalgia with video games!

---

### Post by El Lance-O on 2007-07-26
Any luck?

---

### Post by cogadh on 2007-07-26
No, not yet, but I keep coming back to the monitor resolution as the possible source of the problem. Now that you have added 640x480 to your xorg.conf, what happens if you set your desktop to that resolution? Does your desktop have the bottom few lines cut off like the game?

---

### Post by El Lance-O on 2007-07-26
Yeah I already tried that, you suggest it to me earlier, still no luck :(

It's even worse now, wanting to play it that is. I just found an alpha version of Diablo that has a bunch of stuff that was taken out in the retail version. :)

---

### Post by El Lance-O on 2007-08-01
Seeing as it's been 5 days, I don't expect that you figured it out. :(

Woe is me.

---

### Post by rjfioravanti on 2007-08-13
how did you get the game to run?

I get stuck after installing when I boot it up

Also, I run my monitor at 60hz refresh rate, or else it complains and eventually shuts off. Wine always changes my refresh rate to 85hz when i start a game, how do i get it to leave my refresh rate alone when changing the resolution to game size

---

### Post by El Lance-O on 2007-08-14
Well you have to get the hacked ddraw.dll file from the Wine App DB entry for Diablo for to even get past the first Blizzard logo.

I can get it to work now if I hook it up to my TV, change the resolution to 640x480, and then get annoyed by icons flashing on my toolbar.

It's actually quite ridiculous, and makes me not want to play it at all really.

---

### Post by rjfioravanti on 2007-08-14
I found the ddraw and everything was fine

I am using a square monitor though

I am also using wine version 43

---

### Post by Sammi on 2007-08-14
@El Lance-O
Why don't you just use the "emulate virtual desktop" function in winecfg to fool Diablo in to running in window mode?

---

### Post by El Lance-O on 2007-08-15
If you read my first post, you'll see that I already tried that.

---

### Post by cor2y on 2007-08-15
I had the same problem with the original fallout , Anachronox and Septerra Core, stumbled upon the answer by accident.
It worked for all 3 games and it might work for you.
Disable the virtual desktop in winecfg.
The games will then run in fullscreen.
If you had the bad luck to be running an ATI card and you are using XGL to run compiz/beryl/compiz fusion you will have to enable meta city to be able to play in fullscreen otherwise you get weird transparent problems.

---

### Post by Sammi on 2007-08-16
> **El Lance-O said:**
> If you read my first post, you'll see that I already tried that.Yes I read that. Only I don't understand what the problem is. Doesn't it run, when you configure Wine to use an emulated desktop?

---

### Post by El Lance-O on 2007-08-16
Alright...

YES, when I use a virtual desktop, it DOES work. BUT, it is in 640x480 resolution, making it pretty difficult to play in such a tiny window.

YES, I have tried disabling the virtual desktop option.

THE WHOLE PROBLEM IS THE FACT THAT IT DOES NOT RENDER CORRECTLY IN FULLSCREEN. IT CUTS OFF A PORTION OF THE BOTTOM HALF.

When I say FULLSCREEN, I mean, NO WINDOW TITLEBAR, NO TOOLBAR, F U L L S C R E E N.

And no, I am thankfully not on an ATI card, but a Nvidia 7300 that came with my pre-loaded Inspiron 1505n. And I already tried running it in Metacity, and I usually do this when playing games because running beryl either makes things choppy or just slow.

I'm sorry if I sound all angsty, but I made all of these things pretty clear on the first page. Read the posts people.

But thank you for the replies! At least you guys are trying to help, and I do appreciate it.

---

### Post by Sammi on 2007-08-17
I have no experience with running Diablo in Wine, and I have no real solution for you.

But I do think that I can offer a workaround. That would be to lower the resolution of you entire gnome desktop, so tað the tiny (640x480) diablo window would be bigger.

I actually own Diablo. Haven't played it for years. Maybe I'll dust it off and try it out. I actually have a Dell Inspiron 9300 with a Nvidia and native resolution of 1440x900. Maybe I'll encounter the same problem.

---

### Post by ekravche on 2008-03-30
I'm having problems with a black screen. There is a link to a hacked ddraw.dll in this thread [http://bugs.winehq.org/show_bug.cgi?id=2082](http://bugs.winehq.org/show_bug.cgi?id=2082), however I don't want to screw up wine for other games just to get diablo 1 working. It's a shame... Another alternative is to go to the link above and vote for that bug to get fixed. You'll need an account to do that, so just register and vote for the bug and eventually it will get resolved.

Thank you in advance.

---

### Post by Sammi on 2008-03-31
Was it really in August I said I was going to try Diablo again?

Still haven't done it...

One of my favorite tread on the forums: [Procrastinator's Guide to Ubuntu]("http://ubuntuforums.org/showthread.php?t=371500") :lolflag:

---

### Post by ekravche on 2008-04-01
> **Sammi said:**
> Was it really in August I said I was going to try Diablo again?

Still haven't done it...

One of my favorite tread on the forums: [Procrastinator's Guide to Ubuntu]("http://ubuntuforums.org/showthread.php?t=371500") :lolflag:

It still doesn't work without hacking it...

---

### Post by ekravche on 2008-04-06
THe process of how to get diablo I working with the ddraw.dll can be found here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498) . I've tried it, but there is no existing ddraw.dll for 0.9.58, and you'll need to compile the ddraw.dll from scratch if you want to get it working...

---

### Post by ekravche on 2008-04-06
Here is what I did to solve the problem partially.

First you'll need to get the source code for your version of wine. So if it's 0.9.58, get the 0.9.58 version of the source code.

Then get the patches attached to this post.  placed them in the base directory of the wine source. And run the following commands


> patch -p0 &#5176;wa_ddraw.patch

Now, you'll need to install bison, flex, gcc, and make. Usually the system comes with those. Then go into the dlls directory and run

> make ddraw

That will build your direct draw which you can use to run diablo. You'll need to take the built ddraw.dll.so and rename it to ddraw.dll, and then place it in your diablo directory. 

The only problem that I found was that it runs slowly...

I'm attaching the ddraw.dll for wine 0.9.58 in the case that you are using wine 0.9.58.

Best regards

---

### Post by Vuen on 2008-07-04
Sorry for reviving an old thread, but I just encountered this problem as well and, having found the cause without any documentation of it online, I thought I'd offer an explanation here.

It's due to a bug in the nvidia-glx drivers. It seems that if you set your resolution to anything 4x3 with a widescreen monitor, it scales it wrong and chops off the bottom of the screen. This has nothing to do with wine; just changing the resolution of X to 4:3 causes this bug. I'm not sure how widespread this bug is; for the record, I have an NVidia 6600 GT.

If you change your display driver back to "nv", it scales just fine. Unfortunately it's not much of a solution, since this precludes the use of 3D (this also means for the case of Diablo II that you have to use 2D mode), and it's not exactly convenient to switch video drivers for running different games. Still, I thought after all this time you might finally like an explanation for why this was happening.

My suggestion would be to complain loudly at NVidia about this, and make your next video card purchase from ATI. Show them that you support open source video drivers. I know I will.

---

### Post by pizpot on 2008-08-03
I have a desktop with a nvidia 6200 and native widescreen of 1680x1050 and a laptop with a nvidia 8600M GS and native widescreen and my popcap games are cut off at the bottom on both computers. Ubuntu 8.04, nvidia drivers not nv. 

Knowing that my 8600 is guarenteed to melt, and all the recent nvidia driver bugs (old games!), I am going ATI next time, for the first time since 15 years.

---

### Post by Found on 2009-07-18
Um...if anyone will still have this problem.
I managed to solve it. After installing Diablo you need get ddraw.dll and apply it in regestry. Find your current wine version and download it [http://glados.iwanek.co.uk/dokuwiki/projects/wine-hacks]("here").

There's two files *.dll* and *.reg*. You should put *.dll* in your:
```
/home/<username>/.wine/drive_c/windows/system32
```
and apply the reg file by doing following:
```
regedit hack.reg
```
Afterwards, in Wine Configuration Tool, in Applications tab, you should add your *hellfire.exe*.

If you ever changed the DirectDraw to opengl, you should change it to default which is GDI.
In terminal:
```
regedit
```
Navigate to *HKEY_CURRENT_USER\Software\Wine\AppDefaults\hellfire.exe*
Create new key called *Direct3D*. Then create a new string called *DirectDrawRenderer*, assing a key *gdi*. And close it.

Now you should be able to run it in fullscreen without statusbars or anything that migh distract you. :)

---

### Post by El Lance-O on 2010-05-27
Oh, I'm bringing it back. Wayyyyy back. :)

Here it is, several years later, and I am still, having the same issue. Bum luck or what? I recently discovered The Hell mod, and decided to try it out, to the dismay of experiencing the same haunting symptoms from years ago.

The one person that really stuck out even getting close to the problem was Vuen:

> **Vuen said:**
> Sorry for reviving an old thread, but I just encountered this problem as well and, having found the cause without any documentation of it online, I thought I'd offer an explanation here.

It's due to a bug in the nvidia-glx drivers. It seems that if you set your resolution to anything 4x3 with a widescreen monitor, it scales it wrong and chops off the bottom of the screen. This has nothing to do with wine; just changing the resolution of X to 4:3 causes this bug. I'm not sure how widespread this bug is; for the record, I have an NVidia 6600 GT.

If you change your display driver back to "nv", it scales just fine. Unfortunately it's not much of a solution, since this precludes the use of 3D (this also means for the case of Diablo II that you have to use 2D mode), and it's not exactly convenient to switch video drivers for running different games. Still, I thought after all this time you might finally like an explanation for why this was happening.

My suggestion would be to complain loudly at NVidia about this, and make your next video card purchase from ATI. Show them that you support open source video drivers. I know I will.

I've tried using the nvidia-config tool use a number of combinations with the scaling options under GPU Scaling Method and Flat Panel Scaling. Nothing works.

When using 'Aspect Ratio Scaled', I get an interesting result of the image overlapping itself several times. I really wish I could get a screenshot of this, but strangely, when I take a screenshot it looks absolutely fine.

> **Found said:**
> Um...if anyone will still have this problem.
I managed to solve it. After installing Diablo you need get ddraw.dll and apply it in regestry. Find your current wine version and download it [http://glados.iwanek.co.uk/dokuwiki/projects/wine-hacks]("here").

There's two files *.dll* and *.reg*. You should put *.dll* in your:
```
/home/<username>/.wine/drive_c/windows/system32
```
and apply the reg file by doing following:
```
regedit hack.reg
```
Afterwards, in Wine Configuration Tool, in Applications tab, you should add your *hellfire.exe*.

If you ever changed the DirectDraw to opengl, you should change it to default which is GDI.
In terminal:
```
regedit
```
Navigate to *HKEY_CURRENT_USER\Software\Wine\AppDefaults\hellfire.exe*
Create new key called *Direct3D*. Then create a new string called *DirectDrawRenderer*, assing a key *gdi*. And close it.

Now you should be able to run it in fullscreen without statusbars or anything that migh distract you. :)

The issue was not status bars at all other than when using a virtual desktop, which is not an issue now. I tried using it again, and the menu will not show up. The only thing that made the menu choices appear was having Compiz or compositing in Nautilus running. The Direct3D hack does not change anything at all, and yes I followed all the instructions.

I would really love someone to come along and explain a way to do this. If you google "wine diablo" this is the second thread that appears with over 6000 views. Must mean something?

Now lets revive this and END it PROPER! :guitar:

---

