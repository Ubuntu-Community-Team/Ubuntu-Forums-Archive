---
title: "OriginPro 2015 loading errors after wine install"
date: 2014-11-03
forum: Wine
---

### Post by kaspar4 on 2014-11-03
Hi Im trying to install a program called origin pro which is a graphing tool.
I have sucessfully been ablle to install it and find all the dll files. Though I am having a persistent crash error when starting up, which I cannot find a solution too.
The bug report is as follows:

fixme:thread:GetThreadUILanguage : stub, returning default language.
fixme:thread:GetThreadPreferredUILanguages 56, 0x33f8a0, 0x33f8b0 0x33f8a4
fixme:thread:GetThreadPreferredUILanguages 56, 0x33f8e0, 0x33f8f0 0x33f8e4
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:thread:GetThreadPreferredUILanguages 56, 0x33f880, 0x33f890 0x33f884
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:thread:GetThreadPreferredUILanguages 56, 0x33f8e0, 0x33f8f0 0x33f8e4
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:thread:GetThreadPreferredUILanguages 56, 0x33f970, 0x33f980 0x33f974
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:thread:GetThreadPreferredUILanguages 56, 0x33f880, 0x33f890 0x33f884
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:msvcrt:MSVCRT__set_abort_behavior _WRITE_CALL_REPORTFAULT unhandled
fixme:thread:GetThreadPreferredUILanguages 56, 0x33f7d0, 0x33f7e0 0x33f7d4
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:msg:ChangeWindowMessageFilter 323 00000001
fixme:msg:ChangeWindowMessageFilter 326 00000001
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:msg:ChangeWindowMessageFilter 233 00000001
fixme:msg:ChangeWindowMessageFilter 4a 00000001
fixme:msg:ChangeWindowMessageFilter 49 00000001
fixme:win:LockWindowUpdate (0x20086), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x20080), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x2007a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x303d2), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x4023c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x702d2), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:ieframe:PersistStreamInit_InitNew (0x79c3130)
fixme:seh:__CxxFrameHandler 0x33acf0 33b120 0x339cd0 0x339ba0: not implemented
fixme:seh:__CxxFrameHandler 0x33acf0 33b3a0 0x339cd0 0x339ba0: not implemented
fixme:seh:__CxxFrameHandler 0x33acf0 33c1d0 0x339cd0 0x339ba0: not implemented
fixme:seh:__CxxFrameHandler 0x33acf0 33d270 0x339cd0 0x339ba0: not implemented
fixme:seh:__CxxFrameHandler 0x33acf0 33edb0 0x339cd0 0x339ba0: not implemented
fixme:resource:GetGuiResources (0xac,0): stub
fixme:ntdll:NtFlushInstructionCache 0xffffffffffffffff 0x510fe0 22
fixme:ntdll:NtFlushInstructionCache 0xffffffffffffffff 0x510fe0 22
fixme:ntdll:NtFlushInstructionCache 0xffffffffffffffff 0x510fc0 22
fixme:ntdll:NtFlushInstructionCache 0xffffffffffffffff 0x510fa0 22
fixme:ntdll:NtFlushInstructionCache 0xffffffffffffffff 0x510f80 22
fixme:ntdll:NtFlushInstructionCache 0xffffffffffffffff 0x510f60 22
fixme:ntdll:NtFlushInstructionCache 0xffffffffffffffff 0x510f60 22
fixme:dbghelp:elf_search_auxv can't find symbol in module

Normally I can fix most problems but I dont understand this error, I thought it might have been my wine version was outdated but I have 1.7.28. I have not had problems when installing earlier versions.
Any help would be apprecitaed

---

