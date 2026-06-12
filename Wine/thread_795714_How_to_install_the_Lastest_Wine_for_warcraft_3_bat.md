---
title: "How to: install the Lastest Wine for warcraft 3 battle.net hosting in Hardy"
date: 2008-05-15
forum: Wine
---

### Post by zir0n on 2008-05-15
Hi all, I've done more tinkering and got the latest wine-1.0-rc1 release candidate working with Warcraft 3 TFT. It works very stable and with the addition of two patches you can host custom games on Battle.net and switch desktops without crashes, the two problems that kept me in the dark ages of wine due to the fact I needed to switch desktops from the game I hosted for Skype calls to coordinate ganks. I'm updating my old How-to from installing wine 0.9.45 to the latest because running the old wine gave me performance issues with my other wine apps like Photoshop which are fixed in the latest. In this How To you will be compiling from source in order to apply two patches to fix the problems. I am already assuming you have Warcraft III and TFT installed with the updates and are running it using the -opengl option append to the end of the command you use to run warcraft 3. If you are having trouble with the new B-Net Update because it's asking you to insert the CD, please refer to this thread. [Warcraft 3 TFT asks for CD after patch?]("http://ubuntuforums.org/showthread.php?t=847508")

[COLOR="RoyalBlue"]Step 1:[/COLOR] Make sure to remove your current wine if you have it installed.

```
sudo apt-get remove wine
```

or

```
sudo make uninstall
```

in the directory of your prior wine build, if you compiled wine from source.

[COLOR="RoyalBlue"]Step 2:[/COLOR] You will be compiling things in this "How to" so run.

```
sudo apt-get install build-essential
```

if you haven't already. You might need the kernel header files as well, as I had them installed for something else and didn't know if wine used them also.

[COLOR="RoyalBlue"]Step 3:[/COLOR] Download and unzip the latest wine, as of now wine-1.0-rc1.tar.bz2 source code from 

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449) 

[COLOR="RoyalBlue"]Step 4:[/COLOR] Install the build dependencies for wine.

```
sudo apt-get build-dep wine
```

[COLOR="RoyalBlue"]Step 5:[/COLOR] Enter the wine-1.0-rc1 directory and type

```
wget http://bugs.winehq.org/attachment.cgi?id=12913 -O desktop_switching.patch
wget http://bugs.winehq.org/attachment.cgi?id=8368 -O hosting.patch

```

[COLOR="RoyalBlue"]Step 6:[/COLOR] Patch sync.c and event.c to fix the hosting problem and desktop switching problem by entering

```
patch -p1 <desktop_switching.patch
patch -p1 <hosting.patch

```

[COLOR="RoyalBlue"]Step 7:[/COLOR] Run 

```
./configure
``` 

installing anything you're missing using "apt-get install"

[COLOR="RoyalBlue"]Step 8:[/COLOR] Hopefully you have all your make files made.

```
make depend && make wine
```

[COLOR="RoyalBlue"]Step 9:[/COLOR] Cross you fingers for 30mins-1hr...

[COLOR="RoyalBlue"]Step 10:[/COLOR] If you made it this far, prepare for Warcraft 3 Battle.net heaven and type...

```
sudo make install
```

[COLOR="Red"]*keep the wine-1.0-rc1 directory if you want to uninstall your built wine using "sudo make uninstall"[/COLOR]

[COLOR="RoyalBlue"]Step 11:[/COLOR] Test your (re)gained game hosting abilities by hosting and playing some DOTA!!!

[COLOR="RoyalBlue"]Getting an Autorefresher to work in Ubuntu:[/COLOR]
So after being able to host games, you're now lazy and don't want to close and open slots. Fret no more, there's an autorefresher that works in Linux. Grab it here...

