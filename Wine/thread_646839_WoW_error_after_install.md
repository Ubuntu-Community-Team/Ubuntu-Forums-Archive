---
title: "WoW error after install"
date: 2007-12-21
forum: Wine
---

### Post by tysonh on 2007-12-21
I just followed the WoW howto and installed it without a problem.  Once the game finishes installing I log into my account to start the patching.  The patch file starts to download and then a window pops up and says there is a handling error.  Here is the output from terminal at the time of the error:

war@war-desktop:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33f254,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eee0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee14,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f688,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f674,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee5c,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub

Here is the Critical Error box that pops up when I'm downloading:

This application has encountered a critical error

ERROR #125 (OX8510007d)
Program: C:\Program Files\World of Warcraft\Wow.exe
Object: HANDLER (.?AUHANDLER@@)

SMem3:  Not initialilzed.  Verify linker entry point is set to 'StormStaticEntryPoint' (defined in StormStartup.h)
Press ok to terminate the application

Although this error box pops up the download still continues in the background.

The how to mentions a Gecko rendering engine that is supposed to install.  I didn't see anything about Gecko during the install could that be the cause of the handling error?

---

### Post by Faud on 2007-12-22
Gecko is a WINE thing, but it should have been part of your normal WINE install as far as I know. WINE use's it to open internet pages ( in my unexperienced opion ) You should be able to install it from the winehq page or you can just save your wow folder and uninstall wine and reinstall it from the repo. Ive read some of your other posts and to be honest I think that you messed up your WINE install. Your .wine folder is in your home folder but its a hidden file and can be seen by opening your home folder and then going to view and clicking on show hidden files.
Hope you get it all working.
Good luck

---

