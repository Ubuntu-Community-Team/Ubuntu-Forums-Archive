---
title: "WoW - Intel GM965/GL960"
date: 2008-11-28
forum: Wine
---

### Post by Cryp71c on 2008-11-28
Wine version - 1.1.9
Ubuntu version - 8.1 (Intrepid)
Wow version - WOTLK 3.0.3

I 'installed' wow by copying the entire world of warcraft directory from my NTFS partition into the .../c:/Program Files/ folder under wine.

When I run wow I get a lot of !stub messages and usually 2/3 I can see 'World of Warcraft' window open up in the window bar at the bottom as if its already running by my system freezes and won't respond to anything. When Wow does load its very choppy, ~ 15fps lower than with windows running it :(

Any ideas on how to fix these problems or a way to get those specific !stub messages without my system crashing?

Edit:: here's the terminal messages, I got it to launch without freezing the system
> orld of Warcraft$ wine launcher.exe
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
[email]culture@culture-laptop:~/.wine[/email]/drive_c/Program Files/World of Warcraft$ fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x3aedbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af520,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374025c4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x30028, (nil), 16): stub


---

### Post by hikaricore on 2008-11-28
I'd be willing to bet the issue is with your video card and or drivers.

Check the terminal output of:
> glxinfo | grep rendering
To verify that you have direct rendering functioning properly.

After that I suggest you run the game in OpenGL mode to see if the framerate is any better.
Intel "video" chipsets are known for their lackluster performance and shotty vendor released video drivers.

---

### Post by Cryp71c on 2008-11-28
I had already done the glxinfo | grep rendering before I even copied WoW over to make sure it wasn't a waste of time (I had read that already in other wow threads) and although I can't remember the exact output I remember that it coincided with what the thread had said was 'good' (or correct or whatever).

And actually I am running the game in OpenGL. If I don't use OpenGL and allow the game to think its running under DirectX, there are tons more console error messages that look much worse and then the game crashes with a little WoW-error window.

Is there anywhere to obtain drivers? I didn't install any, I'm simply using the ones ubuntu picked for me.

---

### Post by OrbJinzo on 2008-11-28
I hate to to break this to you. Youll not be able to run WoW on that video card in Linux. Windows is a different story

---

### Post by Cryp71c on 2008-11-29
Why? Lack of driver support?

I would imagine that Linux (in general) actually runs better than windows on most (if not all) systems...And the newest version of wine runs wow 'almost' as perfectly as windows would run it (I had heard).

---

### Post by OrbJinzo on 2008-11-29
Intel in general has shoddy opengl support with its video cards.

---

### Post by Cryp71c on 2008-11-29
I see, no one has written any drivers which circumvent that issue, or is it primarily hardware based?

---

### Post by OrbJinzo on 2008-11-30
I think in my opinion its lack of good drivers.

---