[http://www.hiveworkshop.com/forums/resource.php?t=62965]("http://www.hiveworkshop.com/forums/resource.php?t=62965") 

then run

```
sudo apt-get install libmono-winforms1.0-cil libmono-winforms2.0-cil
```

and run the extracted executable with

```
mono WarcraftIIIAutoRefresh.exe
```


[COLOR="Red"]**Disclaimer:[/COLOR] I know I didn't hit 13 steps this time. I am not a wine developer, but I did have a lot of help from Shae getting the latest wine to run smoothly. I myself haven't had any problems with Warcraft 3 and hosting in Battle.net after using this method. Again, Thanks to Shae, the people over at Wine, and the Wine hackers who created these patches. If you have problems please reply to this thread and I will try to help you.

---

### Post by Kinst on 2008-05-15
Hey that's cool, are the patches going to be included in wine in the future?

---

### Post by cogadh on 2008-05-15
Eventually, but Wine is in code freeze right now, so they are only addressing regressions that caused previously functional games and apps to stop working. IIRC, getting Battle.net working is one of the things left on the 1.0 bug list (i.e. the things that must be fixed before 1.0 is released)

---

### Post by Troll_the_Great on 2008-05-20
Maybe this is a silly question, but the cracked Warcraft works with these settings?

---

### Post by shae on 2008-05-20
These patches will never be included in the source.  This is because the problems are caused by incomplete features with wine.  In the future, they will no longer be needed as they finish the incomplete features.

There is no need to use a cracked version of warcraft because the latest patch (1.21d) disabled the cd check anyway.

---

### Post by zir0n on 2008-05-21
As said earlier, the battle.net issue is one of the bugs they will fix before the final 1.0 release, here is the list of the bugs left as of May 18th. the Warcraft 3 one is near the bottom.

[http://wine-review.blogspot.com/2008/05/wine-10-release-status.html]("http://wine-review.blogspot.com/2008/05/wine-10-release-status.html")

---

### Post by purewater08 on 2008-05-21
Great HOWTO! But i dont wanna fix it so i wont spend too much time playing DOTA :)

---

### Post by SilverDragon on 2008-05-21
> I am already assuming you have Warcraft III and TFT installed with the updates and are running it using the -opengl option append to the end of the command you use to run warcraft 3.

I was just curious why you use the -opengl option?

I thought  people only used that on lower end machines that have trouble running the game.

Will it effect the patching process outlined in your How-to?

---

### Post by Redmumba on 2008-05-22
I'm guessing its because the normal run mode is using DirectX?  Just a guess. :)

---

### Post by zir0n on 2008-05-22
> **SilverDragon said:**
> I was just curious why you use the -opengl option?

I thought  people only used that on lower end machines that have trouble running the game.

Will it effect the patching process outlined in your How-to?
If your warcraft 3 works fine using the emulated DirectX, then thats fine too. It shouldn't have any effect on the patching process. I use the -opengl option because i have an old laptop.

---

### Post by shae on 2008-05-22
So everyone can spend more time playing dota I went ahead and applied the patches and sat up my own PPA at launchpad to host the packages.  I still have not decided on a naming convention, but I have the rc1 building right now.  For information and the appropriate apt lines, see my PPA page:

[https://launchpad.net/~starfall87/+archive](https://launchpad.net/~starfall87/+archive)

---

### Post by tatrefthekiller on 2008-05-22
I don't think the desktop patch is going to be included in wine...
The patch simply replace 'getDesktopWinfow()' by '0' !!!
A good patch should operate on the getDesktopWindow function to make it return 0, isn't it ?

---

### Post by shae on 2008-05-22
My one concern with such a method would be that getDesktopWindow() is likely used elsewhere and works.  Thus just replacing getDesktopWindow() with 0 in that file fixes the bug with Warcraft without messing with the implementation elsewhere, but I will look into it.

---

### Post by SilverDragon on 2008-05-22
Well I've tried following this How-to and I have a few questions.

> You might need the kernel header files as well, as I had them installed for something else and didn't know if wine used them also.

Would the kernel header files be "kernel-package' under Synaptic Package Manager?

Also, is it okay if I put the "wine-1.0-rc1" folder in my Home folder?


> Step 8: Hopefully you have all your make files made.

Code:

make depend && make wine

Step 9: Cross you fingers for 30mins-1hr...

Step 10: If you made it this far, prepare for Warcraft 3 Battle.net heaven and type...

Code:

sudo make install



Going by step 9, it seems the "made depend && make wine" command is supposed to take a while, but only takes about a minute. Meanwhile, when I use "sudo make install" it takes while. I was wondering if this is normal, because it seems like it would be the other way around.


But my main problem is when I go through all of the steps, it seems as if Wine is not installed? I think it may have to do with the fact I don't have the kernel header files which might affect the compiling/patching process?

Also, I'm assuming that the patching did work because the file size of the wine-1.0-rc1 folder when from 93.7 MBs to almost 300 Mbs.

Oh and I forgot to add, I get this in the terminal at the end after "sudo make install"

```
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/huy/wine-1.0-rc1/dlls/winex11.drv'
make[1]: *** [winex11.drv/__install-lib__] Error 2
make[1]: Leaving directory `/home/huy/wine-1.0-rc1/dlls'
make: *** [dlls/__install-lib__] Error 2
```

Thank you for your time :)

---

### Post by shae on 2008-05-22
> **SilverDragon said:**
> Well I've tried following this How-to and I have a few questions.



Would the kernel header files be "kernel-package' under Synaptic Package Manager?



No you need "kernel-headers-generic" if you are using the default kernel.

> **SilverDragon said:**
> Also, is it okay if I put the "wine-1.0-rc1" folder in my Home folder?

That is fine.

> **SilverDragon said:**
> 
Going by step 9, it seems the "made depend && make wine" command is supposed to take a while, but only takes about a minute. Meanwhile, when I use "sudo make install" it takes while. I was wondering if this is normal, because it seems like it would be the other way around.


But my main problem is when I go through all of the steps, it seems as if Wine is not installed? I think it may have to do with the fact I don't have the kernel header files which might affect the compiling/patching process?

Do you get any errors when you do make depends && make wine?

> **SilverDragon said:**
> 
Also, I'm assuming that the patching did work because the file size of the wine-1.0-rc1 folder when from 93.7 MBs to almost 300 Mbs.

The patch does not dramatically increase the size of the folder, the size is that much higher because the compiler dumps the results into that folder before installing.

> **SilverDragon said:**
> 
Oh and I forgot to add, I get this in the terminal at the end after "sudo make install"

```
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/huy/wine-1.0-rc1/dlls/winex11.drv'
make[1]: *** [winex11.drv/__install-lib__] Error 2
make[1]: Leaving directory `/home/huy/wine-1.0-rc1/dlls'
make: *** [dlls/__install-lib__] Error 2
```

Thank you for your time :)

That makes me think that it is not building properly.  You should make sure you have all the dependencies and check for errors when you run make depends && make wine.

Furthermore, if you would like to just use my repository I mentioned earlier, I made a howto for it if you would like([http://ubuntuforums.org/showthread.php?t=803988](http://ubuntuforums.org/showthread.php?t=803988)).

---

### Post by SilverDragon on 2008-05-22
Would it be weird and/or stubborn of me if I wanted to make it work through compiling Wine? I think I just want to learn how to do it correctly :)

I couldn't find "kernel-headers-generic" in Synaptic Package Manager. I think I use the default kernel? I haven't messed around with the kernel at all.

Thanks for answering all of my other questions.

I decided to go through the How-To again and after I typed "make depend && make wine" it ends with:

```
make[2]: Leaving directory `/home/huy/wine-1.0-rc1/tools/wmc'
make[2]: Entering directory `/home/huy/wine-1.0-rc1/tools/wmc'
../../tools/makedep -C. -S../.. -T../..  lang.c mcl.c utils.c wmc.c write.c                mcy.y  
make[2]: Leaving directory `/home/huy/wine-1.0-rc1/tools/wmc'
make[2]: Entering directory `/home/huy/wine-1.0-rc1/tools/wrc'
../../tools/makedep -C. -S../.. -T../..  dumpres.c genres.c newstruc.c readres.c translation.c utils.c wrc.c writeres.c                parser.y parser.l 
make[2]: Leaving directory `/home/huy/wine-1.0-rc1/tools/wrc'
make[2]: Entering directory `/home/huy/wine-1.0-rc1/tools/wrc'
../../tools/makedep -C. -S../.. -T../..  dumpres.c genres.c newstruc.c readres.c translation.c utils.c wrc.c writeres.c                parser.y parser.l 
make[2]: Leaving directory `/home/huy/wine-1.0-rc1/tools/wrc'
../tools/makedep -C. -S.. -T..  fnt2bdf.c fnt2fon.c make_ctests.c makedep.c relpath.c sfnt2fnt.c                   
make[1]: Leaving directory `/home/huy/wine-1.0-rc1/tools'
./tools/makedep -C. -S. -T.                    
rm -f wine && ln -s ./tools/winewrapper wine

```

I don't see any errors but you may notice something wrong.



edit:I think I might have fixed it. I had the repositories for Wine from the official web site still on my sources list so that may have conflicted things, so I removed it.

Oh and I am attempting to install Wine using the link you provided now.

edit again:It works :)

---

### Post by shae on 2008-05-22
That looks like it is right, this is really stumping me.

---

### Post by SilverDragon on 2008-05-22
Well either way thank you very much for your help :)

