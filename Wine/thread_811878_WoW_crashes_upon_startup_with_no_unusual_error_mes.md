---
title: "WoW crashes upon startup with no unusual error message"
date: 2008-05-29
forum: Wine
---

### Post by Amurko on 2008-05-29
Update: What I'm currently trying - I'll use apt-build to manually compile my video drivers and wine and see if that makes a difference.

I've got 2 PCs and I've gotten WoW to work flawlessly in Ubuntu on the newer one with no sophisticated hacks apart from "sudo apt-get install wine" and "wine WoW.exe -opengl".  I also got an older system that ran WoW back when I was using Dapper but I uninstalled it from that comp.  

When I tried installing WoW on this older system in 8.04 with Wine set up, the installation completed normally.  When I launch WoW, the opening movies appear; I hit spacebar to bypass them and WoW just exits and dumps me to the desktop without the login screen appearing.  I'm using Wine 0.9.59.  Here's my Terminal output (I don't see any peculiar error messages in it):

```

me@me:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21eee0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21edf4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f688,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f674,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21ee5c,0x00000000), stub!
me@me:~/.wine/drive_c/Program Files/World of Warcraft$
```

I don't expect a quick and painless fix to this but I'd like to know if there's any way to get the system to output more detailed errors?  I've also checked the WoW log files and they are empty.

I've also tried changing the OS specification in winecfg to no avail.

Tried running WoW with the -nosound and -windowed parameters - still doesn't work.

Hardware Specs:

Toshiba A60 Notebook
2.8 Ghz Celeron
1.2GB RAM
AC97 Sound
ATI Mobility Radeon 7000 IGP Video Card w/ 64 MB RAM *(using the DRI driver.  It doesn't work with the fglrx driver but glxgears works fine and "glxinfo | grep rendering" says that Direct Rendering is supported.  Note that WoW worked in Dapper despite all this!)*

Is there any way I can roll back to the open-source ATI Display drivers included with Dapper?

---

