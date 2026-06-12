---
title: "autorun errors"
date: 2008-05-19
forum: Wine
---

### Post by byzantines2000 on 2008-05-19
I am trying to install Battle for Middle Earth. I pop in the cd, click autorun.exe, and I get an error 

Unable to locate required file or required file is corrupted.

Z:\home\mike\AutorunGUI.DLL

I downloaded the file autorungui.dll and i still have this problem.
I even tried starting it from the terminal.

Can anyone point me in a direction that leads to this problem being solved? :)


UPDATE: I tried moving the file to the location it wanted me to... but now I get a message saying that the file was found, but the message box is missing...
Is there a way to not need the GUI? Can I install it strictly via terminal?

---

### Post by CC_machine on 2008-05-20
you should try running the setup installer directly.. autorun exe's tend to have issues with wine. hunt around the install CD for a setup.exe, install.exe, battleforearthinstall.exe, or anything that looks like an installer. :P

---

### Post by chocomallow89 on 2010-12-17
I have the same problem and I've tried opening either install or setup and neither works it just says "The file '/media/LOTRBFME/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.." A friend suggested to right click, open with other application and then in other just write wine and try again but that comes up with error "unable to locate required file or required file is corrupted" 

Any other ideas?????

---

### Post by chocomallow89 on 2010-12-17
> **chocomallow89 said:**
> I have the same problem and I've tried opening either install or setup and neither works it just says "The file '/media/LOTRBFME/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.." A friend suggested to right click, open with other application and then in other just write wine and try again but that comes up with error "unable to locate required file or required file is corrupted" 

Any other ideas?????


i have now tried right clicking the disc and selecting open with auto run prompt but i just get "Error autorunning software Cannot find the autorun program" is LOTRBFME just not compatible or should i use something other than wine to use it?

---

### Post by cogadh on 2010-12-17
Run it from the terminal. Open a terminal, change directories to the install disk, then "Wine" the setup executable:
```
cd /media/LOTRBFME
wine setup.exe
```

---

### Post by chocomallow89 on 2010-12-18
> **cogadh said:**
> Run it from the terminal. Open a terminal, change directories to the install disk, then "Wine" the setup executable:
```
cd /media/LOTRBFME
wine setup.exe
```

WORKED! It installed and I had to download some patches cause there were some other problems but now I can open it but when the splash screen pops up it then goes grey and freezes everything. It changes the screen res just before it freezes but that's about as far into the game I can get, Any ideas for that one?

---

### Post by cogadh on 2010-12-18
What game is this? The "LOTR" obviously indicates "Lord of the Rings", but which game is it?

EDIT - Ack, just realized "Battle for Middle Earth". See here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2713](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2713)

---

### Post by chocomallow89 on 2010-12-18
> **cogadh said:**
> What game is this? The "LOTR" obviously indicates "Lord of the Rings", but which game is it?

EDIT - Ack, just realized "Battle for Middle Earth". See here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2713](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2713)


Yes it is Battle for Middle Earth and after putting that code in it said:

phoebe@phoebe-Inspiron-1525:~$ cd /media/LOTRBFME
bash: cd: /media/LOTRBFME: No such file or directory
phoebe@phoebe-Inspiron-1525:~$ wine setup.exe

Me and my bf have tried lots of stuff and from what we can tell, there seems to be a problem with two bits that show up in the terminal readout:
wine: cannot find L"C:\\windows\\system32\\TextureAssetBuilder.ex  e"
wine: cannot find L"C:\\windows\\system32\\assetCacheBuilder.exe"
That help??

---

### Post by cogadh on 2010-12-18
You only need to run that code to install the game. Once installed, you need to run the game from its installation directory (C:\Program Files\<whatever>). You can do that by once again changing directories to the install directory and "Wineing" the game executable:
```
cd ~/.wine/drive_c/Program\ Files/path/to/game
wine game.exe
```
Obviously change that "path/to/game" and "game.exe" to the correct path and executable name, I don't know what they are.

---

### Post by chocomallow89 on 2010-12-18
> **cogadh said:**
> You only need to run that code to install the game. Once installed, you need to run the game from its installation directory (C:\Program Files\<whatever>). You can do that by once again changing directories to the install directory and "Wineing" the game executable:
```
cd ~/.wine/drive_c/Program\ Files/path/to/game
wine game.exe
```Obviously change that "path/to/game" and "game.exe" to the correct path and executable name, I don't know what they are.

Nope, same problem... Here's what was in the terminal window:
[email]phoebe@phoebe-Inspiron-1525:~/.wine[/email]/dosdevices/c:/Program Files/EA GAMES/The Battle for Middle-earth (tm)$ wine lotrbfme.exe
fixme:heap:HeapSetInformation 0x1e80000 0 0x33fde4 4
fixme:imm:ImmDisableTextFrameService Stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 30
fixme:font:WineEngAddFontResourceEx Ignoring flags 30
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x181db0,0x181d38): stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
(lots of that)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33d8c8,0x00000000), stub!
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x38d26a0) : stub
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x1
(lots of that)
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x60
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x61
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x62
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x63
fixme:d3d:debug_d3dformat Unrecognized 827611205 (as fourcc: EXT1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(827611205) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 827611206 (as fourcc: FXT1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(827611206) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 827611207 (as fourcc: GXT1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(827611207) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 827611208 (as fourcc: HXT1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(827611208) in the format lookup table
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x1
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x2
(lots of that)
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x5f
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x60
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x61
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x62
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x63
wine: cannot find L"C:\\windows\\system32\\TextureAssetBuilder.exe"
wine: cannot find L"C:\\windows\\system32\\assetCacheBuilder.exe"
[email]phoebe@phoebe-Inspiron-1525:~/.wine[/email]/dosdevices/c:/Program Files/EA GAMES/The Battle for Middle-earth (tm)$

---

### Post by cogadh on 2010-12-18
Odd. It shouldn't even be looking in system32 for those executables, they should be in the game install directory somewhere. Usually when Wine does that (looks in system32 when it shouldn't), it just means that the application path is not set correctly, which is always resolved by changing directories. I'm afraid I'm stumped on this one.

---

### Post by DevilFish101 on 2010-12-19
It's a bit quick-and-dirty, but could you just copy those .exe files into system32?

---

### Post by DevilFish101 on 2010-12-21
There's some mention of this problem at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6613](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6613) , but I can't really decipher the conversation...
Any help?

---