I'm just wondering now if I had removed the official repositories earlier if compiling Wine from source would have worked. I think I might just try later out of curiosity :D

Well time to host some Dota 8-)

---

### Post by soxs on 2008-05-23
> **zir0n said:**
> I use the -opengl option because i have an old laptop.
lol, I've own an Phenom, 4GB of ram and a 3870RadeonHD and it makes a difference of about 100%, DX fps: 20-70; OpenGL FPS: 80-170
I would say, EVERBODY should run with the -opengl switch


EDIT:
For 64bit users:
You need to link some libs and use some special configure options, these steps all have to be done BEFORE comiling with make.
change to your wine folder and:
```

mkdir -p `pwd`/lib32 
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so 
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so 
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so 
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so 
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so 
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so 
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so 
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so 
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so 
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so 
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so 
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so 
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so 
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so 
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so 
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so 
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so 
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so 
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so 
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so 
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so 
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so 
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so 
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so 
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so 
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so 
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so 
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so 
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so 
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so 
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so 
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so

```
Instead of ./configure you must use:
```

CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v

```

Note: Instead of make install you can create a *dirty* .deb package via (which is easier to remove if you need to remove it, and you do not need to keep the build folder in order to remove it):
```

sudo checkinstall --fstrans=no

```

---

### Post by tatrefthekiller on 2008-05-23
I have Pentium M 1,7 GHz, 2GB RAM, X700 Pro, I have to use -opengl, otherwise, it's unplayable (even on the menu) !
I don't see any difference between opengl and directx (on XP), with the same options.

