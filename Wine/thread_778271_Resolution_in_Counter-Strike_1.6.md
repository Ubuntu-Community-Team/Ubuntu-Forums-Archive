---
title: "Resolution in Counter-Strike 1.6"
date: 2008-05-01
forum: Wine
---

### Post by Rocket2DMn on 2008-05-01
I installed the 64 bit version of Ubuntu on my desktop, then installed wine.  I had this problem, so I also tried compiling wine myself with the directions here - [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) - but the problem still exists.
I have a dual head nvidia setup using TwinView
I can open steam just fine, but when I open cs, even with the launch options of
```
-width 1024 -height 768 -windowed
```
the game resolution is stuck really low like 640x480 or 800x600 at best (it doesn't say so it's hard to tell).  There are no options to change the resolution from within the game either.
Here is the terminal dump from opening steam, then from opening cs.
```
connor@compy686:~/.wine/drive_c/Program Files/Steam$ wine Steam.exe 
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
CellID: Fetching server list from CSDS. . .
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
CellID: CSDS returned 160 servers.
CellID: Connecting to 69.28.153.107:27031. . .
CellID: Connect to 69.28.153.107:27031 took 107 MS
CellID: Nothing beat our old best time of 19 MS
fixme:mixer:ALSA_MixerInit No master control found on Monitor Integrated Webcam, disabling mixer
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1b7b60)->(1 00000002 0x11942e0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1b7b60)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1b7b60)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1b7b60)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1b81d0)->(1 00000002 0x1194348)
fixme:shdocvw:PersistStreamInit_InitNew (0x1b81d0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1b81d0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1b81d0)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
```

Now opening Counter-Strike 1.6
```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32cae4,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
fixme:shdocvw:ViewObject_SetAdvise (0x1d5f10)->(1 00000002 0x1198a90)
fixme:shdocvw:PersistStreamInit_InitNew (0x1d5f10)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1d5f10)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1d5f10)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x4002e,0x00000000,52,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4002e,0x00000000,52,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4002e,0x00000000,252,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4002e,0x00000000,252,2): stub!
preloader: Warning: failed to reserve range 00000000-00010000
fixme:win:SetLayeredWindowAttributes (0x4002e,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4002e,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1d5f10)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1d5f10)
fixme:shdocvw:OleObject_Close (0x1d5f10)->(1)
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Monitor Integrated Webcam, disabling mixer
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5f4,0x00000000), stub!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:shdocvw:ViewObject_SetAdvise (0x1650d0)->(1 00000002 0x3c602d0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1650d0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1650d0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1650d0)->(ffffffff)
```

Any feedback would be great.  Thanks in advance.

---

### Post by abh83 on 2008-05-02
check my second post on this thread:[http://ubuntuforums.org/showthread.php?p=4861974#post4861974](http://ubuntuforums.org/showthread.php?p=4861974#post4861974)

seems like a bug in wine. something to do with dual monitors and differing resolutions.

---

### Post by Rocket2DMn on 2008-05-02
Thank you for the reply.  My next step is going to be disabling one of the monitors to see what happens.  I know steam/cs and another program I use worked well under wine in Gutsy on my 32bit, single screen laptop.  Having followed the directions for compiling wine myself for 64 bit, the issue persists, so the next step definitely seems to be to try some graphics stuff.
My card is a NVIDIA GeForce 8600 GT with dual head DVI 20" widescreen dells @ 1680x1050 each.  I used EnvyNG to install the restricted drivers version 169.12.
I think the same problem occurred when I tried to run cs inside of a winxp virtual machine using VirtualBox (even not using the seemless integration).

---

### Post by smrdelj on 2008-05-02
Hi

Excuse me Rocket2DMn, but would you mind telling me how did you install CS 1.6 with Steam? Because a I have a problem with that.

I'm running Steam with Wine's latest version installed in Ubuntu 8.04 and, when I click the "Install" button, Steam crashes. So I can't install Cs, because Steam always closes itself.

Did you deal with this problem (or anything similar)?

Would you please help me if you know the solution?

Here is my thread, just in case you wish to say anything: [http://ubuntuforums.org/showthread.php?t=777484](http://ubuntuforums.org/showthread.php?t=777484)

Thanks. Bye

---

### Post by abh83 on 2008-05-02
> **Rocket2DMn said:**
> Thank you for the reply.  My next step is going to be disabling one of the monitors to see what happens.  I know steam/cs and another program I use worked well under wine in Gutsy on my 32bit, single screen laptop.  Having followed the directions for compiling wine myself for 64 bit, the issue persists, so the next step definitely seems to be to try some graphics stuff.
My card is a NVIDIA GeForce 8600 GT with dual head DVI 20" widescreen dells @ 1680x1050 each.  I used EnvyNG to install the restricted drivers version 169.12.
I think the same problem occurred when I tried to run cs inside of a winxp virtual machine using VirtualBox (even not using the seemless integration).

I think thats the easiest solution right now. I used the nvidia-settings manager to disable my laptop display. At least now I can use photoshop under wine.

What a waste though...

---

### Post by Rocket2DMn on 2008-05-11
I'm gonna bump this thread, with some updates.

First, bug report: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/227563](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/227563)

I reinstalled with the 32 bit version of Ubuntu, and the problem still exists, so it would seem the source of the problem is my Nvidia GeForce 8600 GT video card.  Even after the fresh install with no drivers installed, the problem occurred, as well as when only one screen was enabled with the restricted drivers.  In short, nothing has fixed the problem.  If anybody can confirm this, please post here and on the bug report (confirm it there).
Thanks.

---

