---
title: "Warcraft 3 problems... ( game won't start / won't stay open. )"
date: 2008-05-02
forum: Wine
---

### Post by Cpuboye11 on 2008-05-02
Problem:

I have Warcraft 3 With Frozen Throne in my Wine program files. When I try to run warcraft 3 with the command below. The game will attempt to start in either a vitural box set to 800:600 or full screen and then just crash.. Error report below or w/e... not sure why it doesn't work.. Counter Strike Source runs with steam so. yea....

   1. Wine version - Wine 0.9.59
  
 2. Terminal output - 

```
kyle@kyles-laptop:~$ wine "c:\\Program Files\\Warcraft III\\Frozen Throne.exe" -opengl
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {cda42200-bd88-11d0-bd4e-00a0c911ce86} could be created for context 0x1
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {e436ebb2-524f-11ce-9f53-0020af0ba770} could be created for context 0x1
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f67c,0x00000000), stub!
kyle@kyles-laptop:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x33ce88,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d604,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d694,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @75! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @70! (desktop)
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {e436ebb3-524f-11ce-9f53-0020af0ba770} could be created for context 0x3
[FAIL] CoCreateInstance(CLSID_FilterGraph, NULL, CLSCTX_INPROC, IID_IGraphBuilder, (void **)&s_pGraph) = -2147221164fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x6f0ccca9

kyle@kyles-laptop:~$ 


```  
 3. Wine configuration - didn't really change anything, accept for graphics. I have tried both in a box : 800;600 and in its own windows.. No difference. I have added the direct x support dlls and installed them. From this website: [http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html)
  
 4. Hardware specs/drivers - ATI 7500m  open source drivers. have to be.... Hmm no fglx or w/e. Intel P4m 1.8 Ghz 1.8GB ram...
   
5. Other Wine applications - Hmm. photoshop 7... Thats it... So far ;-D


I hope i gave enough information. I always thought Steam would be the hard one to get running.. Not warcraft 3... lol... Warcraft 3 is just a drag and drop :-D

Any questions? Anything i left out?

Thanks,
kyle
ComputerFreek

---

### Post by Cpuboye11 on 2008-05-03
-Bump-

I looked at this thread--> [http://ubuntuforums.org/showthread.php?t=768176&highlight=Warcraft+III](http://ubuntuforums.org/showthread.php?t=768176&highlight=Warcraft+III)


But it didn't help.. :(


All I know is that the game never starts. I see the beginning logo of it starting and then boom- crashes or closes...

---

### Post by loic5032 on 2008-05-03
Hey,

Did you try renaming the 'Movies' folder. Wine has had problems with the ingame movies in W3 for as long as I've been using it.

The Game works perfectly here (without the movies).

---

### Post by Cpuboye11 on 2008-05-03
> **loic5032 said:**
> Hey,

Did you try renaming the 'Movies' folder. Wine has had problems with the ingame movies in W3 for as long as I've been using it.

The Game works perfectly here (without the movies).


Dude thanks.. I don't really care about the movies any ways.. I don't play the game besides in lan party's with my friends and stuff so thank you!!

I only have one question.. Why is it every time i click on something- like a unit or any where on the map or even the menus before you even get in to a game.. Flash the screen? I mean for example: You first get in to the game after opening it.. you click single player: screen flashes. And it will do this every time you click... Just asking because it can get annoying! 

Thanks You,
Kyle:lolflag:

---

### Post by loic5032 on 2008-05-03
Sorry, no screen-flashing here and I don't know nearly enough about this stuff to start guessing... I hope someone else can help you with that.
Did you try the wine app-database?

regards,

loic

---

### Post by Cpuboye11 on 2008-05-05
Does any one know why the games flash when ever i hit the mouse. It does it in source to.. And i don't know why..

---

### Post by dr-phil on 2008-05-10
are you running it in a window? it used to happen to me, removed the window and ran in full screen and the flashing went away. silly me reformatted now i get a critical error every time i try to open wc3 lol trying to fix ><''

---