---

### Post by shae on 2008-05-23
I am posting to say this should work with wine-1.0rc2.

---

### Post by soxs on 2008-05-23
> **shae said:**
> I am posting to say this should work with wine-1.0rc2.
Well, if the servers weren##t that unresponsive I would have tried it allready -.-

---

### Post by shae on 2008-05-23
Packages as well as the source code are in my repository.

---

### Post by quentindemetz on 2008-06-08
Just wondering: After doing ./configure, the terminal says to 'make depend && make' whereas the tutorial tells to 'make depend && make _wine_' 

Executing the first does grant a wait of 30min-1hr, whereas the latter is fast but the next step is much longer.

I can't get good framerate with the latter, and am making the first one now.
Does anyone know which would be the best solution ?
Thanks!

---

### Post by Sleaka J on 2008-06-08
I just want to point out that the bug preventing hosting on Battle.net in Wine is no longer assigned to be fixed by 1.0.0. It's been deferred to 1.2.0 now.

---

### Post by zir0n on 2008-06-09
I believe if you do a "make depend && make" you also compile manpages for Wine API compile html pages for Wine API and compile sgml source for the Wine API Guide. I might be wrong about that though. Either way it shouldn't give u anyworse performance if u typed "make depend && wine" or "make depend && make wine". I think ur performance issue might be the fact you are running the game with the DirectX drivers instead of the opengl. also if ur having problems starting the game, delete ur movies folder located in your ~/.wine/drive_c/Program\ Files/Warcraft\ III/ directory. Opengl performance boost is stated in this thread 

