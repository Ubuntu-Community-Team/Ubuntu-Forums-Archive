---
title: "Wine+GalliumNine, err:d3d9nine:d3dadapter9_new Your display driver doesn't support na"
date: 2016-09-29
forum: Wine
---

### Post by buenaventura16 on 2016-09-29
Dear Ubuntu Forums,

I'm running xubuntu 16.04 on an Acer Aspire 15 laptop, and I am trying to play Mirror's Edge with Wine (playonlinux), using gallium9 for better performance. 
 **lspci -vvnn | grep VGA** gives:
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (rev 05) (prog-if 00 [VGA controller])
```
For more info on my video card and driver used, check [this pastebin(output of lshw -c video and modprobe radeon)](http://pastebin.com/vQZLNvJz)

I have done thus:

1. Added and sudo apt-get upgraded to the [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/)
2. Added and sudo apt-get upgraded to the [https://launchpad.net/~commendsarnex/+archive/ubuntu/winedri3](https://launchpad.net/~commendsarnex/+archive/ubuntu/winedri3)
3. Made sure what wine version is the system one (wine --version now gives "wine-1.9.19", before it was 1.6 for some reason))
4. In PoL, in my mirrorsedge-prefix, set wine version to System, used winecfg to enable the gallium nine tick in the Staging tab
5. Added
```
[COLOR=#333333][FONT=monospace]Section "Device"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]   Identifier "radeon"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]   Driver "radeon"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]   Option "DRI" "3"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]EndSection
```
to a new /etc/X11/xorg.conf (I'm not sure whether this was loaded on reboot though - how can I make sure?)
6. When I run mirrorsedge with PoL debug, I get this:
```
[/FONT][/COLOR][09/29/16 10:37:35] - Running wine- MirrorsEdge.exe (Working directory : /home/simon/.PlayOnLinux/wineprefix/mirrorsedge/drive_c/Program Files/Electronic Arts/Mirror's Edge/Binaries)fixme:module:load_dll Loader redirect from L"d3d9.dll" to L"d3d9-nine.dll"
fixme:gameux:GameExplorerImpl_VerifyAccess (0x1674d8, L"C:\\Program Files\\Electronic Arts\\Mirror's Edge\\Binaries\\MirrorsEdge.exe", 0x261f2e8)
err:d3d9nine:present_has_d3dadapter Failed to load /usr/lib/i386-linux-gnu/d3d/d3dadapter9.so.1: /usr/lib/i386-linux-gnu/d3d/d3dadapter9.so.1: cannot open shared object file: No such file or directoryerr:d3d9nine:present_has_d3dadapter [1;31m
Native Direct3D 9 will be unavailable.
For more information visit https://wiki.ixit.cz/d3d9[0m
err:d3d9nine:d3dadapter9_new Your display driver doesn't support native D3D9 adapters.
err:d3d9nine:d3dadapter9_new Your display driver doesn't support native D3D9 adapters.
fixme:dbghelp:validate_addr64 Unsupported address fffffffff7270000
fixme:faultrep:ReportFault 0x261f328 0x0 stub
wine: Unhandled page fault on read access to 0x00000000 at address 0xabc796 (thread 0009), starting debugger...
```

Now, I am stuck! What am I doing wrong? Perhaps my xorg.conf is not loaded, how do I check?

Thanks!

---

### Post by cborga1985 on 2016-10-13
It looks like you have it enabled on your default prefix but not the prefix POL is using. Try running ```
WINEPREFIX="/home/simon/.PlayOnLinux/wineprefix/mirrorsedge" winecfg
``` then select Staging tab and enabled Gallium Nine.

---

### Post by buenaventura16 on 2016-10-14
> **cborga1985 said:**
> It looks like you have it enabled on your default prefix but not the prefix POL is using. Try running ```
WINEPREFIX="/home/simon/.PlayOnLinux/wineprefix/mirrorsedge" winecfg
``` then select Staging tab and enabled Gallium Nine.

Thank you for answering! The winecfg that you command brings up is the same as the one I get when I choose Configure->Wine on my mirrorsedge-prefix in POL, I checked by enabling it using your command, trying (same error), then opening winecfg through POL (where the G9 check was checked), unchecked it, and ran your command again - it was unchecked there as well. So it seems, that it is the same prefix.
 
Any other ideas?

Thanks!

---

