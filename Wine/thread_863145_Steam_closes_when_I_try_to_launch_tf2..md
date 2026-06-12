---
title: "Steam closes when I try to launch tf2."
date: 2008-07-18
forum: Wine
---

### Post by King-Bob on 2008-07-18
Okay so I'm fairly new to Ubuntu but I have managed to get most of the things setup by following threads in this forum.  I've managed to fix what I could using those suggestions but I have hit a dead wall.

So everything I try to launch a game from steam it just closes

So here is what I can provide

I have tried various version of wine and drivers

```

lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

```

```

wine --version

wine-1.0

```

```

lspci|grep VGA

03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

```

```

nvidia-installer -v

nvidia-installer:  version 1.0.7  (buildmeister@builder58)  Thu Jun  5 00:08:33
PDT 2008
  The NVIDIA Software Installer for Unix/Linux.

  This program is used to install and upgrade The NVIDIA Accelerated Graphics
  Driver Set for Linux-x86_64.

  Copyright (C) 2003 NVIDIA Corporation.

```

NVIDIA Driver Version: 173.14.09

I think my xconf file might not be setup correct for my video cards here is the insert on the devices

```


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "SLI" "on"
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1200_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection


```

I have install the Tahoma and gecko 

When I launch steam I get the following error

```

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Microsoft LifeChat LX-3000 , disabling mixer

```

Any assistance would be greatly appreciated.

---

### Post by damis648 on 2008-07-18
Okay, how did you install wine? From the default repos? If so, try these repos:
```
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main
```
and install wine from those (or just update if it asks you). And try again. Also, do you have sound in wine? If you run winecfg in terminal and try to set up an audio driver, do any of them work? If not, run winecfg like so:
```
padsp winecfg
```
and try again. That would fix sound if you do not have it.

EDIT: Also, if it still doesn't work, what is the terminal output of
```
wine /home/[your username]/.wine/drive_c/{path to game}.exe
```

---

### Post by King-Bob on 2008-07-18
Hi thanks for the help =)

Okay I installed those repositories

and now have

Wine 1.1.1

Even though I get the ALSA error sound works perfectly

When i run wine steam.exe

```

ellID: Fetching server list from CSDS. . .
CellID: CSDS returned 171 servers.
CellID: Connecting to 195.13.60.3:27031. . .
CellID: Connect to 195.13.60.3:27031 took 140 MS
CellID: Nothing beat our old best time of 9 MS
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Microsoft LifeChat LX-3000 , disabling mixer
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x190330)->(1 00000002 0x11b4838)
fixme:shdocvw:PersistStreamInit_InitNew (0x190330)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x190330)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x190330)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x18c7f0)->(1 00000002 0x11b48a0)
fixme:shdocvw:PersistStreamInit_InitNew (0x18c7f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x18c7f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x18c7f0)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x1008a, filter=0x32dbb8,flags=0x00000004),
	returns a fake device notification handle!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7befea08, overlapped 0x7befe9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x110eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1903cc)->((null) 1 0x32a874 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->((null) 25 2 0x32a888 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->((null) 26 2 0x32a888 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x1903cc)->(0x32a8c4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32a988 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x18ef70)->(L"" L"" 0 0x32a9c0)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->((null) 29 2 0x32d558 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1903cc)
fixme:shdocvw:ClientSite_GetContainer (0x1903cc)->(0x32d508)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1903cc)->(0xf7e23755)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->((null) 25 2 0x32d43c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->((null) 26 2 0x32d43c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x1865a8)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x1ab468)
fixme:mshtml:HTMLBodyElement_put_scroll (0x1865a8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x1865a8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x1865a8)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1903cc)->((null) 28 2 0x32d420 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented

```

Unfortunately I do not have the standalone version to give you an output

---

### Post by King-Bob on 2008-07-18
thanks for the help i think 1.1.1 did it it seems to be working fine getting 100 FPS looks great.

---

### Post by damis648 on 2008-07-18
> **King-Bob said:**
> thanks for the help i think 1.1.1 did it it seems to be working fine getting 100 FPS looks great.

Great! :popcorn:

---

