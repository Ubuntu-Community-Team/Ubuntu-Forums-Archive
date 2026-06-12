---
title: "Team Fortress 2 on Ubuntu 10.04"
date: 2011-07-24
forum: Wine
---

### Post by cmpgm88 on 2011-07-24
Hello, Ubuntu Forum Members!

I installed WINE 1.2.2 and I downloaded the installation package for Steam on Windows.  Steam installed correctly, at least, I think it did; it's letting be browse all the appropriate pages and such.  I then installed Team Fortress 2 through Steam, but when I click 'Play', it will not launch.

What should I do?

---

### Post by cmpgm88 on 2011-07-24
I tried running the game directly through the Terminal using the command:

~env WINEPREFIX="/home/chris/.wine" wine C:\\Program Files\\Steam\\steamapps\\cmpgm88\\team fortress 2\\hl2.exe -game tf

and it yielded this:

```
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32dfec,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x14a840,0x14a788): stub
Using breakpad crash handler
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x1519a0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x32e114)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported

```

---

### Post by cmpgm88 on 2011-07-24
And then I used PlayOnLinux.  Mann, that worked great!

---

### Post by 8_Bit on 2011-07-25
You got TF2 running with POL? That's great! What's the performance like?

---

### Post by cmpgm88 on 2011-08-01
Err... I'm having texture problems..  I've posted another thread about it (that no one has answered yet..) [here]("http://ubuntuforums.org/showthread.php?t=1814312").  Other than that, everything else seems to work fine! :)

---

