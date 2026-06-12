---
title: "Wine Portal + .bat"
date: 2008-01-18
forum: Wine
---

### Post by Sugi on 2008-01-18
I need help with getting portal to start up through a .bat file.  How should I run a .bat file in linux?

> IF EXIST SteamEmuPortal.ini GOTO REVERSENAMES

:PLAYGAME
hl2.exe -steam -game portal
GOTO EXIT

:REVERSENAMES
RENAME SteamEmu.ini SteamEmuHL2.ini
RENAME SteamEmuPortal.ini SteamEmu.ini
GOTO PLAYGAME

:EXIT

---

### Post by Whiffle on 2008-01-18
I would rewrite it as a Bash script, and then just use wine in the script.

---

### Post by sauronsmatrix on 2008-01-18
you should just run it from a link that you make:

ex: 

wine "location of game/game.exe" -steam -game portal -dxlevel 81


dxlevel 81 is critical to running portal on ubuntu, because it cannot play dx9 well. in fact, its extremely laggy and freezes your computer.

so make sure to have dxlevel 81

---

### Post by Sugi on 2008-01-19
Woot! It started up, but then my woot became short lived.  I got this wired error.  "No Premissions to run 'Portal'".  What should I do about this?  and My friend said in windows he had to create a shortcut to the .bat file.  Do we have to do that?

Whiffle:  How do I create a Bash script?

---

### Post by sauronsmatrix on 2008-01-19
wow that is strange. maybe try putting sudo before all the commands?

---

### Post by Sugi on 2008-01-19
What the heck does this mean, "wine: /home/LongPenis/.wine is not owned by you"?  I got this same thing I was trying to install Adobe Photoshop CS2.  How can I run Portals?

---

### Post by Sugi on 2008-01-19
The error I get when I try to run portals with wine without super user.

> $ wine hl2.exe -steam -game portal -dxlevel 81
fixme:win:EnumDisplayDevicesW ((null),0,0x34e2d8,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x152220) : stub
fixme:process:IsWow64Process (0xffffffff 0x3489d8) stub!

---

### Post by Sugi on 2008-01-24
Bump

---

### Post by Sammi on 2008-01-24
Don't you already get links under Applications -> Wine -> programs

---

### Post by Sugi on 2008-01-25
the link won't work.  I have to run it under the .bat file.  Is there a way to run the game with the .bat file?  or maybe recreate it within linux?

---

### Post by Sugi on 2008-01-30
Bump

---

### Post by sauronsmatrix on 2008-01-30
dont use the .bat to execute the game. instead use

wine "gamelocation/hl2.exe" -steam -game portal -dxlevel 81

---

### Post by dark_harmonics on 2008-01-30
> **Sugi said:**
> What the heck does this mean, "wine: /home/LongPenis/.wine is not owned by you"?  I got this same thing I was trying to install Adobe Photoshop CS2.  How can I run Portals?

Nice username. I was reading this because i've had some issues starting this app too (although i think its related to my ati and compiz not liking direct rendering).

---

### Post by Sugi on 2008-01-30
hahha, thanks.  Did you ever find anything to fix it?  I am still unsure on how to get the game to work.

**sauronsmatrix**
> dont use the .bat to execute the game. instead use

wine "gamelocation/hl2.exe" -steam -game portal -dxlevel 81

I starts up and displays "Loading" and then a wine window comes up saying "No Premission to run "Portal"" and shuts down.

Terminal
> wine "hl2.exe" -steam -game portal -dxlevel 81fixme:win:EnumDisplayDevicesW ((null),0,0x34e2d8,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x152220) : stub
fixme:process:IsWow64Process (0xffffffff 0x3489d8) stub!

Now what?

---

### Post by Sugi on 2008-02-10
Bump

---

### Post by slavik on 2008-02-10
try
```
chattr -R +S steam/directory
```

fixed it for me (for portal and tf2)

---