[http://ubuntuforums.org/showthread.php?t=813549&highlight=warcraft+opengl]("http://ubuntuforums.org/showthread.php?t=813549&highlight=warcraft+opengl")

---

### Post by menise270 on 2008-06-12
Ummm ellow im newbie in Warcraft 3 omg sorry to ask this stupd:confused: question but how do you use -opengl thingy i dont understand plzz reply ASAP:lolflag:

---

### Post by zir0n on 2008-06-13
It's in the link right above your post, but instead of reposting the link and being a jerk, I'll just add my own method of creating a launcher with the opengl flag.

make a launcher for warcraft 3 by going in your Applications => Wine => Programs => Warcraft III and right clicking the frozen throne entry and selecting "Add this launcher to Panel" or "Add this launcher to Desktop" your preference. 

Then right click the newly created launcher and select properties. In the Launcher Properties window where it says "Command:" In that box at the very end, append "-opengl" so it looks something like this

```
env WINEPREFIX="/home/user/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl
```

making sure to substitute your user name in "/home/user/.wine" This should run the game using opengl giving you better performance rather than in directx mode.

---

### Post by soxs on 2008-06-13
**Note: this post may be useless, misunderstood last post.**
use $HOME/.wine instead of /home/<yourusername>/.wine (Note: this only works for the user, in which home dir the .wine folder actually is. For otheryousers you will have to link that folder from /home/userA/.wine to /home/userB/.wine (unsing ln -s))

---

### Post by fuzzyworbles on 2008-06-25
> **tatrefthekiller said:**
> I have Pentium M 1,7 GHz, 2GB RAM, X700 Pro, I have to use -opengl, otherwise, it's unplayable (even on the menu) !
I don't see any difference between opengl and directx (on XP), with the same options.

Are you running frozen throne patch 1.21b by any chance? I'm having a problem saving games on my pentium m 1.8 100% of the time, but only occasionally on my p4 3ghz ht with the same kernel and wine version. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1177](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1177) provides a patch for this ([http://bugs.winehq.org/attachment.cgi?id=8368]("http://bugs.winehq.org/attachment.cgi?id=8368"))... and holy jebus, it works!

1. get the source (i used the latest official 1.0 release)
2. patch it
3. remove old wine
3. compile

---

### Post by Akingboy on 2008-07-15
Works well with 1.1.1 thanks a lot!
I needed this!

I just can't now see the "wine settings" and other those things in the wine menu. Only programs.

And when opening autorefresher I get "Cannot open assembly warcraftiiiautorefresh.exe"

---

### Post by zir0n on 2008-07-15
Akingboy:

I get the same error if i just copy and paste "mono WarcraftIIIAutoRefresh.exe" you need to specify what directory you saved the file to. Like in my case i stored it in a folder called Programs so i need to run "mono ~/Programs/WarcraftIIIAutoRefresh.exe"

'~' is shorthand for "/home/user" You can also use the home environment variable like an earlier post suggested by doing "mono $HOME/.../WarcraftIIIAutoRefresh.exe" replacing the ... with the location of the file in your home directory.

Glad this guide helped you!

---

### Post by Akingboy on 2008-07-15
Ah that was the case. Stupid me.
Well got it now thanks.

One problem. When autorefresher joins it doesn't leave :P I had to manually kick them all and then it didn't refresh anymore.

And I still lose textures if I go to desktop or like firefox but I don't lose them if I open something so that I can see warcraft behind it like messenger window.

---

### Post by zir0n on 2008-07-15
Are you using the -opengl Flag? and what does the output say in the autorefresher window? I just tested it and it seems to work fine for me but i am using wine-1.0-rc1 not the 1.1.1 version. I'll have to look into upgrading my wine version on one of my days off.

---

### Post by soxs on 2008-07-15
you are suffering from the libGL error aswell as a lot of other users. You are stuck with indircet rendering (low fps in custom maps/maps with many players/units/fx plus the named BUG)
Have a look at wine bugs..

---

### Post by Akingboy on 2008-07-19
> **soxs said:**
> you are suffering from the libGL error aswell as a lot of other users. You are stuck with indircet rendering (low fps in custom maps/maps with many players/units/fx plus the named BUG)
Have a look at wine bugs..

Who?
I have fine fps even on maps with lots of stuff to make it lag but I have new computer so it doesn't lag.
And about that refresher it started working again. Its like 1 time of 5 I use it doesn't leave but its not a big deal.

---

### Post by soxs on 2008-07-19
oh, sry
You may check it when runnig wc3 from the commandline:
```
wine ~/.wine/drive_c/your/wc3/folder/Frozen\ Throne.exe -opengl
```
If within th first 10 lines something libGL related turns up, you are suffering from that bug

---

### Post by Akingboy on 2008-07-19
Seems like I have that. Heres what I got. Is there way to fix this?

> fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
[B]libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering[/B]
fixme:advapi:SetSecurityInfo stub

---

### Post by soxs on 2008-07-20
> **Akingboy said:**
> Seems like I have that. Heres what I got. Is there way to fix this?
Well, I dind't find one. You may watch the bugreport at winehq.com

---

### Post by Juggercat on 2008-09-08
umm, yea, im trying to follow this how to... but i seem to get stuck on step 4...
it says it cant find the source pacakges for wine.. :S

so... help me please! :O

thx

---

### Post by Juggercat on 2008-09-15
BUMP!

please... can someone help me... im following the guide on page one...
and when i try to install the build dependencies for wine it give me the following error

"E: Unable to find a source package for wine"

please... im a poor nooblet seeking aid!

---

### Post by zir0n on 2008-09-16
Have you changed or modified your sources.list file located in the /etc/apt/ directory or under System > Administration > Software Sources? Please post the contents of your sources.list file.

Also what release are you using? Feisty, Gutsy, Hardy, Intrepid?

Try doing...

```
sudo apt-get update
```

first, then if step 4 still doesn't work reply back with the answers to these questions.

---

### Post by Nexusx6 on 2008-10-13
I had an issue in Wine 1.1.6 where friends on a LAN could see my games, but couldn't join them. It was familiar to the problem lots of people are having have not having their game being even visible so I followed the instructions on this page and am happy to report that it works.

I found a more recent patch in the bug report for this issue. Instead of the one found at the original post, I used this for the the network patch:
[http://bugs.winehq.org/attachment.cgi?id=15523](http://bugs.winehq.org/attachment.cgi?id=15523)

Hope this helps someone.

---

### Post by Aspras on 2008-11-08
Thanks for the guide but what do you mean by "installing anything you're missing using "apt-get install".

---

### Post by Philz0r on 2008-11-08
Hi guys

I need to know how i can host - ive gotten warcraft 3 working perfect aside from no longer being able to host.

(My router has been forwarded for all required ports so it is the OS}.

Ty for reading :)

EDIT

and another thing currently while playing on warcraft 3 TFT im getting large amounts of screen flickering to the ubuntu wallpaper, anyone know what this is about?

---

### Post by Aspras on 2008-11-09
Which version of Ubuntu do you have?

---

### Post by Philz0r on 2008-11-09
Ubuntu 8.04 LTS

---

### Post by Aspras on 2008-11-09
I suggest you try this [http://ubuntuforums.org/showthread.php?t=803988]("http://ubuntuforums.org/showthread.php?t=803988") you will be able to host with it.

---

### Post by zir0n on 2008-11-10
> **Aspras said:**
> Thanks for the guide but what do you mean by "installing anything you're missing using "apt-get install".

Usually when you run a configure script, if something is required but missing, it will stop generating the make file and throw an error saying you're missing a dependency. To resolve this you can usually just apt-get install "insert-missing-dependency-here"

---

### Post by Manu311 on 2008-11-25
Hi,

I've hosted many dotas after I followed your tutorial with wine version 1.1.3.
but now I updated it to 1.1.9 and it just doesn't work :(.
I've applied the hosting patch into it and there was no error, neither on starting anything else.
(window patch works fine)
I can join Bnet without problems, but noone can join my games and even in local network I have problems.
I used to use ListChecker and it had worked fine. ListChecker still does, but WC3 doesn't react to it.
LC says he's joined the game, and I can host games in Bnet with LCs command line.
But in WC3 there is still an empty game where noone joins.

I think these problems have the same source, but I didn't found it so far.
Any Ideas?

EDIT:
ok, I just undid and redid everything and it's working well again.
Maybe it's a random problem or I've forgotten something the first time :).


BUUUUT:
Now wine gots a bit ugly.
I normaly open ventrilo in window mode "wine explorer /desktop=,800x600 Ventrilo.exe"
Desktop Mode totally crashs now: the desktop is not displayed, It's there, but invisible till I move the ventrilo window (in this case) around.
Also when I start WC3 I can't change the desktop. WC3 is on each Desktop.
I don't know if both are cause by the not loaded desktop patch but I guess it's the reason.
I don't know why (I'm not very used to patches ...) but it seems one patch overrides the other). On my first try some month ago there was not even 1 difficulty, and now I've got that much :(.


