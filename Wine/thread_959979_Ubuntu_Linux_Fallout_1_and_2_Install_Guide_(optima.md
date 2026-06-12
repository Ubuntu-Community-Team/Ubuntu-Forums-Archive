---
title: "Ubuntu Linux Fallout 1 and 2 Install Guide (optimal performance)"
date: 2008-10-26
forum: Wine
---

### Post by escapedturkey on 2008-10-26
Ubuntu Linux Fallout 1 and 2 Install Guide (optimal performance)

This guide assumes you are using Ubuntu Linux.

Small commentary:

There are ways to have different versions of Wine installed, however I recommend installing this version, than using CX Games for all other games. 

[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

CX Games is made by the main contributors of Wine, however their product allows isolated installs (bottles) and a variety of other options.

A good legal, downloadable, non DRM place to get Fallout 1 and 2:

[http://www.gog.com](http://www.gog.com) (Good Old Games)

This is both for Fallout 1 and 2:

Get wine 0.9.15 (also known to work better with other 8/16 bit 2D games)

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

[http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb)

You may need the following first:

[http://packages.ubuntu.com/gutsy/i386/libldap2/download](http://packages.ubuntu.com/gutsy/i386/libldap2/download)

If you get the libjack error. Do the following:

sudo apt-get install libjack0.100.0-0
sudo cp /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so

[http://ubuntuforums.org/archive/index.php/t-456002.html](http://ubuntuforums.org/archive/index.php/t-456002.html)

In Linux console:

Type winecfg

Set Windows version to Win2000.

Audio Tab:

Sound Driver - Uncheck all drivers - Checkmark OSS Driver
Hardware Acceleration - Emulation

Graphics Tab:

Checkmark - Emulate a virtual desktop
Desktop Size: 640 x 480

Libraries Tab:

Add ddraw as 'native/built-in'.

Click apply and then OK.

This is for Fallout 1:

Copy/Install Fallout 1 to Linux (using Windows or CX Games).

Install the following updates:

Fallout Patch 1.2 ENG TeamX (install this first)
Fallout Patch 1.3.4 ENG TeamX (install this second)

[http://www.nma-fallout.com/forum/dload.php?action=category&cat_id=12](http://www.nma-fallout.com/forum/dload.php?action=category&cat_id=12)

Also, install:

Fallout 1 v1.2 US (v1.18e, windows 2000/xp/vista)

[http://timeslip.chorrol.com/sfall.html](http://timeslip.chorrol.com/sfall.html)

This is for Fallout 2:

Copy/Install Fallout 2 to Linux (using Windows or CX Games).

Killap's Unofficial Fallout 2 Patch (US/UK - installer) 

[http://www.nma-fallout.com/forum/dload.php?action=category&cat_id=16](http://www.nma-fallout.com/forum/dload.php?action=category&cat_id=16)

Note: Killap's patch already includes sfall.

When running the game, make sure you cd /home/blah/gamedirectory

Then: wine game.exe

The mouse and animations should be smooth and fast in both games; as good as, possibly better than, Windows. If it's sluggish you did something wrong. :)

---

### Post by YokoZar on 2008-10-27
There's no need for the ancient Wine, the newer ones (and Wine 1.0) work well enough.

---

### Post by escapedturkey on 2008-10-27
You need 0.9.15 to have it work correctly.

[http://bugs.winehq.org/show_bug.cgi?id=6033](http://bugs.winehq.org/show_bug.cgi?id=6033)

As you can see by that bug report, 1.x and above are affected by the slow mouse / movement bug in Fallout 1 and 2. It started happening at wine 0.9.16. I talked to Stefan (sp?) from Crossover and he said he had a hack to work around that but it was never approved.

---

### Post by YokoZar on 2008-10-27
I've played through both games with the newer Wine (not full screen, but using 800x600 windows)

---

### Post by escapedturkey on 2008-10-27
Some of us, as pointed out in that Wine bug post, have problems with the mouse movement. This guide fixes that.

This is a great GUI script if you want to install multiple versions of Wine:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

:)

---

### Post by YokoZar on 2008-10-29
I can't remember, but doesn't the game have a built in mouse sensitivity control?  Does that help?

---

### Post by 080729jk on 2008-10-30
[**baidu&#20248;&#21270;&#20844;&#21496;**](http://www.bjbaiduyh.cn/baiduyhgs/index.html).&#35789;&#25105;&#37117;&#26159;&#25490;&#30340;[**&#21271;&#20140;google&#20248;&#21270;**](http://www.bjgoogleyh.cn/googleyh/index.html)&#27604;&#36739;&#21069;&#38754;&#12290;&#36873;&#20851;&#38190;&#35789;&#20063;&#19981;&#33021;&#29992;&#22826;&#20919;&#38376;&#30340;&#65292;[**&#21271;&#20140;baidu&#25490;&#21517;&#20844;&#21496;**](http://www.bjbaiduyh.cn/baidupm/index.html)&#36825;&#26679;&#23601;&#27809;&#26377;&#25628;&#20102;&#12290;&#25105;&#20204;&#35201;&#36873;&#30340;&#23601;&#26159;

---

### Post by escapedturkey on 2008-10-30
The mouse sensitivity doesn't help because it seems to skip frames a lot without this fix. I read it may not be as much a problem on dual core machines, etc, etc. However, if your machine isn't super fast (I'm using Asus 901 EEE), than this workaround is the only real way to do this -- until Wine is fixed. :)

---

### Post by giantoz on 2008-11-19
hi, Im having troubles playing fallout 2 in wine(1.1.5). ive been able to install the game (i used the humungous option because my copy is an iso),and went through the steps in this guide. but when i run the .exe i get an error saying "couldn't find/load text fonts".

as suggested by some people i looked at the fallout2.cfg file, but that seems to be in proper order.

also, on the wineapps page someone mentioned to another person with my problem that the cd needs to be properly mounted. im really not sure how i go about this-do i mount it normally and configure wine to the path? or do i somehow mount it in wine directly?  i did burn the image to cd, and wine seems to see the .iso in (wine's) D: drive,

ive even copied my truetype fonts(not the shortcuts to fonts) to the /windows/fonts in wine. to see if that worked

any help would be appreciated.thanks

ohyeah, im running hardy 64

---

### Post by giantoz on 2008-11-20
also, i do own the original/actual game, i just cant find it at the time (thats why im using the iso)

also, i wasn't really clear on the part of the guide "When running the game, make sure you cd /home/blah/gamedirectory" i made a folder in my home called fallout2, but im not too clear on how to change directories entirely.

ive tried to run wine fallout2.exe in the terminal, it said that it couldnt find fallout2.exe in /system32, so i copied fallout2.exe and stuck it in /system32 and i get a different error message saying "wine cant find directx-requires win95 with directx3.0 or nt with..."

and i still cant get the game to work!

---

### Post by YokoZar on 2008-11-20
> **giantoz said:**
> also, i do own the original/actual game, i just cant find it at the time (thats why im using the iso)

also, i wasn't really clear on the part of the guide "When running the game, make sure you cd /home/blah/gamedirectory" i made a folder in my home called fallout2, but im not too clear on how to change directories entirely.

ive tried to run wine fallout2.exe in the terminal, it said that it couldnt find fallout2.exe in /system32, so i copied fallout2.exe and stuck it in /system32 and i get a different error message saying "wine cant find directx-requires win95 with directx3.0 or nt with..."

and i still cant get the game to work!
When running the game from the terminal, you need to have the terminal's working directory be where the program is.  This will be something like:
*cd ~/.wine/drive_c/Program\ Files/BlackIsle/Fallout2*

Delete the copy of fallout2 you made in the system folder as well.

---

### Post by giantoz on 2008-11-20
> When running the game from the terminal, you need to have the terminal's working directory be where the program is. This will be something like:
cd ~/.wine/drive_c/Program\ Files/BlackIsle/Fallout2

Delete the copy of fallout2 you made in the system folder as well.

thank you for clearing that part up for me :)

however, i still get an error message "couldn't find/load text fonts" when trying to run the game

---

### Post by Aphotic on 2009-07-18
I am getting the same error message. I am curious as to where this gui script places all these different wine c drives. under winecfg, the 0.9.15 version lists it under ../drive_c .

I am thinking perhaps the solution is to install the game using the version of wine you want to run it under. I installed it with version 1.0.5 or w/e is currently being distributed via synaptic in jaunty, and had tried running it with the 0.9.15 binaries when I got the error.

I will let you know if I have any luck and if so, how I did it.

---

### Post by TPM on 2010-01-01
when i use ddraw.dll and change 
> ;Set these to 1 if you want fallout to access the keyboard or mouse in background mode

BackgroundKeyboard=0

BackgroundMouse=0
in ddraw.ini to 
> ;Set these to 1 if you want fallout to access the keyboard or mouse in background mode

BackgroundKeyboard=0

BackgroundMouse=1
i have no muse lag problem

---

### Post by Crispus K on 2010-01-13
I used this guide to install Fallout 1 on my machine and the game is up and running pretty damn smoothly in one of the newer versions of wine. I did have to tweak some things (not emulating virtual background so it goes full screen and different sound driver selected) Thank you for all the helpful information.

My question involves the 1.3.4 patch.  Assuming the directory and file name are correct, is this the correct script to run to install it?

$ tar xf fallout_patch_1.3.4.rar -C ~/.wine/drive_c/Fallout/

This is the only part I'm having trouble with. I originally just tried to decompress it directly into the game directory but where it says version 1.2 in the main menu did not update.  Any way to tell if the patch has been applied?  Any help would be much appreciated.  Love this game and thrilled to be playing it on my ubuntu laptop.

---

### Post by Tzah on 2010-02-04
Hoping this thread isn't too dead,
I've installed FO2 on one account,
it's not in the sudo list though and the only way I can get it to *almost*
function is by running it from the main user (su [myuser]);

```

[mainuser]@[name] su [myuser]
Password
[myuser]@[name]:~/.wine/dosdevices/c:/Program Files/BlackIsle/Fallout2$ wine fallout2.exe
No protocol specified
No protocol specified
No protocol specified
No protocol specified
XOpenDisplay() failed
No protocol specified
XOpenDisplay() failed
No protocol specified
XOpenDisplay() failed
No protocol specified
No protocol specified
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```and from the main user directly

```
[mainuser@[name] /home/[myuser]/.wine/dosdevices/c:/Program Files/BlackIsle/Fallout2$ wine fallout2.exe
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

```

But I keep getting these annoying error messages which I can't make any sense of,
and they always end in a pop-up 'Couldn't find/load text fonts'.

I've tried loads of guides and tips but I've no idea what's wrong.
It used to work fine from applications>wine>program files>black isle>fallout2>fallout2 but it started crashing after char creation and I was advised to run it through the terminal instead. As I am a nub to ubuntu it might be an 'obvious' mistake, but I appreciate the help.

---

