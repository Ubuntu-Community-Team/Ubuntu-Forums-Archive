---
title: "Guild Wars problems"
date: 2007-12-27
forum: Wine
---

### Post by ifflejink on 2007-12-27
So, I'm trying to run Guild Wars in wine 0.9.51, fully patched, but every time I start the launcher, it shows the patch downloading screen, says the program is at %100, then promptly crashes. This is the message I get when I start it in the terminal:
dante@DuMort:~$ wine "C:\Program Files\Guild Wars\Gw.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33f06c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x7c8152d8, 260): stub
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x14bf48) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2b70050) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2e80050) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2860478) : stub
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x14bf48) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2b70050) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2e80050) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2860050) : stub
Mesa 7.0.1 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22
Any ideas?

---

### Post by ifflejink on 2007-12-27
I tried running it through the terminal using: 
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dx8 -noshaders
and the program now runs, but the framerate is slow and, whenever I click on anything, the download window pops up for a split second. Although it doesn't directly affect funcionality, it's incredibly annoying and makes the game very hard to play.

---

