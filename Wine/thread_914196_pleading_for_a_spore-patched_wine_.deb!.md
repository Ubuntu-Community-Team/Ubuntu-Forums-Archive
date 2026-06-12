---
title: "pleading for a spore-patched wine .deb!"
date: 2008-09-08
forum: Wine
---

### Post by KhaaL on 2008-09-08
Hey all, excuse the hard to read title :D

I'd like to ask someone to post .debs of latest wine with the patches listed at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652") in order to get spore render objects correctly. 

I have zero knowlege in patching, compiling and packaging. If someone would post it, I'm sure *a lot* of people would appriciate it, considering how popular this game is. 

Oh, and please don't forget the 64-bit users ;)

---

### Post by trippnk on 2008-09-09
I'll Bump for this.  I really wanna play the game but have no desire to install Xp just to do it!!!

---

### Post by grjemo on 2008-09-14
I too, would be very grateful for something of this sort.

EDIT: I think I figured out how to compile with the patch, it's not that hard

EDIT 2: It failed after about 30 minutes of compiling.

---

### Post by grjemo on 2008-09-14
This is what I ran into, if anyone can help.

```
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/grjemo/Desktop/wine-1.1.4/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/grjemo/Desktop/wine-1.1.4/dlls'
make: *** [dlls] Error 2

```

---

### Post by Perfect Storm on 2008-09-14
is libxext-dev installed?

---

### Post by Vadi on 2008-09-14
file a bug report on getdeb.net. they're already distributing wine with a 3dmark patch, so this can't hurt

---

### Post by grjemo on 2008-09-14
Someone should move this to the wine section.

---

### Post by GSZX1337 on 2008-09-14
> **Vadi said:**
> wine with a 3dmark patch
What's the 3dMark patch? Is it just for 3dMark or it it for other things too?

---

### Post by grjemo on 2008-09-14
> **Artificial Intelligence said:**
> is libxext-dev installed?

You are my hero.  It works.  I'm installing spore as I speak.

---

### Post by Vadi on 2008-09-14
Apparently it makes a bunch of stuff like CoD and other games work. But I also heard that CoD now works without it...

I'm not sure, I don't use wine so I'm not exactly up to date on it.

---

### Post by legolas_w on 2008-09-15
I am also looking for a patched version of WinE, I just want to play spore in linux :( I dont like to go back and forth between linux and windows because of the game.

Thanks

---

### Post by CodyS on 2008-09-16
How to get Spore working in wine 1.1.4     (this is for the i386 version only)

Make sure you have wine 1.1.4 installed.  (wine --version)

Then download the following archive to your desktop.

[http://webz.us/spore-wine1.1.4.tar.gz](http://webz.us/spore-wine1.1.4.tar.gz)

It contains the 2 files that are patched for the graphics problem.

Extract the 2 files to your desktop
then from the command prompt, copy them to the /usr/lib/wine folder.

for example 

sudo cp /home/<username>/Desktop/wined3d.dll.so /usr/lib/wined3d.dll.so
sudo cp /home/<username>/Desktop/d3d9.dll.so /usr/lib/d3d9.dll.so

replace <username>  with your login name

Start spore with the following:

wine "C:\Program Files\Electronic Arts\SPORE\Sporebin\SporeApp.exe" -locale:en-us -w -r:1600x1024 -safe

My monitor is 1920x1200 resolution, and it opens in a window and works perfect for me, ymmv.

Good Luck!

---

### Post by YokoZar on 2008-09-17
Just wait till Friday with Wine 1.1.5

---

### Post by legolas_w on 2008-09-17
Hi
Thank you for the patch, can you take a look at my screenshot and let me know whether the game should appear like this?

Why everything has a trail? is it from the game or WinE / patch installation problem?
[IMG]http://tinypic.info/files/1pjex3xvqa4vnt3olwmq.jpg[/IMG]


Can you please share an screenshot of your Cell stage?
Thanks

---

### Post by koocho on 2008-09-17
hi!

have the same problem like legolas_w - 

[[IMG]http://img299.imageshack.us/img299/2049/bildschirmfotomc8.th.png[/IMG]](http://img299.imageshack.us/my.php?image=bildschirmfotomc8.png)

will the problem be solved with wine 1.1.5 and btw where can i find out when the new versions will be released?

greets
simon

---

### Post by legolas_w on 2008-09-17
Koocho, I heard that there will be a release (1.1.5) on Friday but I do not know whether the patchs will resolve the problem that we have or not.

---

### Post by Geilviech on 2008-09-17
i have the same problem as legolas_w and koocho, and i'm sure the game shouldn't appear like this ;)
i hope the new version of wine(1.1.5) will fix this and will be available for 64 bit systems!
Hints or other useful information welcome!

---

### Post by koocho on 2008-09-19
works fine with wine-1.1.5 ! - just installed and tried it - spore works out of the box now :)

greets
simon

---

### Post by Vadi on 2008-09-19
So no patching is needed?

---

### Post by koocho on 2008-09-19
no it's already patched... but now i got another problem: grafics are fine but when i try to get into the second stage the game crashes... omg... looking for a solution now^^

//EDIT: [http://www.nabble.com/-Bug-15138--New:-Spore-crashes-after-the-first-stage-of-life-td19340556.html](http://www.nabble.com/-Bug-15138--New:-Spore-crashes-after-the-first-stage-of-life-td19340556.html)

//EDIT: my graphics details were too high... sry, game runs fine ;)

---

### Post by legolas_w on 2008-09-19
Hi
Can you please let me know where do you get the 1.1.5?
I looked everywhere for a deb package and I did not find anything .

Thanks.

---

### Post by koocho on 2008-09-19
oh there isn't a .deb package yet. just wanted to mentioned here that the problem with the graphics is gone with the new version... 

you can download the source [[COLOR="Red"]here[/COLOR]]("http://winehq.org/?announce=1.1.5") and compile it yourself. it's easy as you can read [[COLOR="Red"]here[/COLOR]]("http://www.winehq.org/site/docs/wineusr-guide/installing-wine-source") , only four commands ;)

but i guess the .deb will be online in a few hours... 

have fun
simon

---

### Post by melak on 2008-09-19
While I'm willing to try to do it myself, I'll wait the few hours as predicted to see if there will be deb package. I shall be waiting expectantly.

---

### Post by Dungdae on 2008-09-27
Hey trying to make creature creator work, installation of the game was successful. Have upgraded wine to 1.1.5... 

But when starting file:SporeCreatureCreator.exe (which i strongly presume is the right file) the display just cracks up...

When starting manually in terminal i get this message:

```

user@xx:~$ wine "/home/kathka/.wine/drive_c/Program Files/Electronic Arts/SPORE/Sporebin/SporeCreatureCreator.exe"
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1f9a3e0,0x00000004,0x1f9a3dc) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f992cc): Stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1f99150,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3594
fixme:psapi:EnumPageFilesA (0x14cc840, 0x1f79bd4) stub
fixme:psapi:EnumPageFilesA (0x14cc840, 0x1f444f0) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1faf940): Stub!
fixme:thread:SetThreadIdealProcessor (0xa0): stub
fixme:thread:SetThreadIdealProcessor (0xa8): stub


```

Have also tried to type -open gl after the command line, but same happens..

Have allready installed graphic driver (ATI radeon x1950) so i presume that opengl is installed

Using Ubuntu 8.04- the Hardy Hero - 64 bit

plz help cause i am beginning to get quite tired of this:(

---

