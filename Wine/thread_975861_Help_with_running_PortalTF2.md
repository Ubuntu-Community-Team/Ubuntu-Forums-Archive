---
title: "Help with running Portal/TF2"
date: 2008-11-08
forum: Wine
---

### Post by lava on 2008-11-08
Hi,

I've been trying to get Portal running under Wine for a while and I just haven't been able to. I've followed a couple of the tutorials that are out there, and nothing seems to work. I haven't found anything helpful on the AppDB. I also haven't found a lot of instances of my particular problem. So I turn to ask the helpful people on this forum.

My Version of wine: 1.0

My hardware spec:
[http://www.thinkwiki.org/wiki/Category:T61](http://www.thinkwiki.org/wiki/Category:T61)

I'm actually not sure which video card I'm using, the intel or the nVidia (I didn't buy the laptop), so the first question is, can I figure it out somehow? 

**EDIT** Actually, thanks to lshw (awesome, by the way) I can tell that I'm running the Mobile Intel 965 Express Chipset, which is supported by Xorg, so no proprietary drivers needed.

So this is what happens. After launching Portal from Steam, I see the initial Valve intro video, and the logo for Powered by Steam. Then the screen turns black, the mouse comes up, but everything's frozen. Keyboard and mouse don't do anything. I can ssh into it, but killing steam and hl2 doesn't do anything. I have to restart the computer.

I haven't been able to see any console output, because I'm some sort of idiot. I ssh into the laptop, launch steam, navigate to my Portal directory (the one that contains hl2.exe) and try

wine hl2.exe -applaunch 400

(400 is portal) And I get an error saying something like "cannot find gameinfo.txt in directory hl2". To me that says that I'm trying to launch it incorrectly somehow. So the other question is, how do I launch Portal from the command line?

Thanks, your help would be greatly appreciated.

---

### Post by cogadh on 2008-11-08
You are running the wrong executable. You should be running "wine steam.exe -applaunch 400". That will launch Steam then immediately launch Portal. Once you do that, you should be able to get some console output that will explain what is going on.

However, the fact that you are trying to run it on an Intel 965 chipset is going to be a problem. I'm not sure that chipset is sufficient to run the game in Windows, let alone on Linux through Wine.

---

### Post by lava on 2008-11-08
Thanks, that got me launched.

Actually, I just did the dist upgrade to Intrepid. Now I get an entirely different issue, at least it seems like it's getting further. Now I get an alert:

Engine Error
failed to lock vertex buffer in CMeshDX8::LockVertexBuffer

**Edit:**

I had Portal to launch with parameters (set inside steam) like -dxlevel -width -height, setting it up to my native screen resolution. I took those out, and now it gets a little bit further ahead.. it gets past the loading screen, and I hear the Portal menu music, but the screen is black except for some white rectangles at the bottom of the screen.

---

### Post by cogadh on 2008-11-08
Try this:
```
wine steam.exe -applaunch 400 -dxlevel 80
```
Also make sure you have disabled any desktop effects before trying to run the game.

---

### Post by lava on 2008-11-08
I'm replacing compiz with metacity. I tried adding the -dxlevel parameter, but it's still the same thing :(. After "Powered by Steam" The screen flickers white, goes dark except for some white squares at the edges of the screen. I can hear the music, but there's no graphics.

---

### Post by cogadh on 2008-11-08
What are you getting for terminal output from Wine?

---

### Post by LordPi on 2008-12-11
Sorry to res an old thread, but I've been having the same problem. Terminal output is lengthy. Completely fills the buffer, in fact.  The end is here. 
```
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION

```
It crashes at this point. Not sure what the trigger was, but it was about the time I started messing with xterm
```

fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x17f0a0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x17f0a0)
fixme:shdocvw:OleObject_Close (0x17f0a0)->(1)
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!

```

the initial command was ```

env WINEPREFIX="/home/tim/.wine" wine "C:\Program Files\Steam\Steam.exe" -dxlevel80

```

---

### Post by monroetransfer on 2008-12-15
> **cogadh said:**
> ...
However, the fact that you are trying to run it on an Intel 965 chipset is going to be a problem. I'm not sure that chipset is sufficient to run the game in Windows, let alone on Linux through Wine.

What do you mean by that? I'm on a Toshiba Satellite laptop, which uses an intel chipset i think? Are you saying that if I installed pure windows I still wouldn't be able to get this to work?

---