--> I fixed it by reinstalling Wine 1.1.3 ....

---

### Post by mfr1003 on 2009-01-15
alright i got the desktop switch and the hosting patches saved, but as soon as i type in the patch -p1 lines into terminal, i get errors.

I get asked for my sudo password...wtf is that?

---

### Post by Manu311 on 2009-01-21
sudo password = SuperUser (su) Password = Your Root Password

For More informations: The Errors please

---

### Post by ostaja on 2009-05-09
Hey. There was some patching problems with 1.1.21, but with 1.1.3 which is sightly older, works fine. Thanks :).

---

### Post by tolostoi on 2009-12-24
I did this on Ubuntu 9.10 Karmic like this (not the latest wine, but works fine)

```
mkdir ~/build
mkdir ~/build/wine
cd ~/build/wine
apt-get source wine
cd wine*
wget http://bugs.winehq.org/attachment.cgi?id=12913 -O desktop_switching.patch
wget http://bugs.winehq.org/attachment.cgi?id=8368 -O hosting.patch
patch -p1 <desktop_switching.patch
patch -p1 <hosting.patch
dpkg-buildpackage -rfakeroot -uc -b
```
After the compiliation in directory wine, I have 2 deb packages
[COLOR="Orange"]wine_1.0.1-0ubuntu8_i386.deb
wine-dev_1.0.1-0ubuntu8_i386.deb[/COLOR]
just install it by regular way (double click on it, or with dpkg)
```
cd ~/build/wine
sudo dpkg -i wine_1.0.1-0ubuntu8_i386.deb wine-dev_1.0.1-0ubuntu8_i386.deb
sudo apt-get -f install
```

---

### Post by Harmageddon on 2010-09-06
> **zir0n said:**
> 
[COLOR=RoyalBlue]Step 3:[/COLOR] Download and unzip the latest wine, as of now wine-1.0-rc1.tar.bz2 source code from 

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449) 

Where must I unzip the file?
> **zir0n said:**
> 
[COLOR=RoyalBlue]Step 4:[/COLOR] Install the build dependencies for wine.

"/var/lib/apt/lists/ppa.launchopad.net_starfall87_ppa_ubuntu_dists_lucid_main_source_Sources could not be opened - open (2: No such file or directory)"

Can you help me, please?

---

