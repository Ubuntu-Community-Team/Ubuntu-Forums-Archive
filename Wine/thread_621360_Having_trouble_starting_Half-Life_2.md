---
title: "Having trouble starting Half-Life 2"
date: 2007-11-23
forum: Wine
---

### Post by RJ Fighter on 2007-11-23
Alright, when I try to start Half-Life 2 under Wine, all it does is appear for a split second then disappears for no reason without any errors whatsoever.  These are my current settings, which I've changed many times already:

```
env WINEPREFIX="/home/rjfighter/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 220 -window -novid -dxlevel 80 -width 1024 -height 768
```

Anyone have any idea as to why it won't even start for me?  :confused:

---

### Post by Gerlads Mod on 2008-05-08
> **RJ Fighter said:**
> Alright, when I try to start Half-Life 2 under Wine, all it does is appear for a split second then disappears for no reason without any errors whatsoever.  These are my current settings, which I've changed many times already:

```
env WINEPREFIX="/home/rjfighter/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 220 -window -novid -dxlevel 80 -width 1024 -height 768
```

Anyone have any idea as to why it won't even start for me?  :confused:

Make sure you have steam up and running.
Open a Teminal and try the following:
```

cd /home/rjfighter/.wine/Program\ Files/Steam/steamapps/STEAMUSERNAME/half-life\ 2
sudo killall pulseadio
pasuspender ./hl2.exe -- -dxlevel 80 -novid -width 1024 -height 768

```

I have gotten it to work like that in Hardy but now it crashes and outputs:
```

Connection failure: Connection refused
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21e154,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f027640) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f027640) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f027640) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f027640) Event query: Unimplemented, but pretending to be supported
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f027640) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x7f027640) Event query: Unimplemented, but pretending to be supported
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x7f088028) : pBox=0x7f21e31c stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x7f027640) : stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!

```

---

### Post by DoktorSeven on 2008-05-08
> **Gerlads Mod said:**
> 
```

Connection failure: Connection refused
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

