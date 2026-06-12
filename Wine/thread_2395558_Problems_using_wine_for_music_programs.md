---
title: "Problems using wine for music programs"
date: 2018-07-03
forum: Wine
---

### Post by eamner on 2018-07-03
Hello

I recently upgraded to Kubuntu 18.04 (64-b) from 17.10. 
I'm an amateur musician, been using VST instruments through wine for years. Never had problems. Until now.
I was using Sforzando and other VST programs either as standalone or as a dll plugin (most frequently as dll). But since the upgrade, I am unable to use any of them. Sometimes I can use Festige to run VSTs but only about half of my Vst collection works. For the rest I only get errors. Same thing with Carla.
The reason why I post this here instead of the UbuntuStudio forum is because I think the issue is in Wine. I'm even trying to run winecfg and all I get is:
> 
wine: Unhandled page fault on read access to 0x00000008 at address 0x7f0b1603d829 (thread 002a), starting debugger...
winedbg: Internal crash at 0x7f3b6831a829


Also it doesn't work from GUI.

If I try to run vsthost, I get:

> 
vsthost Public/dssi/VstPlugins/sforzando/Plogue\ Art\ et\ Technologie\,\ Inc/sforzando\ VST_x64.dll 
Returning file identifiers: E9gCROQpQ1nv3bwIW9krCJbf
RemoteVSTClient: executing /usr/lib/dssi/dssi-vst/dssi-vst-server.exe -g Public/dssi/VstPlugins/sforzando/Plogue Art et Technologie, Inc/sforzando VST_x64.dll,E9gCROQpQ1nv3bwIW9krCJbf
DSSI VST plugin server v0.986
Copyright (c) 2012-2013 Filipe Coelho
Copyright (c) 2010-2011 Kristian Amlie
Copyright (c) 2004-2010 Chris Cannam
Loading "Public/dssi/VstPlugins/sforzando/Plogue Art et Technologie, Inc/sforzando VST_x64.dll"... dssi-vst-server: ERROR: Couldn't load VST DLL "Public/dssi/VstPlugins/sforzando/Plogue Art et Technologie, Inc/sforzando VST_x64.dll"
Plugin server timed out on startup: No such device or address
vsthost: bailing out


Sometimes the x86 version would run, but now I get this:

> 
vsthost Public/dssi/VstPlugins/sforzando/Plogue\ Art\ et\ Technologie\,\ Inc/sforzando\ VST_x86.dll 
Returning file identifiers: eKypBmttTxMU7F4tx7Wubo2g
RemoteVSTClient: executing /usr/lib/dssi/dssi-vst/dssi-vst-server.exe -g Public/dssi/VstPlugins/sforzando/Plogue Art et Technologie, Inc/sforzando VST_x86.dll,eKypBmttTxMU7F4tx7Wubo2g
DSSI VST plugin server v0.986
Copyright (c) 2012-2013 Filipe Coelho
Copyright (c) 2010-2011 Kristian Amlie
Copyright (c) 2004-2010 Chris Cannam
Loading "Public/dssi/VstPlugins/sforzando/Plogue Art et Technologie, Inc/sforzando VST_x86.dll"... fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
done
Testing VST compatibility... fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
WARNING: Sample rate requested but not yet set
WARNING: Buffer size requested but not yet set
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x33f408,0x33f40c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x33f408,0x33f40c): stub
WARNING: Sample rate requested but not yet set
WARNING: Buffer size requested but not yet set



So, should I reinstall wine? (and if so, what's the best to do it?) or is there a way to diagnose the issue? I'm using wine-2.0.1.

---

