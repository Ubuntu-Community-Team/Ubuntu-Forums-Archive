---
title: "Possible wineboot issue?"
date: 2014-06-14
forum: Wine
---

### Post by Oskar_Kolar on 2014-06-14
Hello!
I have a proble with colin mcrae rally 2005. I installed it with wine and it installed ok, but when i try to run it it prompts me to restart the computer. i tried restarting the computer, then i tried wineboot -r, still same problem. I posted on the winehq page but no replies. This may also be an issue beacuse of the starforce drivers.....

---

### Post by alexandari on 2014-06-14
run the executable from the terminal with wine,it will produce an output. Copy that output here

Navigate to the directory where it is installed, ```
 cd ~/.wine 
```  and so on and so on
and run it like that ```
 wine colinmcrae.exe 
```

---

### Post by Oskar_Kolar on 2014-06-14
wine: Unhandled page fault on read access to 0xffffffff at address 0x54bf04 (thread 0026), starting debugger...
wine: Unhandled page fault on read access to 0xffffffff at address 0x559587 (thread 002e), starting debugger...
err:module:import_dll Library SCSIPORT.SYS (which is needed by L"C:\\windows\\System32\\drivers\\prosync1.sys") not found
err:winedevice:ServiceMain driver L"prosync1" failed to load
fixme:ntoskrnl:KeInitializeEvent stub: 0x540748 1 0
fixme:ntoskrnl:PsSetCreateThreadNotifyRoutine stub: 0x5405c0
fixme:dbghelp_dwarf:dwarf2_parse_subprogram Unhandled Tag type 0x26 at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0x4b0430,symt:0x55c708)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:dwarf2_parse_subprogram Unhandled Tag type 0x26 at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0x4b0430,symt:0x55c708)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:compute_location Only supporting one reg (edx/19 -> -2)
fixme:dbghelp_dwarf:dwarf2_parse_subprogram Unhandled Tag type 0x26 at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0xf51144,symt:0x128265c)
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0xf at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0xf511f4,symt:(nil))
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0xf at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0xf511f4,symt:(nil))
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0x26 at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0x14c1a3c,symt:(nil))
fixme:dbghelp_dwarf:dwarf2_parse_subprogram Unhandled Tag type 0x26 at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0xf51144,symt:0x128265c)
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0xf at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0xf511f4,symt:(nil))
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0xf at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0xf511f4,symt:(nil))
fixme:dbghelp_dwarf:dwarf2_parse_subprogram_block Unhandled Tag type 0x26 at ctx(0x33c19c,L"libc.so.6"), for debug_info(abbrev:0x14c1a3c,symt:(nil))
err:module:attach_process_dlls "PROTECT.DLL" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\prgrm\\Codemasters\\rrrraaa\\CMR5.EXE" failed, status c0000142
kolaric@kolaric-G31M-S2L:~$ err:wineboot:ProcessRunKeys Error running cmd L"C:\\Program Files\\NCWest\\NCLauncher\\NCUpdateHelper.exe" (2)


hope this is ok
EDIT: edited the quote after i clicked the yes to restart once it ran.

---

