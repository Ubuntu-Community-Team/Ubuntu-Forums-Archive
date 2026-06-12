---
title: "Fate running fullscreen on wine"
date: 2007-01-27
forum: Wine
---

### Post by Sandsound on 2007-01-27
With wine 6.29 I am finaly able to play Fate without having to boot up my M$ Windoze, but...

Unfortunaly I cant get it to run proberly in fullscreen. I have made a script that changes the screenresolution (thanks to some thread I found somewhere on the forum) :

#!/bin/bash
    #
  killall -19 gnome-panel		// suspend gnome-panels //
  xrandr -s 3				// switch to 1024x768 //                            
  wine c:/WildTangent/Apps/GameChannel/Games/E2BABA4F-C37B-4A6C-8F00-0D303441C2D3/Fate.exe	// load the game //
  killall -18 gnome-panel		// restart gnome-panels //  
  xrandr -s 1				// switch back to 1400x1050 //
    exit

Now the bottom bar is gone, and the icons on the topbar is also gone, but the topbar is still there ???
( screenshot : [http://www.sandgreen.dk/img/Fate_screenshot.jpg](http://www.sandgreen.dk/img/Fate_screenshot.jpg) )

Also... this game will not run under 24 bit resolution, so I have changed my xorg.conf to use 16 bit as default. This I can live with, but its a bit more tricky to play the game when I cant see my health status ;-)

Other that these minor problems, the game runs real smooth and the sound is perfect.

---

### Post by disturbedite on 2007-02-14
wine should automatically run the color mode correctly.  you shouldn't have to change your xorg config.

as for the resoultion, you "told" wine to run the game at a resolution that you normally can't in windows with a script?  could you post that script?  i've been trying to find out how i can run apps (specifically games, i.e. diablo ii lod) in other-than-native resolutions with wine but i haven't found any answers.

EDIT:  i found [this thread]("http://www.ubuntuforums.org/showthread.php?t=320031&highlight=wine+resolution") for a script.  nvm.

---

### Post by heyo on 2007-02-14
niiiiiiiiiiiiiiiiiiiice

---

### Post by Sandsound on 2007-02-17
> **disturbedite said:**
> wine should automatically run the color mode correctly.  you shouldn't have to change your xorg config.

Hmm... strange ???
I still get a "this game must be run i 16- or 32-bit mode" message unless i change my xorg.conf. 
[IMG]http://www.sandgreen.dk/16bit.jpg[/IMG]

I do think that I have solved my gnome-panel problem thou, turns out I have to set my gnome-panel to normal mode, not restart mode :oops: 

Anyway... at least I can play now, all thou I must admit... making it work is more fun than actually playing, so I guess I'm of to try making Oblivion run under Wine :-)

---

### Post by LordFu on 2007-02-28
I have the cd version of this game, and I'm having no luck getting it to run. If anyone who has it working would like to pass on how they did it, I'd appreciate it. 

Thanks.

---

### Post by Sandsound on 2007-02-28
> **LordFu said:**
> If anyone who has it working would like to pass on how they did it, I'd appreciate it.

I used this one : [http://download.wildgames.com/wildgames/fate-broadband-setup.exe](http://download.wildgames.com/wildgames/fate-broadband-setup.exe)

I'm still dual-booting for games like Oblivion, so I just installed it on my Windoze disk, and then I moved the WildTangent dir to my wine dir (drive_c) and voila :-)
Just remember that you have to run it in 16-bit colors.

btw... my wine runs a lot better after i installed IE6 ? maybe something to do with a servicepack. Not that I would ever use IE... ofcourse :-) it was just a little test.

---

### Post by Sandsound on 2007-02-28
**A simplified How-to**

Assuming you have wine installed and have a Windows available, this is one way to install Fate. I'm not saying it's the only way, and maybe it's not even the right way, but it worked for me :-)

1.
Download Fate here [http://download.wildgames.com/wildga...band-setup.exe](http://download.wildgames.com/wildga...band-setup.exe)

2.
Install it in Windows

3.
Move the WildTangent dir to your wine c-dir (/home/username/.wine/drive_c)

4.
In xorg.conf change the line "DefaultDepth 24" to "DefaultDepth 16"

5.
Open a terminal and enter :
wine c:/WildTangent/Apps/GameChannel/Games/E2BABA4F-C37B-4A6C-8F00-0D303441C2D3/Fate.exe

You might have to play a little with the resolution to make it fit, and if you want to remove the annoying gnome-panel in the game, go to system/preferences/sessions and change your gnome-panel to normal instead of restart.

Btw... This is on a Edgy with envy-nvidia drivers and Wine from the repositories.

If you encounter any problems, please post them here.

---

### Post by LordFu on 2007-02-28
Thanks, I'll give it another go when I get home. I'll try installing IE6 into wine, and see if that helps, too. I dual boot, too, so I won't have a problem copying the install over to wine. 

The main difference is that I bought the retail cd at EB, so I can't download and activate it. It comes already activated on a cd. I don't know if that will make a difference or not. My wine version is 0.9.31. I've got the latest official Nvidia driver.

I'll let you know how it goes. Thanks!

---

### Post by LordFu on 2007-02-28
Ok, here's what I did. 

I installed IE6 using ies4linux, which may have been wrong. 

I copied fate over to the wine c:

I try ~$wine "c:/Program Files/WildGames/FATE/Fate.exe"

and get this:
```
wine: Unhandled page fault on write access to 0x00000000 at address 0x5afeb6 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x005afeb6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:005afeb6 ESP:0033ff0c EBP:0033ffe8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b8ab500 ECX:00000000 EDX:00000000
 ESI:005afeb6 EDI:7ffdf000
Stack dump:
0x0033ff0c:  7b87011e 7ffdf000 00000000 00000000
0x0033ff1c:  00000000 00000000 00000000 00000000
0x0033ff2c:  ffffffff 7b82bf00 7b840610 7b8ab500
0x0033ff3c:  7ffdc000 00001000 0033ffe8 ff39ff10
0x0033ff4c:  848d0090 00000001 10012a03 00000000
0x0033ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x005afeb6 EntryPoint() in fate (0x0033ffe8)
  2 0xb7e9c5a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x005afeb6 EntryPoint in fate: addb     %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE      400000-d6a000   Export          fate
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efee000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d37000-b7d3b000       Deferred        libdl.so.2
ELF     b7d3b000-b7e6f000       Deferred        libc.so.6
ELF     b7e70000-b7e83000       Deferred        libpthread.so.0
ELF     b7e95000-b7fa6000       Export          libwine.so.1
ELF     b7fa8000-b7fc3000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\WildGames\FATE\Fate.exe
        00000009    0 <==

```

which means exactly nothing to me. 

Any thoughts? Thanks again.

---

### Post by Sandsound on 2007-03-01
Did you use this : [http://download.wildgames.com/wildga...band-setup.exe](http://download.wildgames.com/wildga...band-setup.exe) or the one you installed from your cd ?

---

### Post by LordFu on 2007-03-01
I used my cd install. If I download it from wildgames.com, I'm stuck with the demo. The cd version I got doesn't have an unlock code. I'm guessing that it launches differently, and the launcher is what is causing the exception. I wonder if there's a way around that.

---

### Post by Sandsound on 2007-03-01
> **LordFu said:**
> I wonder if there's a way around that.

One solution is to use a... *cough*... "patch". Some software actually run better without the authentications check.
All thou I have bought a version of Cubase, I still use a crack because the dongle takes a considerable amount of my system resources, but I guess it's legal as long as you can prove that you have paid for the software ?

---

### Post by daniel7860 on 2008-06-19
> **Sandsound said:**
> **A simplified How-to**

Assuming you have wine installed and have a Windows available, this is one way to install Fate. I'm not saying it's the only way, and maybe it's not even the right way, but it worked for me :-)

1.
Download Fate here [http://download.wildgames.com/wildga...band-setup.exe](http://download.wildgames.com/wildga...band-setup.exe)

2.
Install it in Windows

3.
Move the WildTangent dir to your wine c-dir (/home/username/.wine/drive_c)

4.
In xorg.conf change the line "DefaultDepth 24" to "DefaultDepth 16"

5.
Open a terminal and enter :
wine c:/WildTangent/Apps/GameChannel/Games/E2BABA4F-C37B-4A6C-8F00-0D303441C2D3/Fate.exe

You might have to play a little with the resolution to make it fit, and if you want to remove the annoying gnome-panel in the game, go to system/preferences/sessions and change your gnome-panel to normal instead of restart.

Btw... This is on a Edgy with envy-nvidia drivers and Wine from the repositories.

If you encounter any problems, please post them here.

What is xorg.conf????

---

### Post by daniel7860 on 2008-06-19
ok i found the xorg file u was talking about, but i forgot how to edit it, cuz it says i dont have to permission to change it.

---

### Post by Sandsound on 2008-06-19
> **daniel7860 said:**
> What is xorg.conf????

Its a file located in /etc/X11/

just write this into a terminal:
sudo gedit /etc/X11/xorg.conf

I havent tried this game in a long time, so I don't know if it still works with the new Ubuntu, Wine and so on.

---

### Post by daniel7860 on 2008-06-20
ok i did everything u said exept the terminal thing cuz it doest work, my game is sin a way different directory, but when i open my Fate.exe nothing happens at all, and when i open my Fate-WT.exe it says: Failed to Initialize.:(

---

### Post by Sandsound on 2008-06-20
> **daniel7860 said:**
> ok i did everything u said exept the terminal thing cuz it doest work, my game is sin a way different directory, but when i open my Fate.exe nothing happens at all, and when i open my Fate-WT.exe it says: Failed to Initialize.:(

instead of :
wine c:/WildTangent/Apps/GameChannel/Games/E2BABA4F-C37B-4A6C-8F00-0D303441C2D3/Fate.exe

just edit the path like this :
wine c:/_PATH_TO_YOUR_FATE_FOLDER_/Fate.exe

This way you'll get error-messages in the console that might tell you what the problem is.

---

### Post by vanquishedangel on 2010-11-09
Hi, a little late but I got this to work though PlayonLinux, and by pulling out my hair.

Get PlayonLinux, and when it is updated and set up, open it and  click install, then Internet, and install Internet explorer6. 

After Internet explorer 6 is done installing click install, look to the bottom where it says install an unsupported package or a .pol, click it, then click manual install, click forward, select edit an existing application, choose Internet explorer 6, click forward, and then browse to installer file for Fate and select it.

This install works on Ubuntu 10.04 lts, with wine 1.3.6 and PlayonLinux 3.8.6. You need the installer from their website and a "patched"(cracked) fate.exe file that i cant tell you where to get it but just search it out. One issue so far is that in your inventory you can't see the items, they are blurred but if you mouse over them it tells you what they are. I am sure this is a setting, or dll or something easy fixable, I just haven't found it, it seems all else works though and you can see the items on you.I tried adding directx9c and gecko html, no luck

I am not good at writing scripts but this could be a start for a pol script for wildtangent games, :).

Update, fate in playonlinux and wine is working perfectly in the newer versions.

---

