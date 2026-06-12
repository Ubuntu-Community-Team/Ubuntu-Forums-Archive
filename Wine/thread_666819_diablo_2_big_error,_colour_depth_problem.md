---
title: "diablo 2 big error, colour depth problem?"
date: 2008-01-13
forum: Wine
---

### Post by dooglex on 2008-01-13
Hi, whenever i try and run diablo2 LOD from the gui i get "we got a big error here". When i try and run from the command line i get:

<code>

[email]nath@nath-laptop:~/.wine[/email]/drive_c/Program Files/Diablo II$ wine D2Loader-1.11b.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f0f8,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:heap:HEAP_ValidateInUseArena Heap 0x110000: bad size 002f1658 for in-use arena 0x19c050



err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xffe7afd8

</code>
Any help would be great, thanks!

---

### Post by DarkSim on 2008-01-14
> **dooglex said:**
> Hi, whenever i try and run diablo2 LOD from the gui i get "we got a big error here". When i try and run from the command line i get:

<code>

[email]nath@nath-laptop:~/.wine[/email]/drive_c/Program Files/Diablo II$ wine D2Loader-1.11b.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f0f8,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:heap:HEAP_ValidateInUseArena Heap 0x110000: bad size 002f1658 for in-use arena 0x19c050



err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xffe7afd8

</code>
Any help would be great, thanks!

fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!

I have been getting these two lines when starting up winecfg. While doing some google-fu I stumbled upon this thread. I don't know if it's related to your problem or not but I found this link saying something about those 2 lines are from a bug.

[http://bugs.winehq.org/show_bug.cgi?id=5407](http://bugs.winehq.org/show_bug.cgi?id=5407)

---

### Post by EGJason on 2008-01-14
You get the same error in Windows also when you try to use a loader of some sort.  Most of these loaders have been patched by Blizzard, even if you did successfully get it to work, once you connect to Battle.net it will disable your account for trying to play it like that..  

$5 for D2 LOD at GameStop, just go buy it.

---

