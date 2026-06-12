---
title: "[SOLVED] Tomb Raider Annivesary - fixed preloaderpagezero but errors in terminal stil"
date: 2008-05-17
forum: Wine
---

### Post by philinux on 2008-05-17
Do I have to install my graphics drivers using wine? Bit of a noob with wine/games.

```
env WINEPREFIX="/home/philcb/.wine" wine "C:\Program Files\Tomb Raider - Anniversary\TRA.exe" 
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8da, disabling mixer
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x175a51c,0x00000004,0x175a518) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1759408): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x175926c,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0xe3f710, 0x1739d18) stub
fixme:psapi:EnumPageFilesA (0xe3f710, 0x1704634) stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d014
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x1732380,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x112e,00007f00),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f03),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f01),stub!
fixme:cursor:SetSystemCursor (0x1156,00007f88),stub!
fixme:cursor:SetSystemCursor (0x1166,00007f86),stub!
fixme:cursor:SetSystemCursor (0x1176,00007f83),stub!
fixme:cursor:SetSystemCursor (0x1186,00007f85),stub!
fixme:cursor:SetSystemCursor (0x1196,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11a6,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11b6,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11c6,00007f02),stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x176f93c): Stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:create_server class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x17
philcb@philcb-desktop:~$
```

---

### Post by happyhamster on 2008-05-17
- Which wine version are you using?
- Do you get the same result when running:

wine TRA.exe

- from within the Tomb Raider - Anniversary folder?

---

### Post by philinux on 2008-05-17
Version 0.9.59
I forgot to include this is the final out of table errror
Failed to open BIGFILE.000

Will try to run as suggested
result extra error
wine: Unhandled page fault on execute access to 0x01cb0075 at address 0x1cb0075 (thread 0009), starting debugger... Then it drops out back to cli.

---

### Post by happyhamster on 2008-05-17
Hmm, I can't reproduce that I'm afraid. It runs fine for me on hardy (wine version 1.0rc or 0.9.59, compiz or no compiz) and it runs fine on gutsy too (1.0rc). I'm using the proprietary Nvidia driver.

Note that I have Anniversary running on hardy despite the preloader warning (I haven't applied the fix). Things you could try:

- Play with the sound settings a bit, perhaps it's pulse-audio related (System-->Preferences-->Sound and choose ALSA for everything for example.)

- Get rid of previous wine:

sudo apt-get remove --purge wine

- Get rid of the hidden .wine folder in your home dir (this will mean you'll have to re-install all programs you had running under wine). You might also want to move or delete the "Eidos" folder in your home dir which Anniversary uses to store its settings and savegames.

- Install the current version of wine. Follow the instructions here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Note that the wine servers tend to be flaky, so you might have to try a few times to get things to download.

- After installing wine, run winecfg to configure it. See this excellent thread for more info:
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

Good luck, and keep us informed.

---

### Post by philinux on 2008-05-17
Tested sound using alsa and thats ok.

I have the dvd as it was free with my graphics card. Legal you know.

Is it cos I'm running hardy 64 bit?

---

### Post by happyhamster on 2008-05-17
> **philinux said:**
> Is it cos I'm running hardy 64 bit?
Ah, that could be it. I'm on i386 myself, but I should have a 64 bit test-partition somewhere. I'll see if I get the same result.

---

### Post by happyhamster on 2008-05-17
Ok, confirmed. I get a page fault as well :(

---

### Post by philinux on 2008-05-17
I've got two Hd's so I could install 32 bit in the spare unused one. Seems a bit overkill though. I've tried other distro's and non recognise my on board lan card. Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

Thanks for confirm!

Do you get exactly same errors?

---

### Post by happyhamster on 2008-05-17
Ok, I think I found the problem: apparently the copy-protection is broken on 64 bit. Applying a nocd-crack* fixes things. This isn't needed on i386 though; there it all works out of the box. I'm not sure if that's a regression, because I have no experience with 64 bit, but I assume this will affect more applications than just Tomb Raider Anniversary.

* please don't ask for links.

---

### Post by philinux on 2008-05-17
Could you tell me what a nocd crack is. Never heard of this.

---

### Post by Half-Left on 2008-05-17
> **philinux said:**
> Could you tell me what a nocd crack is. Never heard of this.

It lets you play the game without needing the CD/DVD. I've got TRA myself, I'll have to test it in Hardly 64(always worked fine last time I tried it).

---

### Post by philinux on 2008-05-17
Ok got a replacement tra.exe file from a site and it now works. It said on their website only for use if you own the game which I do.

The mouse is a bit laggy on the intro and set up page

---

### Post by happyhamster on 2008-05-17
Ironically, this problem will only affect people who have a legal copy of the game. It's annoying, and rather common unfortunately (regardless of the platform you're using).

But I'd better suppress the urge to rant about copy-protection and drm.... :)

---

### Post by philinux on 2008-05-17
Thanks all for help. The game play's fine with my thrustmaster joystick with full effects. The only weird part is the intro which has a few odd rendering effects, but one in the game it's fine.

Very annoying this is affecting me with a legal copy though. Better be of to launchpad as it looks like is defo a  64 bit issue.

---

### Post by happyhamster on 2008-05-17
> **philinux said:**
> The mouse is a bit laggy on the intro and set up page
Yes, but it's better when playing correct?

To optimize things a bit, you can set a few registry settings. Make a text file containing the lines:

```

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"VideoMemorySize"="256"
"UseGLSL"="enabled"
"OffscreenRenderingMode"="pbuffer"
"RenderTargetLockMode"="auto"

```

- Use the correct amount of video memory for your video card instead. Then save it as "anniversary.reg"

- Next, import it into the registry. Run this command from within the folder where you saved the file:

regedit anniversary.reg


- Oh and BTW, I'm not really sure how strict forum policy is on this matter, but I think it's safest if you'd edit your post and delete the name of the site.

---

### Post by philinux on 2008-05-17
I'm not sure yet if I want to play with registry. I'll see how it goes.

Once in the actual game everything is fine very smooth graphics. Mouse and joystick work fine.

---

